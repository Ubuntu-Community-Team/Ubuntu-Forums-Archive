---
title: "audacity problem installing [Resolved]"
date: 2007-02-10
forum: Absolute Beginner Talk
---

### Post by rapattack1 on 2007-02-10
Hi I did ask before how to install Audacity but maybe I couldn't install it because of the different versions like amd64, i386 and powerpc I think. The machine I now want to install it on that isn't net connected yet as I haven't been able to get it to talk to any modem. I tried to install Audacity from a file I downloaded for another machine and this failed. Anyway the machine I now want it on has Edgy and is an AMD machine but I am confused as to this AMD 64 thing. My machine is 2 years old and I think AMD32?????? I don't know. I read somwhere that the AMD 64 is a new thing? So I am confused as to which version of Audacity I should get?

---

### Post by aysiu on 2007-02-10
According to [this page](http://packages.ubuntu.com/edgy/sound/audacity), Audacity is available for all three architectures--PowerPC, AMD64, and i386.

---

### Post by aysiu on 2007-02-10
Based on this image, I'd say you should download these packages:
audacity
libflac++5c2
libgtk1.2
libgtk1.2-common
libid3tag0
libmad0
libvorbisfile3
libwxgtk2.4-1

All those files can be found for download here:
[http://packages.ubuntu.com/edgy/sound/audacity](http://packages.ubuntu.com/edgy/sound/audacity)

Just pick the correct architecture--i386 or AMD64. You should know from the command ```
uname -m
``` whether you're using i386 or AMD64.

Once you've downloaded all the appropriate packages and copied them to the desktop of your non-connected computer, type these commands in the terminal: ```
cd ~/Desktop
sudo dpkg -i *.deb
```

---

### Post by rapattack1 on 2007-02-10
ah it says i686 ......that is odd. I thought I bought an AMD machine.

---

### Post by rapattack1 on 2007-02-10
Ah just realised something else too. I was trying to install the Hoary Hedgehog version on Edgy. Ahhhhhh. Anyway am downloading the i386 version for Edgy is that right?

---

### Post by rapattack1 on 2007-02-10
Well only one of those files didn't install and I have attached what it said in the terminal.

---

### Post by aysiu on 2007-02-10
You don't need to attach text files. You can just paste text straight into the post: ```
&#65279; sudo dpkg -i libwxgtk2.4-1_2.4.5.1ubuntu1_i386.deb
dpkg: error processing libwxgtk2.4-1_2.4.5.1ubuntu1_i386.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 libwxgtk2.4-1_2.4.5.1ubuntu1_i386.deb
``` Errors were encountered... hm. That doesn't sound good. Does ```
sudo dpkg --configure -a
``` help?

Is it possible you didn't *get* libwxgtk2.4-1_2.4.5.1ubuntu1_i386.deb? It's looking for it, but it's not there?

---

### Post by rapattack1 on 2007-02-11
Yep I realised that tonight that I could paste txt. I automatically attached because I had to bring the code over with the flash device. It was easier to just attach from the device than open, copy and paste. If you know what I mean.
libwxgtk2.4-1_2.4.5.1ubuntu1_i386.deb is there but maybe the file could have got corrupted during download?


sudo dpkg --conf -a
Password:
dpkg: unknown option --conf

Type dpkg --help for help about installing and deinstalling packages [*];
Use `dselect' or `aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;
Type dpkg --license for copyright license and lack of warranty (GNU GPL) [*].

Options marked [*] produce a lot of output - pipe it through `less' or `more' !

---

### Post by rapattack1 on 2007-02-11
I figured out what was the problem. There were 3 files missing so I looked around further than that link and found them. They were libgtk1.2, libgtk1.2-common. Oh and I redownloaded  libwxgtk2.4-1_2.4.5.1ubuntu1_i386.deb and that fixed it. So Audacity is installed. Thanks so much!!!!:KS

---

