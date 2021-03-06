`ahc` seems to behave differently than `ghc` when the `-odir` option is used in conjunction with the `-c` option.


In this directory when running:

```
ghc subdir/lib.hs -odir odir -c
```

The output `.o` file is : `./odir/Lib.o`.

However with `ahc`:

```
sudo docker run --rm -v $(pwd):/workspace -w /workspace terrorjack/asterius ahc subdir/lib.hs -odir odir -c
```

The output `.o` file is : `./odir/subdir/lib.o`.

(If we remove the `-c` option, then the output is located in `./odir/Lib.o` in both cases.)

## versions

The ahc version from the docker image is `8.8.4`.

Regarding ghc, I tried version `8.8.4` as well as `8.10.7` and the behavior is the same.
