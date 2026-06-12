---
title: "regarding libgtk"
date: 2005-05-14
forum: Absolute Beginner Talk
---

### Post by animesh on 2005-05-14
I am a newbie to linux and I have installed ubuntu .Now whenever I am installing any thing the libgtk creates problem .there is always the same error.I cannot install any thing 
  Below is what happens during one such try. Plz help me I am stranded  as now in everything I try to install ultimately leads to libgtk


root@animesh:/home # apt-get -f install
Reading Package Lists... Done
Building Dependency Tree... Done
Correcting dependencies... Done
The following extra packages will be installed:
  libgtk1.2 libgtk1.2-common
The following NEW packages will be installed:
  libgtk1.2 libgtk1.2-common
0 upgraded, 2 newly installed, 0 to remove and 101 not upgraded.
86 not fully installed or removed.
Need to get 0B/1051kB of archives.
After unpacking 2744kB of additional disk space will be used.
Do you want to continue? [Y/n] Y

Preconfiguring packages ...
(Reading database ... 67889 files and directories currently installed.)
Unpacking libgtk1.2-common (from .../libgtk1.2-common_1.2.10-17_all.deb) ...
dpkg: error processing /var/cache/apt/archives/libgtk1.2-common_1.2.10-17_all.deb (--unpack):
 trying to overwrite `/usr/share/locale/az/LC_MESSAGES/gtk+.mo', which is also in package gtk+
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Unpacking libgtk1.2 (from .../libgtk1.2_1.2.10-17_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/libgtk1.2_1.2.10-17_i386.deb (--unpack):
 trying to overwrite `/usr/lib/libgdk-1.2.so.0.9.1', which is also in package gtk+
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/libgtk1.2-common_1.2.10-17_all.deb
 /var/cache/apt/archives/libgtk1.2_1.2.10-17_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by Xian on 2005-05-14
[QUOTE=animesh]Preconfiguring packages ...
(Reading database ... 67889 files and directories currently installed.)
Unpacking libgtk1.2-common (from .../libgtk1.2-common_1.2.10-17_all.deb) ...
dpkg: error processing /var/cache/apt/archives/libgtk1.2-common_1.2.10-17_all.deb (--unpack):
 trying to overwrite `/usr/share/locale/az/LC_MESSAGES/gtk+.mo', which is also in package gtk+
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Unpacking libgtk1.2 (from .../libgtk1.2_1.2.10-17_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/libgtk1.2_1.2.10-17_i386.deb (--unpack):
 trying to overwrite `/usr/lib/libgdk-1.2.so.0.9.1', which is also in package gtk+
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/libgtk1.2-common_1.2.10-17_all.deb
 /var/cache/apt/archives/libgtk1.2_1.2.10-17_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)[/QUOTE]
Open a terminal and input the following:

```
$ sudo dpkg -i --force-overwrite /var/cache/apt/archives/libgtk1.2-common_1.2.10-17_all.deb
$ sudo dpkg -i --force-overwrite /var/cache/apt/archives/libgtk1.2_1.2.10-17_i386.deb
```

Then do a couple of more commands to clean up:

```
$ sudo dpkg --configure -a
$ sudo apt-get -f install

```

---

### Post by animesh on 2005-05-15
Thnks very very much this problem was a big big  headache for me  \\:D/

---

