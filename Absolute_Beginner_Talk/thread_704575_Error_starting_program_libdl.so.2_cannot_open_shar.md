---
title: "Error starting program: libdl.so.2: cannot open shared object file"
date: 2008-02-22
forum: Absolute Beginner Talk
---

### Post by espenbe on 2008-02-22
I have a binary program called xlpipe which will not start in Gutsy.  In Dapper it starts.

If I try to start it as
```
espenbe@ministerial:~$ xlpipe
```
I get
```
xlpipe: relocation error: xlpipe: symbol errno, version GLIBC_2.0 not defined in file libc.so.6 with link time reference
```

To avoid this, I try the following:
```
espenbe@ministerial:~$ LD_ASSUME_KERNEL=2.4.1 xlpipe
```
...but the result is
```
xlpipe: error while loading shared libraries: libdl.so.2: cannot open shared object file: No such file or directory
```

This program depends on the following libraries:
```
espenbe@ministerial:~$ ldd /home/espenbe/bin/xlpipe 
        linux-gate.so.1 =>  (0xffffe000)
        libXrender.so.1 => /usr/lib/libXrender.so.1 (0xb7f2b000)
        libSM.so.6 => /usr/lib/libSM.so.6 (0xb7f23000)
        libICE.so.6 => /usr/lib/libICE.so.6 (0xb7f0a000)
        libdl.so.2 => /lib/tls/i686/cmov/libdl.so.2 (0xb7f06000)
        libGLU.so.1 => /usr/lib/libGLU.so.1 (0xb7e83000)
        libGL.so.1 => /usr/lib/libGL.so.1 (0xb7ded000)
        libXext.so.6 => /usr/lib/libXext.so.6 (0xb7ddf000)
        libX11.so.6 => /usr/lib/libX11.so.6 (0xb7cee000)
        libm.so.6 => /lib/tls/i686/cmov/libm.so.6 (0xb7cc8000)
        libXft.so.1 => /usr/lib/libXft.so.1 (0xb7cb6000)
        libfreetype.so.6 => /usr/lib/libfreetype.so.6 (0xb7c46000)
        libXmu.so.6 => /usr/lib/libXmu.so.6 (0xb7c30000)
        libpthread.so.0 => /lib/tls/i686/cmov/libpthread.so.0 (0xb7c18000)
        libc.so.6 => /lib/tls/i686/cmov/libc.so.6 (0xb7ace000)
        /lib/ld-linux.so.2 (0xb7f48000)
        libstdc++.so.6 => /usr/lib/libstdc++.so.6 (0xb79da000)
        libgcc_s.so.1 => /lib/libgcc_s.so.1 (0xb79cf000)
        libGLcore.so.1 => /usr/lib/libGLcore.so.1 (0xb7037000)
        libnvidia-tls.so.1 => /usr/lib/tls/libnvidia-tls.so.1 (0xb7035000)
        libXau.so.6 => /usr/lib/libXau.so.6 (0xb7032000)
        libXdmcp.so.6 => /usr/lib/libXdmcp.so.6 (0xb702c000)
        libfontconfig.so.1 => /usr/lib/libfontconfig.so.1 (0xb7001000)
        libz.so.1 => /usr/lib/libz.so.1 (0xb6fec000)
        libXt.so.6 => /usr/lib/libXt.so.6 (0xb6f9b000)
        libexpat.so.1 => /usr/lib/libexpat.so.1 (0xb6f7b000)
```

Since it seems like it fails on libdl.so.2, I checked where that one is located:
```
espenbe@ministerial:~$ locate libdl.so.2
/lib/tls/i686/cmov/libdl.so.2
/lib/libdl.so.2
```

So then - why doesn't xlpipe find libdl.so.2 ?  It is there...
Anyone out there been experiencing this problem and got a solution?

---

### Post by espenbe on 2008-05-09
Still nobody got an idea on how to solve this problem?

---

