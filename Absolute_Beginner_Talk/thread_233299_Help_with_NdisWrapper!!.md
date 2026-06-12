---
title: "Help with NdisWrapper!!"
date: 2006-08-09
forum: Absolute Beginner Talk
---

### Post by WalmartSniperLX on 2006-08-09
Im using the wiki instructions :

[http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation](http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation)

and when i type in 'make' it says:


[I]patrick@patrick-desktop:~/ndiswrapper-1.22$ make
make -C driver
make[1]: Entering directory `/home/patrick/ndiswrapper-1.22/driver'
Can't find kernel build files in /lib/modules/2.6.15-26-386/build;
  give the path to kernel build directory with
  KBUILD=<path> argument to make
make[1]: *** [prereq_check] Error 1
make[1]: Leaving directory `/home/patrick/ndiswrapper-1.22/driver'
make: *** [all] Error 2[/I]


What does this mean?

---

### Post by GuitarHero on 2006-08-09
try 
sudo aptitude install build-essentials
and do it again.

---

### Post by WalmartSniperLX on 2006-08-09
> **GuitarHero said:**
> try 
sudo aptitude install build-essentials
and do it again.

Should I do that in the source Directory or in the main?

---

### Post by GuitarHero on 2006-08-09
It shouldnt matter, just open up a terminal and do it.

---

### Post by WalmartSniperLX on 2006-08-09
> **GuitarHero said:**
> It shouldnt matter, just open up a terminal and do it.

Heres what i got in return:

[I]Couldn't find package "build", and more than 40
packages contain "build" in their name.
Couldn't find any package whose name or description matched "essentials"
No packages will be installed, upgraded, or removed.[/I]

---

### Post by maniacmusician on 2006-08-10
alright. 1st off, you're entering the command wrong. you probably have a space between build and essential. but before that, please answer this question:

do you have internet access on the machine that you're trying to set up wireless networking on? this is pretty crucial, as it will determine how i help you. 

also, you do not need build essential; there is already a version of ndiswrapper in the repositories, you do not need to compile one from source. i went back and read your first few posts on this forum, and they indicate that this is your first stab at ndiswrapper. now we start our quest for wireless.

Step1. If you DO have an internet connection on the machine that you need wireless on, type this in terminal:

sudo apt-get install ndiswrapper-utils

or, if you want to get used to graphical interfaces, you can use synaptic package manager to find ndiswrapper-utils. but this is the package you need,  

Step 2: you also have to find the correct driver for your wireless card. we're going to follow the ndiswrapper wiki step by step (but we're skipping the compiling; we used a package so that's already done automatically). i've already done this, but it'll be good for you. this is what the wiki says to do:

> 
Install Windows driver

Important: Do NOT use the drivers on your CD. They may work, but you may experience kernel crashes, etc., if the driver on your CD has not been tested.
Instead, you need to download the appropriate Windows XP driver for your card from the wiki entry list. To identify the driver that you need, first identify the card you have with 'lspci' and note the first column such as 0000:00:0c.0 and then find out the PCI ID of the card that with 'lspci -n' corresponding to the first column of 'lspci' output.
The PCI ID is third column or fourth in some distributions and of the form '104c:8400'. Now you need to get the Windows driver for this chipset. In the list, find out an entry for the same PCI ID, and download the driver corresponding to it.

Step 3: so crack open a terminal, enter lspci, and find your card (it needs to be inserted). ie, mine is "0000:02:02.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)" You have to remember that number in front of the line. 

Step 4: Then you enter 

lspci -n

then, using that number from the front of that line you found before, you track down the pci ID of your card. mine is "0000:02:02.0 0280: 14e4:4320 (rev 03)" since that first number matches the number from before, we know that the pci id of my card is "14e4:4320 (rev03)" yes, the rev is important too. After you get this far, post back here and we'll go from there. 

oh and please post your ouputs after lspci and lspci -n and identify your card's pci id

thanks.

---

### Post by WalmartSniperLX on 2006-08-12
OmG thanks a lot for the help I didnt even notice the pvt message you gave me. I appreciate it !! :D :D Network is showing up but I need the security code but thats just me getting up and finding the paper. :p 8-)

---

