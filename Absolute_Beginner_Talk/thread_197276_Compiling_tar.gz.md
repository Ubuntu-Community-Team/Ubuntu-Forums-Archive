---
title: "Compiling tar.gz"
date: 2006-06-15
forum: Absolute Beginner Talk
---

### Post by evil_elman on 2006-06-15
Question from a person who've never compiled source code or similar.

I'm interested in playing the following game: [http://www.darkarts.co.za/projects/vultures/downloads/](http://www.darkarts.co.za/projects/vultures/downloads/)

There are quite a lot of packages to download. The question from me as a newbie is what the UNIX installer (bin.sh) files are?

As far as I know the tar.gz is basically the source code which I'll need to compile myself and the documentation for the above mentioned game is mentioning quite a lot of packages (SDL to name on) which also needs to be installed. Everything seems to be over-the-top complicated for a simple game like this....

Ideally, an explanation of the bin.sh files would be nice or a link to a good guide for tar.gz files.

---

### Post by bluevoodoo1 on 2006-06-15
[http://www.monkeyblog.org/ubuntu/installing/](http://www.monkeyblog.org/ubuntu/installing/)

See if there's something there to help.

---

### Post by evil_elman on 2006-06-15
After installing (what I think are all the needed packages) I finally come to these error messages... Any ideas?

```
Building and installing Slash'EM in /home/tobias/vultures/vulturesclawdir
vultures_gfl.c:14:23: error: SDL_image.h: No such file or directory
vultures_gfl.c: In function &#8216;vultures_load_surface&#8217;:
vultures_gfl.c:62: warning: pointer targets in passing argument 1 of &#8216;png_sig_cmp&#8217; differ in signedness
make[3]: *** [build_s/vultures_gfl.o] Error 1
make[2]: *** [../win/vultures/build_s/vultures.o] Error 2
make[1]: *** [vulturesclaw] Error 2
make: *** [slashem-home] Error 2

```

Btw... This is by sudo'ing the bin.sh file on above mentioned website...

---

### Post by Kilz on 2006-06-15
[QUOTE=evil_elman]Could someone tell me why I'm not allowed / nothing happens when i do the following: ```
sudo vultures-2.1.0-claw_unix-1.bin.sh
```

???

Is it because it's not Ubuntu-specific?

Just complains that there's no such script or file, basically.[/QUOTE]
You may not be in the directory that the file is in. If the file is on your desktop type 
cd ~/Desktop 
first, then the sudo command

---

### Post by Slicedbread on 2006-06-15
You probably dont have sdl libraries installed- go [here]("http://usrsrc.org/darcs/vultures/doc/INSTALL_unix.html") for installation instructions. (same site)

---

### Post by evil_elman on 2006-06-15
[QUOTE=Slicedbread]You probably dont have sdl libraries installed- go [here]("http://usrsrc.org/darcs/vultures/doc/INSTALL_unix.html") for installation instructions. (same site)[/QUOTE]
Yes, I thought of that as well... I've got the following packages installed (it gave quite a lot of error messages before I had these installed)

libsdl1.2debian
libsdl1.2debian-all
libsdl1.2-dev
libsdl-image1.2
libsdl-image1.2-dev
libsdl-mixer1.2
libsdl-mixer1.2-dev
libsdl-ttf2.0-0
libsdl-ttf2.0-dev

libpng12-0
libpng12-dev

For every package I installed the amount of error messages declined but I can't figure out what the last one is about...

I'm thinking I've got the wrong version of a package, perhaps...?

I've installed a couple of more or less necessary packages and current state is the following:

```

Building and installing Slash'EM in /home/tobias/vultures/vulturesclawdir
vultures_gfl.c: In function &#8216;vultures_load_surface&#8217;:
vultures_gfl.c:62: warning: pointer targets in passing argument 1 of &#8216;png_sig_cmp&#8217; differ in  signedness
make[2]: yacc: Command not found
make[2]: *** [dgn_yacc.c] Error 127
make[1]: *** [dungeon] Error 2
make: *** [slashem-home] Error 2

```

The resulting directory which is created is empty...

[b]EDIT:
Instead of trying to run the shell script installer or compile from source I instead opted for the older version's RPM package, ran Alien on it and installed the resulting .DEB package... Worked fine![/b]

---

