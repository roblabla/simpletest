# Simple Test for Xargo and no PIE

Getting stuff to compile without PIE for Android.

How to use : 

1. Set `RUSTSRC` to a clone of the rust source
2. Set `ANDROID_TOOLCHAIN` to a standalone NDK toolchain :

```
$NDK_HOME/build/tools/make-standalone-toolchain.sh \
    --platform=android-21 --arch=arm --install-dir=$ANDROID_TOOLCHAIN \
    --toolchain=arm-linux-androideabi-4.9
```

3. Make sure you have xargo installed with `cargo install xargo`
4. Run `XARGO_RUST_SRC=$RUSTSRC PATH=$ANDROID_TOOLCHAIN/bin:$PATH xargo build --target=arm-linux-androideabi`
5. Check if the file is PIE by running `file target/arm-linux-androideabi/debug/fantafs` and making sure it's an Executable (and not a Shared Object)
