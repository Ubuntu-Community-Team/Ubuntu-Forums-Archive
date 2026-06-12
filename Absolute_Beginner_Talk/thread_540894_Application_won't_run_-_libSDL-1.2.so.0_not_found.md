---
title: "Application won't run - libSDL-1.2.so.0 not found"
date: 2007-09-02
forum: Absolute Beginner Talk
---

### Post by bascule on 2007-09-02
Running Ubuntu 6.06 LTS and I'm trying to run the game Cube 1 ([http://www.cubeengine.com/cube.php4](http://www.cubeengine.com/cube.php4)). I'm familiar with the game under Windows, so I know the file structure etc.

I unzipped the tarball to /home/ed/games successfully. Did not need to chmod anything as the relevant executables were already 'r-x':
-rwxr-xr-x  1 ed ed  807 2005-08-24 18:54 cube_unix
-rwxr-xr-x 1 ed ed 226788 2005-08-29 22:20 linux_client

When I try to run the game, I get this error:
ed@ed-desktop:~/games/cube$ ./cube_unix
./bin_unix/linux_client: error while loading shared libraries: libSDL_image-1.2.so.0: cannot open shared object file: No such file or directory

I had assumed SDL would be installed by default in Ubuntu, but apparently not

I tried:
ed@ed-desktop:/$ sudo apt-get install sdl
Password:
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package sdl

This was the same if I tried the above with Libsdl or libSDL_image-1.2.so.0

So my question is, how do I install SDL...

FYI I'm a new WinXP > Ubuntu switcher and I really want to switch completely, but ATM I'm dual-booting, beacause it's getting apparently simple stuff to work like this that really *does my head in* in Linux :(

---

### Post by marsmissionaries on 2007-09-02
sudo apt-get install libsdl-image1.2

---

### Post by luisromangz on 2007-09-02
It is much easier to find a package you don't know exactly its name if you use Synaptic or Adept. Also, don't assume that the package is called the way you think it should be called, or has the same name as in other distributions.

---

### Post by Skrynesaver on 2007-09-02
Or on the command line use apt-cache search SDL then have a look at the resulting packages with apt-cache show <package name>

---

### Post by bascule on 2007-09-02
Thanks very much to you both - SDL is now installed, but of course I've hit the next unavailable package... LibSDL_mixer :-|

I can probably sort it myself from here, but a couple of related questions:

I've found Synaptic through the 'Advanced...' button in the default add/remove program and it is listing SDL stuff. Is it correct that there is no mention of SDL in the default package manager?

Is this *really* the only way to get a new Linux installation up to date with all required packages? It seems kind of clunky ;)

Do I really have to go through Synaptic looking for all these:
> ed@ed-desktop:~/games/cube/bin_unix$ ldd linux_client
        linux-gate.so.1 =>  (0xffffe000)
        libSDL-1.2.so.0 => /usr/lib/libSDL-1.2.so.0 (0xb7ea2000)
        libpthread.so.0 => /lib/tls/i686/cmov/libpthread.so.0 (0xb7e90000)
        libSDL_image-1.2.so.0 => /usr/lib/libSDL_image-1.2.so.0 (0xb7e74000)
        libSDL_mixer-1.2.so.0 => not found
        libz.so.1 => /usr/lib/libz.so.1 (0xb7e60000)
        libGL.so.1 => /usr/lib/libGL.so.1 (0xb7dfa000)
        libGLU.so.1 => /usr/lib/libGLU.so.1 (0xb7d84000)
        libstdc++.so.5 => /usr/lib/libstdc++.so.5 (0xb7cca000)
        libm.so.6 => /lib/tls/i686/cmov/libm.so.6 (0xb7ca7000)
        libgcc_s.so.1 => /lib/libgcc_s.so.1 (0xb7c9d000)
        libc.so.6 => /lib/tls/i686/cmov/libc.so.6 (0xb7b6e000)
        libX11.so.6 => /usr/lib/libX11.so.6 (0xb7a88000)
        libasound.so.2 => /usr/lib/libasound.so.2 (0xb79d3000)
        libdl.so.2 => /lib/tls/i686/cmov/libdl.so.2 (0xb79d0000)
        libXext.so.6 => /usr/lib/libXext.so.6 (0xb79c2000)
        /lib/ld-linux.so.2 (0xb7f37000)
        libtiff.so.4 => /usr/lib/libtiff.so.4 (0xb7972000)
        libjpeg.so.62 => /usr/lib/libjpeg.so.62 (0xb7953000)
        libpng12.so.0 => /usr/lib/libpng12.so.0 (0xb7930000)
        libXxf86vm.so.1 => /usr/lib/libXxf86vm.so.1 (0xb792b000)
        libdrm.so.2 => /usr/lib/libdrm.so.2 (0xb7923000)
        libstdc++.so.6 => /usr/lib/libstdc++.so.6 (0xb784e000)
        libXau.so.6 => /usr/lib/libXau.so.6 (0xb784b000)


---

### Post by Skrynesaver on 2007-09-02
Most of those are part of the standard install, the only ones that may present a problem are libGL  and libGLU which, (as far as I remember and I'm open to correction on this) need a configured 3D card to work properly
If an application is available as a .deb package it will install it's dependencies "automagically" however if you are installing an application without a .deb (or .rpm if using alien) then you have to fulfill all dependencies manually, (in windows this used to be known as "dll hell")

---

