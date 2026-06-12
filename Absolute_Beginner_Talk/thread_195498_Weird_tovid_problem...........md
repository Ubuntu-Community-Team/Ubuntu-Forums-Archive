---
title: "Weird tovid problem.........."
date: 2006-06-12
forum: Absolute Beginner Talk
---

### Post by user1397 on 2006-06-12
In light of a recent post in my tovid howto thread, i decided to try out the new version of tovid, 0.27 instead of 0.24.  I uninstalled 0.24, and then I was still able to run the tovidgui.  My terminal out put for "which tovid" and "which tovidgui" are both in /usr/local/bin.  Does this mean that i can uninstall it, but it can still run somehow???:?:  That doesn't make any sense.

---

### Post by nalmeth on 2006-06-13
It might have just left some configuration files, that's all I can think of. 

have you tried
sudo apt-get --purge remove tovid?

---

### Post by user1397 on 2006-06-13
[quote=nalmeth]It might have just left some configuration files, that's all I can think of. 

have you tried
sudo apt-get --purge remove tovid?[/quote]when i do that, the output is: 
```
Reading package lists... Done
Building dependency tree... Done
Package tovid is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

---

### Post by user1397 on 2006-06-13
oops! nevermind this post!

---

### Post by user1397 on 2006-06-13
still stuck on this one! hmm :-k

---

### Post by taurus on 2006-06-13
How did you uninstall it?  What does "ls -la /usr/local/bin" look like then?

---

### Post by user1397 on 2006-06-13
[quote=taurus]How did you uninstall it?  What does "ls -la /usr/local/bin" look like then?[/quote]well i installed it from a tar.gz package, using checkinstall, so i just uninstalled it from synaptic later.

```
~$ ls -la /usr/local/bin
total 504
drwxr-xr-x 2 root root   4096 2006-06-12 21:39 .
drwxr-xr-x 9 root root   4096 2006-06-12 21:39 ..
-rwxr-xr-x 1 root root  20040 2006-06-12 21:39 idvid
-rwxr-xr-x 1 root root  11130 2006-06-12 21:39 makedvd
-rwxr-xr-x 1 root root  18514 2006-06-12 21:39 makemenu
-rwxr-xr-x 1 root root   4317 2006-06-12 21:39 makeslides
-rwxr-xr-x 1 root root   4725 2006-06-12 21:39 makevcd
-rwxr-xr-x 1 root root  20881 2006-06-12 21:39 makexml
-rwxr-xr-x 1 root root   6775 2006-06-12 21:39 postproc
-rwxr-xr-x 1 root root   4497 2006-06-12 21:39 previd
-rwxr-xr-x 1 root root    544 2006-06-12 21:39 pyidvid
-rwxr-xr-x 1 root root    809 2006-06-12 21:39 pymakemenu
-rwxr-xr-x 1 root root    738 2006-06-12 21:39 pymakexml
-rwxr-xr-x 1 root root    912 2006-06-12 21:39 pytovid
-rwxr-xr-x 1 root root  68153 2006-06-12 21:39 todisc
-rwxr-xr-x 1 root root   8659 2006-06-12 21:39 todisc-fade-routine
-rwxr-xr-x 1 root root  55068 2006-06-12 21:39 tovid
-rwxr-xr-x 1 root root   2498 2006-06-12 21:39 tovid-batch
-rwxr-xr-x 1 root root   1344 2006-06-12 21:39 tovidgui
-rwxr-xr-x 1 root root 173579 2006-05-30 18:39 tovidgui~
-rwxr-xr-x 1 root root  21011 2006-06-12 21:39 tovid-init
-rwxr-xr-x 1 root root   6286 2006-06-12 21:39 tovid-interactive
-rwxr-xr-x 1 root root   2698 2006-06-12 21:39 tovid-stats
-rwxr-xr-x 1 root root   6472 2006-06-12 21:39 tovid-test
```

---

### Post by taurus on 2006-06-13
You don't have to uninstall the old version.  Just install the new version and it will over-write the old version.

---

### Post by user1397 on 2006-06-13
ok, but now the problem lies on actually installing it! (srry  for being such a nisuance :p)

I downloaded this package: [tovid-0.27.tar.gz]("http://prdownloads.sourceforge.net/tovid/tovid-0.27.tar.gz?download") and in the wiki it says to do this:
```
$ ./configure
$ su -c "make install"
```
i'm no ubuntu master, but i do know that we dont use su and instead we use sudo, so how am i supposed to do this?

---

### Post by taurus on 2006-06-13
```

sudo make install

```

---

### Post by user1397 on 2006-06-13
i'm not sure if it worked or not, but here's the output:
```
$ sudo make install
Password:
make[1]: Entering directory `/home/erik/Desktop/downloads/tovid-0.27'
test -z "/usr/local/bin" || mkdir -p -- "/usr/local/bin"
 /usr/bin/install -c 'src/idvid' '/usr/local/bin/idvid'
 /usr/bin/install -c 'src/makedvd' '/usr/local/bin/makedvd'
 /usr/bin/install -c 'src/makemenu' '/usr/local/bin/makemenu'
 /usr/bin/install -c 'src/makeslides' '/usr/local/bin/makeslides'
 /usr/bin/install -c 'src/makevcd' '/usr/local/bin/makevcd'
 /usr/bin/install -c 'src/makexml' '/usr/local/bin/makexml'
 /usr/bin/install -c 'src/postproc' '/usr/local/bin/postproc'
 /usr/bin/install -c 'src/previd' '/usr/local/bin/previd'
 /usr/bin/install -c 'src/todisc' '/usr/local/bin/todisc'
 /usr/bin/install -c 'src/todisc-fade-routine' '/usr/local/bin/todisc-fade-routine'
 /usr/bin/install -c 'src/tovid' '/usr/local/bin/tovid'
 /usr/bin/install -c 'src/tovid-batch' '/usr/local/bin/tovid-batch'
 /usr/bin/install -c 'src/tovid-init' '/usr/local/bin/tovid-init'
 /usr/bin/install -c 'src/tovid-interactive' '/usr/local/bin/tovid-interactive'
 /usr/bin/install -c 'src/tovid-test' '/usr/local/bin/tovid-test'
 /usr/bin/install -c 'src/pyidvid' '/usr/local/bin/pyidvid'
 /usr/bin/install -c 'src/pytovid' '/usr/local/bin/pytovid'
 /usr/bin/install -c 'src/pymakemenu' '/usr/local/bin/pymakemenu'
 /usr/bin/install -c 'src/pymakexml' '/usr/local/bin/pymakexml'
 /usr/bin/install -c 'src/tovidgui' '/usr/local/bin/tovidgui'
 /usr/bin/install -c 'src/tovid-stats' '/usr/local/bin/tovid-stats'
test -z "/usr/local/lib/python2.4/site-packages/libtovid/gui" || mkdir -p -- "/usr/local/lib/python2.4/site-packages/libtovid/gui"
 /usr/bin/install -c -m 644 'libtovid/gui/configs.py' '/usr/local/lib/python2.4/site-packages/libtovid/gui/configs.py'
 /usr/bin/install -c -m 644 'libtovid/gui/constants.py' '/usr/local/lib/python2.4/site-packages/libtovid/gui/constants.py'
 /usr/bin/install -c -m 644 'libtovid/gui/controls.py' '/usr/local/lib/python2.4/site-packages/libtovid/gui/controls.py'
 /usr/bin/install -c -m 644 'libtovid/gui/dialogs.py' '/usr/local/lib/python2.4/site-packages/libtovid/gui/dialogs.py'
 /usr/bin/install -c -m 644 'libtovid/gui/frames.py' '/usr/local/lib/python2.4/site-packages/libtovid/gui/frames.py'
 /usr/bin/install -c -m 644 'libtovid/gui/icons.py' '/usr/local/lib/python2.4/site-packages/libtovid/gui/icons.py'
 /usr/bin/install -c -m 644 'libtovid/gui/__init__.py' '/usr/local/lib/python2.4/site-packages/libtovid/gui/__init__.py'
 /usr/bin/install -c -m 644 'libtovid/gui/options.py' '/usr/local/lib/python2.4/site-packages/libtovid/gui/options.py'
 /usr/bin/install -c -m 644 'libtovid/gui/panels.py' '/usr/local/lib/python2.4/site-packages/libtovid/gui/panels.py'
 /usr/bin/install -c -m 644 'libtovid/gui/util.py' '/usr/local/lib/python2.4/site-packages/libtovid/gui/util.py'
Byte-compiling python modules...
configs.py constants.py controls.py dialogs.py frames.py icons.py __init__.py options.py panels.py util.py
Byte-compiling python modules (optimized versions) ...
configs.py constants.py controls.py dialogs.py frames.py icons.py __init__.py options.py panels.py util.py
test -z "/usr/local/lib/python2.4/site-packages/libtovid" || mkdir -p -- "/usr/local/lib/python2.4/site-packages/libtovid"
 /usr/bin/install -c -m 644 'libtovid/cli.py' '/usr/local/lib/python2.4/site-packages/libtovid/cli.py'
 /usr/bin/install -c -m 644 'libtovid/disc.py' '/usr/local/lib/python2.4/site-packages/libtovid/disc.py'
 /usr/bin/install -c -m 644 'libtovid/globals.py' '/usr/local/lib/python2.4/site-packages/libtovid/globals.py'
 /usr/bin/install -c -m 644 'libtovid/__init__.py' '/usr/local/lib/python2.4/site-packages/libtovid/__init__.py'
 /usr/bin/install -c -m 644 'libtovid/media.py' '/usr/local/lib/python2.4/site-packages/libtovid/media.py'
 /usr/bin/install -c -m 644 'libtovid/menu.py' '/usr/local/lib/python2.4/site-packages/libtovid/menu.py'
 /usr/bin/install -c -m 644 'libtovid/opts.py' '/usr/local/lib/python2.4/site-packages/libtovid/opts.py'
 /usr/bin/install -c -m 644 'libtovid/standards.py' '/usr/local/lib/python2.4/site-packages/libtovid/standards.py'
 /usr/bin/install -c -m 644 'libtovid/stats.py' '/usr/local/lib/python2.4/site-packages/libtovid/stats.py'
 /usr/bin/install -c -m 644 'libtovid/tdl.py' '/usr/local/lib/python2.4/site-packages/libtovid/tdl.py'
 /usr/bin/install -c -m 644 'libtovid/testvid.py' '/usr/local/lib/python2.4/site-packages/libtovid/testvid.py'
 /usr/bin/install -c -m 644 'libtovid/textmenu.py' '/usr/local/lib/python2.4/site-packages/libtovid/textmenu.py'
 /usr/bin/install -c -m 644 'libtovid/thumbmenu.py' '/usr/local/lib/python2.4/site-packages/libtovid/thumbmenu.py'
 /usr/bin/install -c -m 644 'libtovid/utils.py' '/usr/local/lib/python2.4/site-packages/libtovid/utils.py'
 /usr/bin/install -c -m 644 'libtovid/video.py' '/usr/local/lib/python2.4/site-packages/libtovid/video.py'
 /usr/bin/install -c -m 644 'libtovid/VideoUtils.py' '/usr/local/lib/python2.4/site-packages/libtovid/VideoUtils.py'
Byte-compiling python modules...
cli.py disc.py globals.py __init__.py media.py menu.py opts.py standards.py stats.py tdl.py testvid.py  File "/usr/local/lib/python2.4/site-packages/libtovid/testvid.py", line 1
    Test-video generator
                       ^
SyntaxError: invalid syntax
 textmenu.py thumbmenu.py utils.py video.py VideoUtils.py
Byte-compiling python modules (optimized versions) ...
cli.py disc.py globals.py __init__.py media.py menu.py opts.py standards.py stats.py tdl.py testvid.py textmenu.py thumbmenu.py utils.py video.py VideoUtils.py
test -z "/usr/local/lib/python2.4/site-packages/libtovid/encoders" || mkdir -p -- "/usr/local/lib/python2.4/site-packages/libtovid/encoders"
 /usr/bin/install -c -m 644 'libtovid/encoders/ffmpeg.py' '/usr/local/lib/python2.4/site-packages/libtovid/encoders/ffmpeg.py'
 /usr/bin/install -c -m 644 'libtovid/encoders/__init__.py' '/usr/local/lib/python2.4/site-packages/libtovid/encoders/__init__.py'
 /usr/bin/install -c -m 644 'libtovid/encoders/mencoder.py' '/usr/local/lib/python2.4/site-packages/libtovid/encoders/mencoder.py'
 /usr/bin/install -c -m 644 'libtovid/encoders/mpeg2enc.py' '/usr/local/lib/python2.4/site-packages/libtovid/encoders/mpeg2enc.py'
Byte-compiling python modules...
ffmpeg.py __init__.py mencoder.py mpeg2enc.py
Byte-compiling python modules (optimized versions) ...
ffmpeg.py __init__.py mencoder.py mpeg2enc.py
test -z "/usr/local/man/man1" || mkdir -p -- "/usr/local/man/man1"
mkdir: cannot create directory `/usr/local/man': File exists
make[1]: *** [install-man1] Error 1
make[1]: Leaving directory `/home/erik/Desktop/downloads/tovid-0.27'
make: *** [install-am] Error 2
```

---

### Post by user1397 on 2006-06-15
i guess it installed correctly, cause everything works

---

