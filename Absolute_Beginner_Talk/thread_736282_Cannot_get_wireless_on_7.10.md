---
title: "Cannot get wireless on 7.10"
date: 2008-03-26
forum: Absolute Beginner Talk
---

### Post by ticknubbs on 2008-03-26
I have a new Gateway laptop and I just installed Ubuntu 7.10 on it dual boot. I cannot get it to connect to the internet wirelessly like my toshiba.(it did it virtually automatically) I looked up help on this forum but I am such a beginner that I need some help that is broken down a bit more. My laptop has the realtek RTL8187B in it for wireless connection. Is there anybody that can help? Thanks, Tick

---

### Post by dstew on 2008-03-26
Open a terminal window (Applications --> Accessories --> Terminal) and enter the following commands:```
lspci
ifconfig
iwconfig
```Post the output to the forum.

---

### Post by ticknubbs on 2008-03-26
It says"no wireless extensions" after I type in the iwconfig....

---

### Post by SunnyRabbiera on 2008-03-26
you may need to install ndiswrapper, lucky you have a dual boot so you can download all the files you need in windows and then transfer them to your Ubuntu partition.

---

### Post by ticknubbs on 2008-03-26
Can you tell me where to download that and how to get it from the windows to ubuntu partition? sorry for being such a newbie!

---

### Post by SunnyRabbiera on 2008-03-26
sure.
first go to the ndiswrapper website, and download the latest version:
[Ndiswrapper website]("http://ndiswrapper.sourceforge.net/joomla/")
you will also need to download stuff to compile ndiswrapper, go to the following web pages to download what you need:
[http://packages.ubuntu.com/gutsy/build-essential]("http://packages.ubuntu.com/gutsy/build-essential")
[http://packages.ubuntu.com/gutsy/dpkg-dev]("http://packages.ubuntu.com/gutsy/dpkg-dev")
[http://packages.ubuntu.com/gutsy/g++]("http://packages.ubuntu.com/gutsy/g++")
[http://packages.ubuntu.com/gutsy/gcc]("http://packages.ubuntu.com/gutsy/gcc")
[http://packages.ubuntu.com/gutsy/libc6-dev]("http://packages.ubuntu.com/gutsy/libc6-dev")
[http://packages.ubuntu.com/gutsy/make]("http://packages.ubuntu.com/gutsy/make")
all of these are needed, I know its a lot to take in but its the only way.
Now you do have a link on your desktop or in your computer to your windows drive yes?
hopefully you do, go to places in ubuntu and into computer and see if you have the windows drive listed, if not we may need to tweak your ubuntu system to automount windows drives.
but lets take this by the steps.

---

### Post by skidoo540 on 2008-03-26
alright, this is tick. I downloaded those items that you mentioned. I am unsure of what to do next. Nothing has happened automatically, so what do I have to do now in order to recognize my wireless card. Still no internet, let me know

---

### Post by SunnyRabbiera on 2008-03-26
well if you can read your windows drive just copy the files over from your windows partition to your linux partition.
you have to install those files and then compile ndiswrapper, after that you may need a driver for the card too, you can pretty much copy the driver if you know where it is on windows over to linux and use ndiswrapper to install it.
like I said we take this by the steps.

---

### Post by skidoo540 on 2008-03-26
alright, i got the computer to recognize the wireless card, but am unsure how to keep the settings for everytime i boot up. everytime i boot up, i have to reload the information from the beginning, let me know what you think. i need some help with the startup issue so that ubuntu recognizes the driver everytime. thanks, tick

---

