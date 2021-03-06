# Debugging

When a value generated by `any` causes a test to fail inconsistently, it can
be incredibly difficult to track down the failing conditions. In order to
reliably reproduce the problem, you need to be able to get `any` to repeatedly
produce the same value.

## Determine the seed

The [debug](https://www.npmjs.com/package/debug) library is in place to enable
revealing the `seed` that was used for the randomness of generated values. This
means that the `seed` is not displayed by default, but can be revealed by
instructing `debug` to output logs for `any`:

```sh
$ DEBUG=any mocha --recursive test/unit/

Thu, 29 Jun 2017 02:13:29 GMT any randomness seed: 0.4070123094134033
```

## Set the seed

Once a problematic `seed` is determined, it can be provided back to any so that
the generation becomes repeatable.

```sh
$ ANY_SEED=0.4070123094134033 mocha --recursive test/unit/
```
