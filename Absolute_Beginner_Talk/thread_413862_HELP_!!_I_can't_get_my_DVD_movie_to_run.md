---
title: "HELP !! I can't get my DVD movie to run"
date: 2007-04-19
forum: Absolute Beginner Talk
---

### Post by beatman on 2007-04-19
Hi there Re the instruction
sudo apt-get install libdvdread3 libdvdcss2 ogle-mmx ogle-gui

I receive the following information:
Reading package lists... Done
Building dependency tree
Reading state information... Done
libdvdread3 is already the newest version.
libdvdread3 set to manual installed.
Package libdvdcss2 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libdvdcss2 has no installation candidate

Can anyone help me get my DVDs to run... they worked fin in the earlier version, with Automatix.

Many thanks in advance

:popcorn:

---

### Post by heimo on 2007-04-19
Did you try these instructions?
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

### Post by rustybronco on 2007-04-19
I have been running the alpha and beta versions of fiesty with no problems UNTIL i downloaded the latest rc last night (which i thought would be the same as the final version) and that is about the same message that I had seen... I hate to say it  but I think 7.04 is broken or possibly add/remove?, i'll find out tonight when I can devote more time.

---

### Post by locke.dragon on 2007-04-19
download vlc.  it's awesome with dvd's and it should fix it.  just pop the dvd disk in, open vlc, click file>>quick open and make sure you hit "dvd (menus)".  that's how i fixed it on my computer at least.  hope that helps!  :D

---

### Post by compiledkernel on 2007-04-19
[http://ubuntuforums.org/showthread.php?t=413624](http://ubuntuforums.org/showthread.php?t=413624)

Follow instructions therein to get libdvdcss2 package installed properly.

---

### Post by teddybairs1 on 2007-04-19
You need libdvdcss2 to run it. Unfortunately it's not available in the repositories. Ogle/Okle are practically worthless anyway. One way to get this and w32codecs is to add this line to your repositories:

deb [http://www.debian-multimedia.org](http://www.debian-multimedia.org) etch main

It's technically for debian etch (4.0), but it'll work for Ubuntu feisty because they're "genetically" related.

Another way to get it is to go to vlc's website and dig for it.

The reason why you need libdvdcss2 is because most storebought dvds have an encryption on them. The reason why it doesn't come by default (like it should) in Ubuntu is because there are issues regarding licencing and legality. However, all you have to do is grab it and install it and your dvds should run on any media player for ubuntu. I usually use kaffeine, but totem (the default for gnome based ubuntu) should run them as well.

If you have trouble adding this line or it doesn't work somehow, you can try going to the website indicated in the line and then searching for the codecs you want.
This should be it here:
[http://www.debian-multimedia.org/pool/main/libd/libdvdcss/](http://www.debian-multimedia.org/pool/main/libd/libdvdcss/)

---

### Post by rustybronco on 2007-04-19
Mr. locke.dragon, I use vlc and the problem I am having is with fiesty 7.04rc  and your not having any problems? what version do you have?

TEDDYBAIRS, i'll try your method tonight.

---

### Post by beatman on 2007-04-19
Heimo,
You were right on the button...
Thank you so much...

I can now watch my movie and enjoy the popcorn..

Cheers..

Beatman

:popcorn:

---

