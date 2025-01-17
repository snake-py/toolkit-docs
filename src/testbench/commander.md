# CLI Commander

Testbench provides support for command line tool equivalent to `artisan` command where you can interact directly with the stub Laravel application. 

For example instead of refreshing the database on every tests you may now seed the database before running `phpunit`, using:

```
php vendor/bin/testbench migrate
```

or, you can setup the application such as installing Passport:

```
php vendor/bin/testbench passport:install
```

Both commands allows you to setup the testing environment where before you only able to setup manually on every `TestCase::setUp()`.

In order for the `testbench` command to understand any required service providers or environment variables to be used when executing the "artisan" command you need to add the following `testbench.yaml` file on the project root directory.

```yaml
env:
  - DB_CONNECTION="mysql"
  - DB_USERNAME="homestead"
  - DB_PASSWORD="secret"

providers:
  - Laravel\Passport\PassportServiceProvider
```

:::tip Notes and Considerations

* The command is currently designed to help testing, however you might be able to run other feature to help package development such as running `ide-helper:models` etc.
* The command wouldn't work for file stubbing as the generated file will be based on the booted Laravel application and not your package directories.
:::

