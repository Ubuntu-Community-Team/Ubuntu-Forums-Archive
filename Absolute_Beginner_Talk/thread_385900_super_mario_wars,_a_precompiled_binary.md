---
title: "super mario wars, a precompiled binary?"
date: 2007-03-16
forum: Absolute Beginner Talk
---

### Post by stoer on 2007-03-16
Hi all,
I wanted to give Super  Mario Wars a try,
[http://smw.72dpiarmy.com/](http://smw.72dpiarmy.com/)
I've downloaded the source,   smw-binary.tar.gz file and extracted it.
I get a map (usr) and inside 2 more,  bin and share.
using checkinstall or make, sudo make install doesn't get me very far, 
Can anyone tell me, is this then a precompiled binary  and if so what's my next step?
Sorry if this seems too simple, just never encountered it before.
Any help, very much appreciated.

---

### Post by taurus on 2007-03-16
If it's a binary file, then you just run it directly from that same directory.  

```
./**filename**
```

---

### Post by stoer on 2007-03-16
> **taurus said:**
> If it's a binary file, then you just run it directly from that same directory.  

```
./**filename**
```

He, he....
said it was easy didn't i.
Thanks for the reply.

Guess i'm missing something else,
```
steve@laptop:~/supermario/usr/bin$ ./smw
./smw: error while loading shared libraries: libpng.so.3: cannot open shared object file: No such file or directory

```
And i cant find this (libpng.so.3) with synaptic...
I've extracted into my /home, should i have extracted it to anther location maybe?

---

### Post by taurus on 2007-03-16
Look for png (or libpng) with synaptic.  Also, what's the output of this command where you want to run that super mario game?

```
ldd smw
```

---

### Post by stoer on 2007-03-16
> **taurus said:**
> Look for png (or libpng) with synaptic.  Also, what's the output of this command where you want to run that super mario game?

```
ldd smw
```

Hi,
ok first.
steve@laptop:~/supermario/usr/bin$ ldd smw gave me the following

    ```
    linux-gate.so.1 =>  (0xffffe000)
        libSDL-1.2.so.0 => /usr/lib/libSDL-1.2.so.0 (0xb7ee6000)
        libpthread.so.0 => /lib/tls/i686/cmov/libpthread.so.0 (0xb7ebd000)
        libSDL_image-1.2.so.0 => /usr/lib/libSDL_image-1.2.so.0 (0xb7ea1000)
        libSDL_mixer-1.2.so.0 => /usr/lib/libSDL_mixer-1.2.so.0 (0xb7e33000)
        libpng.so.3 => not found
        libstdc++.so.6 => /usr/lib/libstdc++.so.6 (0xb7d5e000)
        libm.so.6 => /lib/tls/i686/cmov/libm.so.6 (0xb7d3c000)
        libgcc_s.so.1 => /lib/libgcc_s.so.1 (0xb7d32000)
        libc.so.6 => /lib/tls/i686/cmov/libc.so.6 (0xb7c02000)
        libasound.so.2 => /usr/lib/libasound.so.2 (0xb7b4d000)
        libdl.so.2 => /lib/tls/i686/cmov/libdl.so.2 (0xb7b4a000)
        libX11.so.6 => /usr/lib/libX11.so.6 (0xb7a64000)
        libXext.so.6 => /usr/lib/libXext.so.6 (0xb7a57000)
        /lib/ld-linux.so.2 (0xb7f71000)
        libtiff.so.4 => /usr/lib/libtiff.so.4 (0xb7a07000)
        libjpeg.so.62 => /usr/lib/libjpeg.so.62 (0xb79e7000)
        libpng12.so.0 => /usr/lib/libpng12.so.0 (0xb79c4000)
        libz.so.1 => /usr/lib/libz.so.1 (0xb79b0000)
        libvorbisfile.so.3 => /usr/lib/libvorbisfile.so.3 (0xb79a8000)
        libvorbis.so.0 => /usr/lib/libvorbis.so.0 (0xb7980000)
        libogg.so.0 => /usr/lib/libogg.so.0 (0xb797b000)
        libsmpeg-0.4.so.0 => /usr/lib/libsmpeg-0.4.so.0 (0xb7922000)
        libXau.so.6 => /usr/lib/libXau.so.6 (0xb791f000)
```

So in synaptic looked for libpng and found 
libpng3
libpng3-dev
Installed them both.
and now,

```
steve@laptop:~/supermario/usr/bin$ ldd smw
        linux-gate.so.1 =>  (0xffffe000)
        libSDL-1.2.so.0 => /usr/lib/libSDL-1.2.so.0 (0xb7f4c000)
        libpthread.so.0 => /lib/tls/i686/cmov/libpthread.so.0 (0xb7f23000)
        libSDL_image-1.2.so.0 => /usr/lib/libSDL_image-1.2.so.0 (0xb7f07000)
        libSDL_mixer-1.2.so.0 => /usr/lib/libSDL_mixer-1.2.so.0 (0xb7e99000)
        libpng.so.3 => /usr/lib/libpng.so.3 (0xb7e76000)
        libstdc++.so.6 => /usr/lib/libstdc++.so.6 (0xb7da1000)
        libm.so.6 => /lib/tls/i686/cmov/libm.so.6 (0xb7d7f000)
        libgcc_s.so.1 => /lib/libgcc_s.so.1 (0xb7d75000)
        libc.so.6 => /lib/tls/i686/cmov/libc.so.6 (0xb7c45000)
        libasound.so.2 => /usr/lib/libasound.so.2 (0xb7b90000)
        libdl.so.2 => /lib/tls/i686/cmov/libdl.so.2 (0xb7b8d000)
        libX11.so.6 => /usr/lib/libX11.so.6 (0xb7aa7000)
        libXext.so.6 => /usr/lib/libXext.so.6 (0xb7a9a000)
        /lib/ld-linux.so.2 (0xb7fd7000)
        libtiff.so.4 => /usr/lib/libtiff.so.4 (0xb7a4a000)
        libjpeg.so.62 => /usr/lib/libjpeg.so.62 (0xb7a2a000)
        libz.so.1 => /usr/lib/libz.so.1 (0xb7a16000)
        libvorbisfile.so.3 => /usr/lib/libvorbisfile.so.3 (0xb7a0e000)
        libvorbis.so.0 => /usr/lib/libvorbis.so.0 (0xb79e6000)
        libogg.so.0 => /usr/lib/libogg.so.0 (0xb79e1000)
        libsmpeg-0.4.so.0 => /usr/lib/libsmpeg-0.4.so.0 (0xb7989000)
        libXau.so.6 => /usr/lib/libXau.so.6 (0xb7985000)
```

Also,
./smw now gives the following error,

steve@laptop:~/supermario/usr/bin$ ./smw
ERROR: Empty map directory!


Any idea what i got wrong?

---

### Post by taurus on 2007-03-16
What's the output of this command?

```
ls -la ~/supermario
```

---

### Post by stoer on 2007-03-16
> **taurus said:**
> What's the output of this command?

```
ls -la ~/supermario
```

Output is

```
steve@laptop:~/supermario/usr/bin$ ls -la ~/supermario
total 8984
drwxr-xr-x   3 steve steve    4096 2007-03-16 14:55 .
drwxr-xr-x 127 steve steve    8192 2007-03-16 14:33 ..
-rw-r--r--   1 steve steve 9162829 2007-03-16 14:36 smw-binary.tar.gz
drwxr-xr-x   4 steve steve    4096 2007-01-01 21:47 usr
```

---

### Post by taurus on 2007-03-16
Okay, looks like your Super Mario, smw, is looking for the maps in /usr/share/smw/maps.  Therefore, you need to unpack it to /.

Copy smw-binary.tar.gz to root directory and unpack it from there.  

```
cd ~/supermario
sudo cp smw-binary.tar.gz /
cd /
sudo tar xvzf smw-binary.tar.gz
sudo rm smw-binary.tar.gz
cd ~
smw
```
If it runs successfully, you can delete the version in your $HOME directory since you don't need it anymore.

```
rm -rf ~/supermario
```

---

### Post by stoer on 2007-03-16
Taurus,
many thanks, that did it.
Works a treat now.
Cheers!

---

