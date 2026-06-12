---
title: "Can't install Ubuntu on my PC"
date: 2007-02-11
forum: Absolute Beginner Talk
---

### Post by 656599933 on 2007-02-11
Hi there,

I can't install Ubuntu on my computer.

My first question is:  it is possible to install Ubuntu on a Pentium II, 400Mhz, 96Mb Ram and 6Gb HD, that only has FreeDOS installed and HD with FAT16?

If it is possible, then I need help to proceed with the installation. I have downloaded the file 'ubuntu-6.06.1-desktop-i386.iso', I have checked with md5sum that the file is ok. Then I have burned a cd with Nero, using the option 'burn image'. So I think the CD is ok.

Then I switch on th PC with the CD inside, and it boots from the CD. I can see the Ubuntu options and I have tried first and second options (1st: start or install ubuntu, 2nd: install Ubuntu in safe graphics mode).
- Both options start with 'Loading Linux Kernel' it goes from 0 to 100%, seems ok.
- Then a screen with 'Uncompressing Linux .... OK, booting the kernel.' 
- Then the Ubuntu logo with these texts: 'Loading essential drivers... ok'
- Then there are 2 diferents ways that the installation fails:

1 - 'Mounting root file system...ok'. And then it goes back to the screen 'Uncompressing Linux .... OK, booting the kernel.' and starts to add these errors:

[  195.425781] SQUASHFS error: zlib_fs returned unexpected result 0xfffffffd
[  195.426102] SQUASHFS error: unable to read fragment cache block [330d9e2]
[  195.426388] SQUASHFS error: unable to read page, block 330d9e2, size 60f0
[  256.982356] hdc: time out waiting for DMA
[  261.985450] hdc: drive not ready for command
[  326.509473] hdc: time out waiting for DMA
[  331.512578] hdc: drive not ready for command
[  451.586384] Buffer I/O error on device hdc, logical block 319666

2 - 'Mounting root file system...' never gets the ok and it goes back to the screen  'Uncompressing Linux .... OK, booting the kernel.' and add this error:

'BusyBox v1.01 (Debian 1:1.01-4ubuntu3) Built-in Shell (ash)
Enter 'help' for a list of built-in commands.

/bin/sh: can't access tty; job control turned off
#'

In both cases, then it hungs and nothig else.

What should I do?

Thanks in advance!!

Berni.

---

### Post by xpod on 2007-02-11
Your best bet with those specs is mabey Xubuntu but even then you might struggle.You can also use an "alternate cd" which dont require all the resources a live cd does but you obviously cant try the desktop out like you can with the live cd

You might still struggle though but there are other lighter distro`s so i`m sure you`ll find something that works if you hunt around....Distrowatch is good

---

### Post by rggavubt on 2007-02-11
I think you need at least 256MB if RAM.  Mine wouldn't install with 256MB RAM.  I had to get the alternate CD which installs in text mode to get Ubuntu installed.  I have ordered more RAM.  I also created a boot floopy with my old system and then formatted both hard drives before the install.  Do you need to keep the stuff that is on there?  I then had Ubuntu use the whole hard drive.  I'm a noobie that just installed Ubuntu and I like it so far.  It is sort of like the old MS DOS and you enter commands at the terminal prompt.

---

### Post by bulldog on 2007-02-11
Have to disappoint you,96MB of ram is not enough to boot the live cd.
There are other options for a linux distro,but gnome and KDE won't run very well on your system.
Do a search for distro's which are not so demanding on your hardware.

---

### Post by arochester on 2007-02-11
96Mb is low. The recommended hardware requirements are 256Mb. Have a look at "Installation/LowMemorySystems" on [https://help.ubuntu.com/community/Installation/LowMemorySystems](https://help.ubuntu.com/community/Installation/LowMemorySystems)

---

### Post by 656599933 on 2007-02-11
Thanks everybody for your time.

I see my system has very low mem, but I will try the way the link Arochester sent. I want to try with Ubuntu!

I will keep informed, so you can know if a PC with my specs can work with Ubuntu.

Thanks again, and c u soon.

---

### Post by Bartender on 2007-02-11
How do you feel about adding some RAM?  I don't know anything about your situation, but lots of old PC's of that vintage get tossed out every day.  A person with a little bit of resourcefulness oughta be able to find a 256 stick for little or no money.
Of course, that would depend on your motherboard.  You're getting back into the time frame where some boards wouldn't support very much memory per slot.
It shouldn't be hard to figure out what your motherboard is, how many RAM slots it has, and how much RAM per slot it can handle.

---

### Post by Unlockitall on 2007-02-11
id personally suggest damn small linux, but if you want something more complete, id suggest a ram expansion, they arent too expensive, and if you do that you will have a better chance at running a more complete distrobution.

---

### Post by Jussi01 on 2007-02-11
DSl, will definately run, but I would go with xubuntu alternate cd. I had it running nicely on a machine of the same specs but only 64mb ram.

---

