---
title: "WIFI Help needed."
date: 2007-05-19
forum: Absolute Beginner Talk
---

### Post by cinmachina on 2007-05-19
Ok I have scoured the forums trying to get the wireless card on my M6810 E-Machines Laptop to work. None of the guides (all 10) have worked, I have reinstalled the OS 3 times to be sure I didn't fudge something up irreversibly.

can someone Please help?

Here's the info I have.

OS Version: Ubuntu Desktop Version 7.04 (Feisty Fawn)
Wireless Card: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03) -- Found by using the lspci | grep Broadcom\Corporation command in a terminal session.

There seems to be a lot of guides that help with version 6.x installations, but nothing in the way of 7.04. Many of them also ask me to go into System --> Administration --> Synaptic Package Manager --> Settings --> Repositories --> and click an ADD button....it doesn't exist! It's not there! I'm supposed to check for something called "Universe"...it's not there either!

Can someone please help me get this installed? I'm pulling my hair out here. 

Thanks!

---

### Post by Hobo Joe on 2007-05-19
> **cinmachina said:**
> Ok I have scoured the forums trying to get the wireless card on my M6810 E-Machines Laptop to work. None of the guides (all 10) have worked, I have reinstalled the OS 3 times to be sure I didn't fudge something up irreversibly.

can someone Please help?

Here's the info I have.

OS Version: Ubuntu Desktop Version 7.04 (Feisty Fawn)
Wireless Card: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03) -- Found by using the lspci | grep Broadcom\Corporation command in a terminal session.

There seems to be a lot of guides that help with version 6.x installations, but nothing in the way of 7.04. Many of them also ask me to go into System --> Administration --> Synaptic Package Manager --> Settings --> Repositories --> and click an ADD button....it doesn't exist! It's not there! I'm supposed to check for something called "Universe"...it's not there either!

Can someone please help me get this installed? I'm pulling my hair out here. 

Thanks!

In the console, type:
```

gksudo gedit /etc/apt/sources.list

```
Then uncomment all the lines that are links. For example, if the line looks like this:
```

# deb http://us.archive.ubuntu.com/ubuntu/ feisty-updates main restricted

```
Make it look like this:
```

deb http://us.archive.ubuntu.com/ubuntu/ feisty-updates main restricted

```

But don't do the ones that say cd-rom.

---

### Post by Ozeuss on 2007-05-19
to add universe repository in feisty, the gui way
open synaptic-> click settings-repositories->on the "ubuntu software" tab (first one) tick the box that says "community-maintained open source software (universe)"

---

### Post by jm2003uk on 2007-05-19
There's also an 'add' button on the 'Third party software' tab....if you still need it to add some other repositories.

---

### Post by cinmachina on 2007-05-19
> **Hobo Joe said:**
> In the console, type:
```

gksudo gedit /etc/apt/sources.list

```
Then uncomment all the lines that are links. For example, if the line looks like this:
```

# deb http://us.archive.ubuntu.com/ubuntu/ feisty-updates main restricted

```
Make it look like this:
```

deb http://us.archive.ubuntu.com/ubuntu/ feisty-updates main restricted

```

But don't do the ones that say cd-rom.

Ok, that seemed to change the network Icon to some bars at the top, instead of a computer with an exclamation mark. Now what do I do to get it actually connected? How do I get it to recognize my card?

---

### Post by Happy_Man on 2007-05-19
Your add button is under the Third-Party Sofware tab. Universe tab says "Community-Maintained Open Source Software". Check the box, and click close.

---

### Post by ukripper on 2007-05-19
> **cinmachina said:**
> Ok I have scoured the forums trying to get the wireless card on my M6810 E-Machines Laptop to work. None of the guides (all 10) have worked, I have reinstalled the OS 3 times to be sure I didn't fudge something up irreversibly.

can someone Please help?

Here's the info I have.

OS Version: Ubuntu Desktop Version 7.04 (Feisty Fawn)
Wireless Card: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03) -- Found by using the lspci | grep Broadcom\Corporation command in a terminal session.

There seems to be a lot of guides that help with version 6.x installations, but nothing in the way of 7.04. Many of them also ask me to go into System --> Administration --> Synaptic Package Manager --> Settings --> Repositories --> and click an ADD button....it doesn't exist! It's not there! I'm supposed to check for something called "Universe"...it's not there either!




Can someone please help me get this installed? I'm pulling my hair out here. 

Thanks!







Try this guide [http://ubuntuforums.org/showthread.php?t=201902&highlight=bcm4306](http://ubuntuforums.org/showthread.php?t=201902&highlight=bcm4306)

One of the best guides used on forums with ndiswrapper

---

### Post by konungursvia on 2007-05-19
Not all laptops have hardware that has been ubuntu-tested extensively. If you're having problems, Debian sarge is a similar, but more laptop stable, distro you should try.

---

### Post by cinmachina on 2007-05-19
How do I install NDISWRAPPER from the CD? I can't get it to work on the net obviously. Any ideas?

---

### Post by Happy_Man on 2007-05-19
Stick the CD in the drive, open up Synaptic, go to settings, Third-Party Software, Add CD-ROm.

---

### Post by cinmachina on 2007-05-19
> **Happy_Man said:**
> Stick the CD in the drive, open up Synaptic, go to settings, Third-Party Software, Add CD-ROm.

Yeah I did that but it gets stuck at "unmounting cd-rom" ;(

This is very problematic

---

### Post by ukripper on 2007-05-19
> **cinmachina said:**
> Yeah I did that but it gets stuck at "unmounting cd-rom" ;(

This is very problematic

Have you tried internet connection to your network through wired network card?

---

### Post by cinmachina on 2007-05-19
I think that guide you posted will work, but I can't for the love of jesus christ get the gd ndiswrapper to install!!!
IF I can do that, I bet that guide will work.

I downloaded it onto a usb drive, and am trying to load it onto ubuntu, but I have no idea what it's asking me to do, rofl

I may be helpeless

---

### Post by cinmachina on 2007-05-19
I was finally able to fix my problem by doing the following:

1. [https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29?highlight=%28ndiswrapper%29#head-f1b6201d0b5822506a2df08fa5b8314f4237e765](https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29?highlight=%28ndiswrapper%29#head-f1b6201d0b5822506a2df08fa5b8314f4237e765) -- go here to download and install ntiswrapper

2. [http://ubuntuforums.org/showthread.php?t=201902&highlight=bcm4306](http://ubuntuforums.org/showthread.php?t=201902&highlight=bcm4306) -- go here and follow steps 6 - 9

Thanks all!

---

