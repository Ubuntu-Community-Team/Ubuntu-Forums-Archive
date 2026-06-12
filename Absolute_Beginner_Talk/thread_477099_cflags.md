---
title: "cflags"
date: 2007-06-18
forum: Absolute Beginner Talk
---

### Post by antonym on 2007-06-18
I haven't been using ubuntu for all that long, and I've run into plenty of snags, but up til now I've been able to scrounge up solutions from the forums or google. it might that it's late and I'm tired, but I'm figuring it's easier to just ask.

I'm trying to compile tls 1.5... sudo ./configure goes smoothly, but when I enter sudo make, it quickly gives me an error and tells me to recompile with -fPIC. now, I've managed to figure out what that means, but I'm afraid I haven't been able to find a way to do it in ubuntu. I'm guessing it's something pretty basic, or that I might need to modify an environment variable, but I'm not sure how to do the latter and I'd rather not break anything.
so how would I go about setting that flag?

Thanks a bunch in advance!


here is the full output of the make command, by the way. 
```
radu@radu-ub:~/Desktop/tls1.5$ sudo make
rm -f libtls1.50.so
cc -shared -O2  -fPIC  -o libtls1.50.so tls.o tlsIO.o tlsBIO.o tlsX509.o fixstrtod.o  -L/usr/local/tcltk/lib -ltclstub8.5 -L/usr/local/ssl/lib -lssl -L/usr/local/ssl/lib -lcrypto  
/usr/bin/ld: /usr/local/ssl/lib/libssl.a(s2_meth.o): relocation R_X86_64_32 against `a local symbol' can not be used when making a shared object; recompile with -fPIC
/usr/local/ssl/lib/libssl.a: could not read symbols: Bad value
collect2: ld returned 1 exit status
make: *** [libtls1.50.so] Error 1

```

---

### Post by antonym on 2007-06-19
okay, I managed to get it compile with -fPIC... but it's still giving me the same error. I'm thinking this is an error somewhere else then.
anyone have any ideas?

---

