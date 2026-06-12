---
title: "Issues with WIFI"
date: 2007-05-03
forum: Absolute Beginner Talk
---

### Post by Exygot on 2007-05-03
I am having issues with using the WIFI on my Dell Inspiron 5160.  It has a Dell Wireless 1350 WLAN Mini-PCI Card.  Is this card even supported?  I am running Ubuntu 7.04.

---

### Post by overdrank on 2007-05-03
> **Exygot said:**
> I am having issues with using the WIFI on my Dell Inspiron 5160.  It has a Dell Wireless 1350 WLAN Mini-PCI Card.  Is this card even supported?  I am running Ubuntu 7.04.

Hi I hope this link will help you Good luck!
[https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)

:)

---

### Post by Exygot on 2007-05-04
I looked at the thing you posted it says that my card is not supported do i just need to download the drivers that are linked to the article to make it work?  Or will it never be able to work with ubuntu?

---

### Post by candtalan on 2007-05-04
It seems to need the use of ndiswrapper and also bcmwl5a.inf and the instructions are linked also.

These are given as:
[http://ndiswrapper.sourceforge.net/wiki/index.php/InstallationNdiswrapper](http://ndiswrapper.sourceforge.net/wiki/index.php/InstallationNdiswrapper)
[http://ndiswrapper.sourceforge.net/wiki/index.php?Distributions](http://ndiswrapper.sourceforge.net/wiki/index.php?Distributions)
[http://ndiswrapper.sourceforge.net/wiki/index.php/List](http://ndiswrapper.sourceforge.net/wiki/index.php/List)

It should work ok, although it is not quite as simple as a single click I think. For a beginner it may seem a bit complictaed, but do not be worried, take your time and come back here for comments when you need them?

---

### Post by jargoman on 2007-05-04
I think that you need to load windows drivers using a program called ndiswrapper. I also think that your card uses the same drver that mine does because you have a broadcom chip. 

Do you have a working ethernet connection so you can install ndiswrapper

$ sudo apt-get update
$ sudo apt-get install ndiswrapper

or
 
optionally you can use Synaptic Package Manager found in System > Administration

go this site download the file bcmwl5.zip
 [http://www.xpefiles.com/viewtopic.php?t=433&](http://www.xpefiles.com/viewtopic.php?t=433&)

right click on your newly downloaded folder bcmwl5_176.zip and select extract here

open a command line terminal and go to your extracted folder

$ cd ~Desktop/bcmwl5_175.zip_FILES
that's assuming it's on your desktop

then

$ sudo rmmod ndiswrapper
$ sudo rmmod bcm43xx

if you get a warning saying that it's not in /proc/modules thats ok

$ sudo ndiswrapper -i bcmwl5.inf
$ sudo modprobe ndiswrapper

you should be in buisiness! usally I have to press my wireless button on and off a few times times to get the bugs out and retry my connection. 

If this works you need to ensure that this loads every boot

$ sudo gedit  /etc/modules

a text editor should open. you need to add 

ndiswrapper

at the end of the page so that ndiswrapper loads on boot.

save and quit then

$ sudo gedit /etc/modprobe.d/blacklist

add the line

blacklist bcm43xx

save then quit.

---

### Post by Acglaphotis on 2007-05-04
I have the same card and this worked for me no further configuration: 

```
sudo aptitude install bcm43xx-fwcutter
```

Ndiswrapper wont work.... i assure you.

-Acgla

EDIT: BTW you should install wifi-radar to manage your wireless.

---

