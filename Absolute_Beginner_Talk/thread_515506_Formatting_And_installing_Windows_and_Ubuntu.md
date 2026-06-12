---
title: "Formatting And installing Windows and Ubuntu"
date: 2007-08-02
forum: Absolute Beginner Talk
---

### Post by riptreeper on 2007-08-02
I am formatting my hard drive and was wondering how I would install windows on a 10gb partition and Ubuntu or Kubuntu on a 50gb partition? I have a dell dimension 3250 running XP home and a 60gb hard drive running 256 mb of ram. I need windows to do school work and to run Office 2007 and was needing some help starting the format and installing both Operating systems. Thanks is advance for the help

---

### Post by jackmc on 2007-08-02
dual booting: [https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

Basically do a normal windows install, but during setup allocate 10gb rather than the full drive.

I am currently using a virtual machine, which I like better - it is using VirtualBox. This lets you run both operating systems at once. Virtualbox is fairly easy to set up as well. These instructions look pretty comprehensive if you want to try that:

[http://www.blog.arun-prabha.com/2007/05/07/installing-virtualbox-and-windows-using-virtualbox-in-ubuntu/](http://www.blog.arun-prabha.com/2007/05/07/installing-virtualbox-and-windows-using-virtualbox-in-ubuntu/)

---

### Post by forestpixie on 2007-08-02
You might want to look at using the alternate cd for installation - you might have problems with 256Mb RAM

---

### Post by riptreeper on 2007-08-02
It's been a very long time since I formatted a drive how would I go about that ?

---

### Post by riptreeper on 2007-08-02
What's the alternate cd ?

---

### Post by jackmc on 2007-08-02
ooh, I just saw the 256mb of ram.. Virtualbox is out of the question sorry.

You can boot from the Windows XP cd (just put it in the drive and restart the computer, and it *should* work, otherwise the bios needs editing). From there, you can follow the steps for where you want to install, and it will format the hard drive for you. 

From memory, you can even just let it do the whole drive, and then let the Ubuntu installer shrink it back down.

as Forestpixie said, you will probably need to install via the alternate CD, which I do not have experience with sorry.

---

### Post by jackmc on 2007-08-02
> **riptreeper said:**
> What's the alternate cd ?

Alternate CD - [http://releases.ubuntu.com/feisty/ubuntu-7.04-alternate-i386.iso](http://releases.ubuntu.com/feisty/ubuntu-7.04-alternate-i386.iso)

Basically, you dont get graphics to install with, it is a text based installer (that is my understanding at least)

---

### Post by riptreeper on 2007-08-02
Ok thanks for the help

---

### Post by jackmc on 2007-08-02
sure, let me know if you need anything else.

Here is a guide for the text based install - [http://users.bigpond.net.au/hermanzone/p2.htm](http://users.bigpond.net.au/hermanzone/p2.htm)

---

### Post by forestpixie on 2007-08-02
> **riptreeper said:**
> What's the alternate cd ?

text based install instead of a livecd - 256mb is the minmum recommended for a live cd - you get it from same dowmload page, theres a tick box directly below the start download button

[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

As far as the format question goes I would assume that the drive has had xp on it already.

Use XP to install as normal - put it in and startup - if BIOS is set to boot from cd it will start the xp install.

Once you've got beyond the loading part of the install - you should get the partition part of the install - you can delete the partition at that point - THEN you can make a new 10Gb partition and let XP install to that.

When you get to install Ubuntu - it will see unused space and you'll be able to install to it.

Edit - bit slow there, trouble thinking ;)

---

### Post by riptreeper on 2007-08-02
Sweet thanks.

---

