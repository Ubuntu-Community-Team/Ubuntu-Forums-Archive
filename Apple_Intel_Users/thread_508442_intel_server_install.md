---
title: "intel server install"
date: 2007-07-24
forum: Apple Intel Users
---

### Post by pspcz on 2007-07-24
Perhaps I am missing something obvious but I can not find any detailed info on install of ubuntu server on dual core mac

we are looking at installing feisty or dapper on a headless dual core mac mini, what disk do we use and what known issues are out there

installation on PPC was straightforward and well documented



Pz

---

### Post by cyberdork33 on 2007-07-24
you can use the 1386 or AMD64 version. (32bit vs 64bit)

As far as the detailed install, You will have to search around. Most people are installing on Macbooks and Macbook Pros, followed in popularity by iMacs. I have seen little information about the Mac Mini.

The Mactel-Linux page is a good source of information
[http://www.mactel-linux.org/wiki/Main_Page](http://www.mactel-linux.org/wiki/Main_Page)

Here are some threads related to the Mac Mini:
[http://ubuntuforums.org/showthread.php?t=437552](http://ubuntuforums.org/showthread.php?t=437552)
[http://ubuntuforums.org/showthread.php?t=435153](http://ubuntuforums.org/showthread.php?t=435153)
[http://ubuntuforums.org/showthread.php?t=363179](http://ubuntuforums.org/showthread.php?t=363179)
[http://ubuntuforums.org/showthread.php?t=369176](http://ubuntuforums.org/showthread.php?t=369176)
[http://ubuntuforums.org/showthread.php?t=465221](http://ubuntuforums.org/showthread.php?t=465221)
[http://ubuntuforums.org/showthread.php?t=427217](http://ubuntuforums.org/showthread.php?t=427217)
[http://ubuntuforums.org/showthread.php?t=401330](http://ubuntuforums.org/showthread.php?t=401330)

---

### Post by pspcz on 2007-07-24
thank you,

what if you dont mind me asking would be the reason for choosing 32 vx 64bit. excuse the ignorance i have not used anything but a PPC for over ten years


Pz

---

### Post by cyberdork33 on 2007-07-24
There are 64-bit PPC CPUs too.

There is generally more software available for 32-bit operating systems. If you are just going to use the machine as a server, then 64bit might be a valid alternative

[http://en.wikipedia.org/wiki/64-bit#32_vs_64_bit](http://en.wikipedia.org/wiki/64-bit#32_vs_64_bit)

---

### Post by netztier on 2007-07-24
> **pspcz said:**
> thank you,

what if you dont mind me asking would be the reason for choosing 32 vx 64bit. excuse the ignorance i have not used anything but a PPC for over ten years



I am also thinking about buying a Mac mini (Intel) to replace my fileserver. I want something small, silent and reasonably fast to hold my files - and that doesn't draw hundreds of Watts of electrical power. All of the NAS boxes I have come across are just too slow. 

I have an AMD64 system as my (Ubuntu) desktop, yet I run i386 on it since ever since 5.10.

I chose i386 over amd64 because back at that time, there were issues with Java, flash plugins, and some restricted modules not being available for "native" amd64. You had to to tremendous workarounds with 32bit chroot environments to get some of them running. I wanted to avoid all of that and stuck with 32bit since then. If ever it should make a minor performance disadvantage - I think I can live with it.

On a server, you generally have a lot less of these problems - unless you have some hardware that is only supported by the restricted-module packages - madwifi drivers for atheros chips come to mind, or X.org drivers for nVidia and ATI cards..

best regards

Marc

---

### Post by cyberdork33 on 2007-07-24
> **netztier said:**
> I am also thinking about buying a Mac mini (Intel) to replace my fileserver. I want something small, silent and reasonably fast to hold my files - and that doesn't draw hundreds of Watts of electrical power. All of the NAS boxes I have come across are just too slow. 

I have an AMD64 system as my (Ubuntu) desktop, yet I run i386 on it since ever since 5.10.

I chose i386 over amd64 because back at that time, there were issues with Java, flash plugins, and some restricted modules not being available for "native" amd64. You had to to tremendous workarounds with 32bit chroot environments to get some of them running. I wanted to avoid all of that and stuck with 32bit since then. If ever it should make a minor performance disadvantage - I think I can live with it.

On a server, you generally have a lot less of these problems - unless you have some hardware that is only supported by the restricted-module packages - madwifi drivers for atheros chips come to mind, or X.org drivers for nVidia and ATI cards..

best regards

Marc

Summed it up quite nicely. Just as an addon, there are 64-bit versions of the ATI driver, but the Mac mini should have intel graphics anyhow. I would have to do more research to see if the Airport card would work. You might be able to use ndiswrapper instead of the madwifi drivers.

---

### Post by pspcz on 2007-07-24
thank you for the help and suggestions

i will be trying out this install next week, will post my trials and tribulations :0

Pz

---

