---
title: "[SOLVED] libSDL problem when trying to run pdiaspora"
date: 2008-01-09
forum: Absolute Beginner Talk
---

### Post by acidzfire on 2008-01-09
I want to play this game, Project Diaspora. I play it all the time on windows but want to get it running on linux. there is a linux client available but i am having problems getting it to run. The client can be found here
[http://downloads.sourceforge.net/pdiaspora/pdiaspora_client-beta-1.1.9.tar.gz?modtime=1194914964&big_mirror=0]("http://downloads.sourceforge.net/pdiaspora/pdiaspora_client-beta-1.1.9.tar.gz?modtime=1194914964&big_mirror=0")

I extract it and enter the directory and type
```
./pdiaspora
```

and get this error.
```
./pdiaspora: error while loading shared libraries: libSDL_gfx.so.13: cannot open shared object file: No such file or directory

```

I have tried finding this by googling and searching synaptics. i found other libsdl packages and have installed them but nothing seems to work. The readme file that comes with the client says this:

> Required Libraries:
SDL
SDL_ttf
SDL_image
SDL_gfx

I ran 
```
ls /usr/lib/libSDL_*
```
and here are the results:
```
cary@tux-lap:~/pdiaspora_client-beta-1.1.9$ ls /usr/lib/libSDL_*
/usr/lib/libSDL_gfx.a               /usr/lib/libSDL_mixer.la
/usr/lib/libSDL_gfx.la              /usr/lib/libSDL_mixer.so
/usr/lib/libSDL_gfx.so              /usr/lib/libSDL_net-1.2.so.0
/usr/lib/libSDL_gfx.so.4            /usr/lib/libSDL_net-1.2.so.0.0.5
/usr/lib/libSDL_gfx.so.4.9.0        /usr/lib/libSDL_net.a
/usr/lib/libSDL_image-1.2.so.0      /usr/lib/libSDL_net.la
/usr/lib/libSDL_image-1.2.so.0.1.4  /usr/lib/libSDL_net.so
/usr/lib/libSDL_image.a             /usr/lib/libSDL_ttf-2.0.so.0
/usr/lib/libSDL_image.la            /usr/lib/libSDL_ttf-2.0.so.0.6.3
/usr/lib/libSDL_image.so            /usr/lib/libSDL_ttf.a
/usr/lib/libSDL_mixer-1.2.so.0      /usr/lib/libSDL_ttf.la
/usr/lib/libSDL_mixer-1.2.so.0.2.4  /usr/lib/libSDL_ttf.so
/usr/lib/libSDL_mixer.a
```

It looks to me like all the libraries are there. the client also comes with dll files for these packages. is there a way to extract/install dll files for use in linux.  There is also no make file. Here is a directory list of the game:

```
cary@tux-lap:~/pdiaspora_client-beta-1.1.9$ ls -ltr
total 2000
-rwxr--r-- 1 cary cary    208 2008-06-06 20:57 readme_linux.txt
-rwxr--r-- 1 cary cary 441498 2008-06-06 21:01 tiff.dll
-rwxr--r-- 1 cary cary  54272 2008-06-06 21:01 librle3.dll
-rwxr--r-- 1 cary cary 127488 2008-06-06 21:01 jpeg62.dll
-rwxr--r-- 1 cary cary  74240 2008-06-06 21:01 zlib1.dll
-rwxr--r-- 1 cary cary 248745 2008-06-06 21:01 sdl.dll
-rwxr--r-- 1 cary cary  12888 2008-06-06 21:01 mingwm10.dll
-rwxr--r-- 1 cary cary 203264 2008-06-06 21:01 libpng12.dll
-rwxr--r-- 1 cary cary 348160 2008-06-06 21:01 SDL_ttf.dll
-rwxr--r-- 1 cary cary  56565 2008-06-06 21:01 SDL_Image.dll
-rwxr--r-- 1 cary cary  86556 2008-06-06 21:01 SDL_gfx.dll
-rwxr-xr-x 1 cary cary 308662 2008-10-23 04:39 pdiaspora
drwxr-xr-x 3 cary cary   4096 2008-10-23 05:51 server
drwxr-xr-x 2 cary cary   4096 2008-10-23 05:51 fonts
drwxr-xr-x 6 cary cary   4096 2008-10-23 05:51 graphics
drwxr-xr-x 8 cary cary   4096 2008-10-23 05:51 sounds

```

Any help will be appreciated

---

### Post by acidzfire on 2008-01-09
ok. got it working. i had to make a hard link to libSDL_gfx.so.13 from the libSDL in the /usr/local dir

---

### Post by jtraal on 2008-04-01
I am having the same problem with Project Diaspora however I am running Mandriva 2008, not
Ubuntu.  You said you solved this problem by creating a hard link from something to something
in the /usr/local folder.

My questions are as follows:

1.  What is the exact syntax of the command you typed to do this?
2.  Did you put this link in /usr/local or /usr/local/bin?  Mandrake, by default, doesn't
export /usr/local but rather /usr/local/bin and /usr/local/sbin.  I'm not sure if this is
different on Ubuntu or if it even matters at all. 
3.  Does this require a reboot to be effective?

Oh, almost forgot... 
ls /usr/lib/libSDL_* returns the following:

/usr/lib/libSDL_gfx.so.0@                           /usr/lib/libSDL_net-1.2.so.0@
/usr/lib/libSDL_gfx.so.0.0.16*                     /usr/lib/libSDL_net-1.2.so.0.0.7*
/usr/lib/libSDL_image-1.2.so.0@                /usr/lib/libSDL_sound-1.0.so.1@
/usr/lib/libSDL_image-1.2.so.0.1.5*            /usr/lib/libSDL_sound-1.0.so.1.0.0*
/usr/lib/libSDL_mixer-1.2.so.0@                /usr/lib/libSDL_ttf-2.0.so.0@
/usr/lib/libSDL_mixer-1.2.so.0.2.6*            /usr/lib/libSDL_ttf-2.0.so.0.6.3*

Would you help me?

---

### Post by rork on 2008-04-24
I agree, a little more information about how to fix it would be helpfull, however you can find the command to create the symlink in [this thread](http://ubuntuforums.org/showthread.php?p=1100454&mode=linear#post1101418). Creating the link /usr/lib/ worked fine for me but I'm running Debian so I'm not sure it works the same on Mandrake.

It should work fine without rebooting.

---

