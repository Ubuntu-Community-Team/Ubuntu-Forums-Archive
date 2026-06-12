---
title: "Where's my built-in wifi card?"
date: 2006-03-27
forum: Absolute Beginner Talk
---

### Post by Etoile on 2006-03-27
Hello all,

I'm a computer geek, but primarily Windows-oriented.  I wanted to experiment with Linux, and friends pointed me to Knoppix and Ubuntu.  I tried Knoppix first, couldn't get it to recognize my built-in wifi, and hated that it only wanted to run at 640x480.  So I figured I'd try Ubuntu instead.

Wow!  Ubuntu is gorgeous, and I love it.  My only problem: it still can't see my wifi card.  I have a Dell Inspiron 1150 laptop, with a built-in Dell wireless card.  It's my sole Internet connection when I'm on XP.

When I bring up the network connections box on Ubuntu, it sees eth0 (my ethernet card, which is a wired connection, and I don't use it) and my dialup modem, but it doesn't seem to know my wireless card exists.

Help!  I am so excited about Ubuntu and this is the only thing keeping me from using it!

---

### Post by Papa-san on 2006-03-27
```
lspci -n
``` should give a list of hardware, and you need to find the pci id (Mine is: PCI ID (14e4:4320) (rev 02) on a Dell lattitude c610)

```
sudo lshw -c network
```
will also give you info you need to find your drivers
ee this link for installing windows driver with ndiswrapper:
[https://wiki.ubuntu.com/WifiDocs/Driver/Ndiswrapper](https://wiki.ubuntu.com/WifiDocs/Driver/Ndiswrapper)

---

### Post by Etoile on 2006-03-27
...and then what? :)

---

### Post by Papa-san on 2006-03-27
Dude... you got a Dell.... lol

You're in for a LOT of fun...

Did you check out the ndiswrapper link?

---

### Post by Etoile on 2006-03-27
Heh, no, it wasn't there when I replied asking "then what" - you must have added it later.

Why do you say a Dell would be "a lot of fun" - are they not Linux friendly?  I know the Inspiron 1150 was on linux-on-laptops.com as working with several flavors.

Also, I notice ndiswrapper won't work with a Live CD, so perhaps this won't work for me after all.  I suppose there won't be any hope then.

---

### Post by Qrk on 2006-03-27
I'd recommend trying the current version of Ubuntu before giving up. Breezy (5.10) has better support for wireless cards than Hoary did.

Also check out [http://www.linux-laptop.net/](http://www.linux-laptop.net/) to see supported Laptop hardware in Linux (its incomplete, if you don't see yours, it may still be fine)

Lastly, Ubuntu is easy to install and ndswrapper is fairly easy to set up; don't be too worried about a hard disk installation unless you really can't do it.

---

### Post by Project 318 on 2006-03-27
According to this page
[http://www.hpl.hp.com/personal/Jean_Tourrilhes/Linux/Linux.Wireless.drivers.802.11b.html](http://www.hpl.hp.com/personal/Jean_Tourrilhes/Linux/Linux.Wireless.drivers.802.11b.html)
> ...Dell (Dell TrueMobile 1150 - on the other hand, the 1100 is an Aironet card)...

Aironet cards have a native linux driver and, if I'm not mistaken, are included with Ubuntu.  I could be wrong.
[http://airo-linux.sourceforge.net/](http://airo-linux.sourceforge.net/)

edit: ah i misread that article, it was saying the **1100** had the aironet card
oh well, the article might be of some help to somebody

---

### Post by Etoile on 2006-03-28
I think I might already be using Breezy, actually, and just selected the wrong one when signing up for this forum; I'll have to check when I get home tonight.  The 1150 does appear on linux-laptop.net a few times (although the only "generic" one is in French).

I don't mind installing Ubuntu onto the hard disk, my only concern there would be setting up a dual-boot system so I could access XP when I needed to.  (Not ready to make the jump yet.)

Tonight I will confirm what version of Ubuntu I am using (it's whatever was mentioned as "the latest stable version," so I think it *is* Breezy).  But I wonder: does it matter if the drivers are there, if it doesn't recognize the card exists?  My XP background leads me to think that it first must recognize the card and then install drivers, so is that not the case in Ubuntu?

---

### Post by Obor on 2006-03-28
[QUOTE=Etoile]
Why do you say a Dell would be "a lot of fun" - are they not Linux friendly?  I know the Inspiron 1150 was on linux-on-laptops.com as working with several flavors.

Also, I notice ndiswrapper won't work with a Live CD, so perhaps this won't work for me after all.  I suppose there won't be any hope then.[/QUOTE]

I think Papa San was refering to problems he had while trying to get his card working - [link]("http://ubuntuforums.org/showthread.php?t=148317")
quite entertaining and usefull to read :)

---

### Post by Etoile on 2006-03-30
I installed Breezy onto my HDD and used ndiswrapper and got my wi-fi working and got my Windows partition mounted and everything is *awesome*!  Thanks all!

---

