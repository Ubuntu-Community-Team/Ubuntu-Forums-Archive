---
title: "Macbook Pro Installation Issues"
date: 2007-09-25
forum: Apple Intel Users
---

### Post by Tophocles on 2007-09-25
Let me preface this post by saying that I'm totally new to Linux. I've never used it before, but want to give it a go.

I have a Macbook Pro 1.83, with 512 MB RAM and an 80 GB HD. I have an ATI Radeon X1600, which is the source of most of my problems.

Basically, my plan is to install to an external hard drive so that I have a bootable copy of Linux wherever I go.

My questions are as follows.

1. What filesystem should I use when pre-formatting the Ubuntu partition of my external hard drive? Currently, it's HFS+. Would that bring up compatibility issues with Linux? Will Ubuntu reformat that partition when it's installed?

2. My external HD is USB 2.0. Now, I am pretty sure that booting from USB 2.0 drives is not supported officially on Macbook Pros, but I have also read that it is possible. Does anyone have any further info about this?

3. Due to my having the ATI Radoen, X can't boot up from the Live CD. I am going to need to use the Alternative CD and install via command line. I'm then going to need to install closed source drivers for the ATI card, as detailed [here]("http://ubuntuforums.org/showthread.php?t=414194"). Will this update the card's firmware, or just the software Linux uses to run them? If the former is true, will this change the way they operate in Mac OS X? Will it break it? Furthermore, will I need to be connected to the internet for these commands to work? I am guessing so.

Is my setup just too unwieldy right now, with the USB HD, the graphics card, etc, to bother installing, and would a different Linux distribution, such as Fedora, work better?

Any advice you have would be useful, because this is getting pretty frustrating. Thanks!

---

### Post by cyberdork33 on 2007-09-25
> **Tophocles said:**
> 1. What filesystem should I use when pre-formatting the Ubuntu partition of my external hard drive? Currently, it's HFS+. Would that bring up compatibility issues with Linux? Will Ubuntu reformat that partition when it's installed?
Yes, just like windows or OSX, it will ask you to format partitions. There are various options here, but the default ext3 filesystem has a proven track record.

> 2. My external HD is USB 2.0. Now, I am pretty sure that booting from USB 2.0 drives is not supported officially on Macbook Pros, but I have also read that it is possible. Does anyone have any further info about this?You are going to have issues trying to boot from an external drive. Most that have got this working had to create a /boot partition on the main hard drive. This, of course, would ruin your portable linux system. You might try looking here as someone has claimed to get it working: [https://wiki.ubuntu.com/MacBookProFeisty](https://wiki.ubuntu.com/MacBookProFeisty)

> 3. Due to my having the ATI Radoen, X can't boot up from the Live CD. I am going to need to use the Alternative CD and install via command line. I'm then going to need to install closed source drivers for the ATI card, as detailed [here]("http://ubuntuforums.org/showthread.php?t=414194").Before we go further down this path, you can follow the directions in that thread on the live cd to get the display working. and install from the normal cd, except you don't reboot... or update the entire system. do these steps:

Use CTRL+ALT+F1 to get to a terminal then

```
sudo apt-get install xorg-driver-fglrx
sudo depmod -a
sudo aticonfig --initial
sudo aticonfig --overlay-type=Xv
sudo /etc/init.d/gdm restart
```If you get an error or something try that last command again... sometimes it doesn't work nicely.

> Will this update the card's firmware, or just the software Linux uses to run them? If the former is true, will this change the way they operate in Mac OS X? Will it break it?No, this affects the linux system.

> Furthermore, will I need to be connected to the internet for these commands to work? I am guessing so.yes, many packages are downloaded some may be copied from the cd

> Is my setup just too unwieldy right now, with the USB HD, the graphics card, etc, to bother installing, and would a different Linux distribution, such as Fedora, work better? See above about external drive. Unfortunately, it will be pretty much the same for any distro since we all really use the same software (there are some differences). We seem to have quite a few Mac people here though to help.

> Any advice you have would be useful, because this is getting pretty frustrating. Thanks!There is quite a bit of information in the wiki and in these forums for the problems you will encounter:[http://ubuntuforums.org/showthread.php?t=474144](http://ubuntuforums.org/showthread.php?t=474144)

---

### Post by Tophocles on 2007-09-25
Thanks. This is quite helpful&#8212;I'll see if I can get something up and running following your instructions.

---

