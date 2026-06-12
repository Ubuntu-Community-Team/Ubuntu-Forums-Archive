---
title: "Linksys WPC54G ver. 3 installation tutorial"
date: 2006-12-29
forum: Absolute Beginner Talk
---

### Post by Achetar on 2006-12-29
I created this PDF tutorial for getting the Linksys WPC54G version 3 wireless card.
It is compressed, so extract it first.
Hope this helps :)

Plz vote, and make sure Your version is the EXACT SAME VERSION AS THE ONE liSTED ABOVE OR THIS WILL PROBABLY NOT WORK! Also plz give me the reason for it not working (errors, etc.)

---

### Post by thirstygerry on 2007-02-15
Thank you!
I've been struggling with this card for weeks.
You rule
So again, thanks!

---

### Post by velkymx on 2007-03-22
ndiswrapper is no longer in the apt-get! Now what?

---

### Post by mclenrd on 2007-03-28
yeah... now what?

---

### Post by su_penguin on 2007-03-29
This would probably work but, the BIGGEST question is:

If a person never had an internet connection to begin with, and they're trying to *apt-get*, how are they suppose to install ndiswrapper and it's dependencies ( or any dependencies at all for that matter)?

---

### Post by mclenrd on 2007-03-29
i found the ndiswrapper thru the synaptic manager... installed fine.  now the dhclient bit of info is not working.

---

### Post by Achetar on 2007-04-12
If you do not have an internet connection available on your computer, then you may be able to use a library or work computer to download the package files to a CD or USB flash drive. I will attempt to find a way to get dhclient and ndiswrapper.

---

### Post by Achetar on 2007-04-12
Go into Synaptic Package Manager (System->Administration-Synaptic Package Manager) and search for ndiswrapper. Install 'ndiswrapper-common','ndiswrapper-utils','ndiswrapper-utils-1.1', and 'ndiswrapper-utils-1.8' and you will have ndiswrapper installed.
For dhclient install 'dhcdbd'.
I believe that will work. I will update the guide and re-upload it.

---

### Post by Achetar on 2007-04-12
Also, make sure you use sudo su root **before** attempting to use dhclient. Also test before you use it by entering: dhclient

---

### Post by Achetar on 2007-09-19
Alright, now upgrading to Feisty broke my ndiswrapper. If you are using Feisty, look at what I did [here]("http://ubuntuforums.org/showthread.php?t=554697"). Use it in accompaniment with my guide.

---

### Post by ItsManaged on 2007-12-03
> **Achetar said:**
> Alright, now upgrading to Feisty broke my ndiswrapper. If you are using Feisty, look at what I did [here]("http://ubuntuforums.org/showthread.php?t=554697"). Use it in accompaniment with my guide.

Gutsy 7.10 - just start synaptic package manager,  seach for ndiswrapper, select ndisgtk (it will select ndiswrapper-common and  ndiswrapper-utils 1.9) and install all three.

Copy the driver files and inf files (*.sys and *.inf) from the CD to the desktop

Go to System -> Administration - > Windows wireless drivers
Click install driver and select the inf file you copied from the CD.
Reboot then setup your wireless

---

### Post by Achetar on 2007-12-24
If ndisgtk works now good, it didn't work before. Also installing this card is much simpler now, simply install ndiswrapper then run:
```

sudo ndiswrapper -i <driver>.inf

```
and it works! W00T!

---

### Post by Voltxion on 2007-12-27
I was wondering where this PDF is... I just picked this card up and am having trouble installing it, I tried 7.10 but it takes up too much resources on my laptop so i switched to fluxbuntu latest and it reconized teh card but still will not connect to the wireless network, the encryption type is wpa personal i don't know if thats a problem

---

### Post by pabloag5 on 2007-12-30
Hi!!!
This is my first time with ubuntu linux and any linux operating system. I need to install my wireless card WPC54G ver. 3. I found some threads about it, but none have a step by step for a linux beginner. Could some one help me with this? Thank you and happy new year!!

---

### Post by Achetar on 2007-12-31
I will work on a new guide for it, though I may not be able to have a true "Fresh from Install" guide because I already have it set up on my laptop. It should consist of downloading the ndiswrapper packages from *Synaptic* 
or *packages.ubuntu.com*. Copying the .INF and .SYS files from the driver CD to your hard drive, running 
```

cd /path/to/file
sudo ndiswrapper -i <DRIVER_FILE_NAME>.INF
sudo modprobe ndiswrapper
```
Then add ndiswrapper and nm-applet (you may have to download that as well) to your startup programs, and rebooting. Then you should be able to connect, beware that the guide I wrote for this (the PDF one) is for Ubuntu 6.10, not 7.10 (the current version). What I wrote above (the guide) is generic and may be hard to figure out. I will see what I can do.

---

### Post by Achetar on 2008-01-06
I have now taken the PDF down becuase it does not work with Ubuntu versions 7.04 and up. I am working on writing a new one.

---

### Post by pprjack on 2008-04-25
So, why did this card work for me "out of the box" with Gutsy but has stopped working after my upgrade to Hardy?!!!

---

### Post by Achetar on 2008-05-16
You're asking the wrong guy. I fixed my internal wifi card so I use it now. But it's so old that it'll work with anything ;)

---

