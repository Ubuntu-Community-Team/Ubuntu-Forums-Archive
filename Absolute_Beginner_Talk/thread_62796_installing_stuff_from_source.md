---
title: "installing stuff from source"
date: 2005-09-05
forum: Absolute Beginner Talk
---

### Post by wilywampa on 2005-09-05
i installed ubuntu 5.04 today and got beep media player to play my music. i want to be able to use the play/pause/stop/etc keys on my keyboard, so i need to install the bmp-itouch plugin for bmp. i downloaded the tar.gz and extracted it to my desktop. i opened up a root terminal, navigated to that folder, then typed "./configure", "make", and "make install". it spewed a bunch of "directory does not exist" errors and the plugin was not installed. do i have to do it from a different directory or something? why, in linux, do you never specify the directory to which applications are installed? this stuff is confusing.

if someone wants, i can post what the terminal told me when i tried to do that. thanks for any help.

---

### Post by aysiu on 2005-09-05
Have you thought of just doing an alien install of a [bmp-itouch rpm](http://prdownloads.sourceforge.net/bmp-itouch/bmp-itouch-1.0.0-1bi.i386.rpm?download)?

---

### Post by wilywampa on 2005-09-05
i could do that. it's an older version, but that shouldn't matter too much. i would like to know why i can't make it work by building it from the source.

i'll try installing that version now.

edit: umm.. i'm stupid. what is an alien install and what do i do with that file?

---

### Post by tehwa on 2005-09-05
You might be missing some development libraries needed to compile. If you want to know why it's not compiling, paste the output of the commands here.

---

### Post by wilywampa on 2005-09-05
root@wilywampa:/home/wilywampa/Desktop/bmp-itouch-1.1.0 # ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
/bin/sh: /home/wilywampa/Desktop/bmp-itouch-1.1.0/missing: No such file or directory
configure: WARNING: `missing' script is too old or missing
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for style of include used by make... GNU
checking for gcc... no
checking for cc... no
checking for cc... no
checking for cl... no
configure: error: no acceptable C compiler found in $PATH
See `config.log' for more details.
root@wilywampa:/home/wilywampa/Desktop/bmp-itouch-1.1.0 #


i guess i have no compiler. that'd do it. should've looked more closely earlier. can i just get a compiler package from synaptic?

---

### Post by aysiu on 2005-09-05
[QUOTE=wilywampa]
edit: umm.. i'm stupid. what is an alien install and what do i do with that file?[/QUOTE] The alien command allows you to install packages that are alien to Debian-based distros (i.e., .rpms instead of .debs).

So you'd type *sudo alien -i bmp-itouch-1.0.0-1bi.i386.rpm* in a terminal, and it would install the rpm.

---

### Post by aysiu on 2005-09-05
[QUOTE=wilywampa]
i guess i have no compiler. that'd do it. should've looked more closely earlier. can i just get a compiler package from synaptic?[/QUOTE] I think it would be *sudo apt-get install gcc*

---

### Post by wilywampa on 2005-09-05
i installed the compilers, than had to install gtk+, then had to install the beep dev package. then it finally worked. now i also installed the bmp-docklet plugin successfully, but it's not working properly. when i click the tray icon it should hide or unhide the beep media player window. however, it only works when BMP is not playing anything. if it is, and i try to click the icon to hide the player, it exits. if i have the player hidden and try to play a song, it also exits. this is probably a bug that has nothing to do with ubuntu though, so i don't expect you to be able to fix that.

thanks for the help getting the compiler to work though.

---

### Post by wilywampa on 2005-09-05
well, it's a known bug in bmp causing it to crash.

[http://www.sosdg.org/~larne/bugs/show_bug.cgi?id=103](http://www.sosdg.org/~larne/bugs/show_bug.cgi?id=103)

there are patches listed there. i want to apply the newer one. how do i do that?

thanks.

---

### Post by aysiu on 2005-09-06
I know this isn't a solution to your problem--and I do hope you find one soon--but if you're just looking for a media player, AmaroK is pretty good. I use it all the time, and the keyboard shortcuts customization is built into it already without a plugin. [This](http://www.ubuntuforums.org/showthread.php?t=59132) is the only problem I've run into with AmaroK.

Again, not a solution--as perhaps you prefer Beep to AmaroK--but it may be a good in-the-meantime stop-gap measure.

---

