---
title: "Sorry to be so noob but..."
date: 2005-07-19
forum: Absolute Beginner Talk
---

### Post by soleside on 2005-07-19
Hi,

I've only just finished my first installation of Ubuntu and I have a couple of very noob questions about it that I'd appreciate some help with.

Due to having a Speedtouch 330 modem I have had to download drivers through my Windows boot and pop them onto disc. no probs so far though when I boot the disc in Ubuntu I can only see part of the file name. e.g 'speedto~1' as opposed to 'speedtouchconf-06-03-2005.tar' so my first question is: Can I alter the appearence of Ubuntu so that i can see the whole of the filename?

Another query I have is with the installation/configuration of my modem, it's the silver Speedtouch 330 and I was wondering if anyone has a tried and tested way of installing it? There is a method I've seen on these forums (courtesy of Karlos) which I'd like to try in the meantime however it says to apt-get gcc & g++ from the Ubuntu CD, how exactly (step by step preferable) do I do this?

Sorry to be such a pain-in-the-bum noob but any help would be greatly appreciated. Thanks in advance.  :-D

---

### Post by wellery on 2005-07-19
this will take care of your filename problems:

[http://www.ubuntuforums.org/showthread.php?t=37507&highlight=floppy+long+filenames](http://www.ubuntuforums.org/showthread.php?t=37507&highlight=floppy+long+filenames)

---

### Post by poofyhairguy on 2005-07-19
[QUOTE=soleside] apt-get gcc & g++[/QUOTE]

Put in the install CD. Make sure you still have the CD line in the sources.list. (if you don't know what that is you are good).

the enter this command in the regular terminal:

> 
sudo apt-get install build-essential

to install all of that easily.

---

### Post by soleside on 2005-07-19
Thanks for the pointers, very appreciated.

Just wish I could sort out this modem now ](*,)

---

### Post by aragorn2909 on 2005-07-19
Try [this](http://linux-usb.sourceforge.net/SpeedTouch/index.html) for the modem.

---

