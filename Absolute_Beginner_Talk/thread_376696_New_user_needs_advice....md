---
title: "New user needs advice..."
date: 2007-03-05
forum: Absolute Beginner Talk
---

### Post by mramsey on 2007-03-05
Hi everyone, I am new to the Linux comunity and new to this board.  I would like to build a Linux box with ubuntu as the OS.  

I need to buy a box and components to start this process and need some advice as far as what to get.  I am going to go to my local comp shop to see what they have to offer (used equip or barebones unit).  Is there anything in particullar I should look for? Or stay away from?

---

### Post by PartisanEntity on 2007-03-05
IMO:

1. nvidia cards are easier to get to work than ati (based on my own experience)
2. broadcom network (wifi) cards are easier to set up than others

---

### Post by x1a4 on 2007-03-05
Hi,

[This thread](http://ubuntuforums.org/showthread.php?t=365630&highlight=boycott+hardware) should help.  

Personally, I prefer nVidia video cards and AMD processors on a Gigabyte motherboard.  Be sure NOT to get one of those winmodems (Conexant chipset).  For communications interface (fax/voice/data, ethernet) I like 3Com.

---

### Post by impediment on 2007-03-05
I am brand new to Linux, 2 wks now.   I would not get an ATI graphics card.  My computer does alot of redrawing no matter which distro or whichdrivers I use.  I  assume its because of my graphics card.

---

### Post by mramsey on 2007-03-05
> **x1a4 said:**
> Hi,

[This thread](http://ubuntuforums.org/showthread.php?t=365630&highlight=boycott+hardware) should help.  

Personally, I prefer nVidia video cards and AMD processors on a Gigabyte motherboard.  Be sure NOT to get one of those winmodems (Conexant chipset).  For communications interface (fax/voice/data, ethernet) I like 3Com.


Thanks x1a4, that just what I was looking for!

---

### Post by maniacmusician on 2007-03-05
> **PartisanEntity said:**
> IMO:

1. nvidia cards are easier to get to work than ati (based on my own experience)
2. broadcom network (wifi) cards are easier to set up than others
No way. Broadcom cards suck for Linux; you have to use ndiswrapper to get them to work, usually. 

Stick with Nvidia graphics cards, and get Prism Wireless.

My favorite builds these days are Gigabyte boards with Intel Core 2 Duo processors and of course nvidia video cards.

---

### Post by x1a4 on 2007-03-05
> **mramsey said:**
> Thanks x1a4, that just what I was looking for!

No problem, that's what this forum is here for.

---

### Post by maniacmusician on 2007-03-05
> **impediment said:**
> I am brand new to Linux, 2 wks now.   I would not get an ATI graphics card.  My computer does alot of redrawing no matter which distro or whichdrivers I use.  I  assume its because of my graphics card.
you are correct :) you can try to install the proprietary fglrx drivers. That may help a little.

---

### Post by xyz on 2007-03-05
[Just in case it's a laptop]("http://www.linux-laptop.net/")

---

### Post by tagra123 on 2007-03-05
Belkin Wireless (Most are plug & play) without ndis
Reallink ethernet cards are also plug & play.
NVIDIA is the way to go. I have ati cards here too, but the nvidia work much better.

---

### Post by maniacmusician on 2007-03-05
> **tagra123 said:**
> Belkin Wireless (Most are plug & play) without ndis
Reallink ethernet cards are also plug & play.
NVIDIA is the way to go. I have ati cards here too, but the nvidia work much better.
for wireless, the best shot is really something like Prism.

Everything else is a crapshoot, unless you do some research beforehand. I have Belkin gear at home, and I have to use ndiswrapper to get it to work.

---

### Post by Zzl1xndd on 2007-03-05
Also if you are gonna have wireless via PCI get something with the Arthos chipset

---

### Post by radioouman on 2007-03-05
Atheros chipset based wireless cards work really well with the madwifi drivers.  You'll get WPA and WPA2 encryption support (along with WEP).  There are plenty of Atheros based cards out there, but you have to do your research to figure out which ones have it.  I believe that there are some D-Link cards with Atheros chips now.  

Is there a reason that you are building a new system and not just partitioning the system that you are currently using (for a dual-boot setup)?  Grub works great for dual boot, and gets installed with Ubuntu.

---

### Post by mramsey on 2007-03-05
> **radioouman said:**
> 
Is there a reason that you are building a new system and not just partitioning the system that you are currently using (for a dual-boot setup)?  Grub works great for dual boot, and gets installed with Ubuntu.

Since I am new to this I really want to minimize my risk of screwing up my existing PC. The use for this "new" one has yet to be determined long term.  I would like to configure it  like a media pc to stream my audio and video files from my NAS box on the network to my home theater set up.  I have always wanted to give linux a go and the ubuntu distro seems to be the one for me.

Here is where I am right now...

Gigabyte GA8I865 - socket775 MATX mobo. this has onboard 6ch sound, video and network. 2GB max DDR RAM.  $69.00
Intel Celeron 331 2.66Ghz processor $55.00
Micro tower case  350w PS $49.00

What I have - (suplus components)
512MB PC2700 RAM
Western Digital Caviar WD200 20GB HDD
Generic CD/R/RW

Will the mobo and processor be good for general purpose or should I go for  something a little more robust? Is onboard video too limiting?:confused:

---

### Post by chaplanger on 2007-03-05
You might look to upgrade that processor to something other than Celeron.  In the long run you may be happier for a few $ more at the outset.

---

### Post by PartisanEntity on 2007-03-05
> **maniacmusician said:**
> No way. Broadcom cards suck for Linux; you have to use ndiswrapper to get them to work, usually. 

What's wrong with using ndiswrapper ?

---

### Post by mramsey on 2007-03-05
> **chaplanger said:**
> You might look to upgrade that processor to something other than Celeron.  In the long run you may be happier for a few $ more at the outset.

I thought that may be a little light but not knowing much about linux I wasn't sure how heavy to go.:)

---

### Post by Snookered on 2007-03-05
Check prices here. [http://www.newegg.com/](http://www.newegg.com/) Better than local shops . I got the MSI board (see sig) and  am very happy with it. You can always search places like Anandtech for reviews on mobo, processor, etc. I researched for at least six months to find what I wanted and could afford.
For wireless, check with manufacturer web sites to see they have linux drivers. Good results here with Netgear. WGT624 router and WG511U pcmcia and WG311T pci card. 
[http://www.linuxquestions.org/hcl/showproduct.php/product/874](http://www.linuxquestions.org/hcl/showproduct.php/product/874)  -WG311T
[http://digg.com/linux_unix/HOW-TO_Configure_Netgear_WG511U_in_Ubuntu_Linux](http://digg.com/linux_unix/HOW-TO_Configure_Netgear_WG511U_in_Ubuntu_Linux)  -WG511U

Note; Picked up the WG511U from EBay at COMPUSA auctions. Out bid 5 times and then payed $8 less than all the others! Total $21.50!

---

### Post by tagra123 on 2007-03-06
> **PartisanEntity said:**
> What's wrong with using ndiswrapper ?

I personally don't think anything is wrong with it. Some folks seem to get stuck on a brand.  All but 1 Belkin product I tried worked without ndiswrapper, and the one that didn't work out of the box worked just fine with the ndiswrapper.

My personal opinion is that when you are working on someone elses machine -- you want to show them how good ubuntu is -- not how bad their hardware is. Same if building your own. 
Try one. If it doesn't work with your system then take it back.  

One thing I'd recommend to anyone building a pc is to spend a little extra on good power supply:  FSP, ANTEC, ROSEWELL, etc...



You could always pick up a second harddrive for your existing machine.

---

### Post by tagra123 on 2007-03-06
> **Snookered said:**
> Check prices here. [url]
Note; Picked up the WG511U from EBay at COMPUSA auctions. Out bid 5 times and then payed $8 less than all the others! Total $21.50!


I use auctionsniper when I really want a bargain. They have bidgroups you can set up so if you wanted a card for $8.00 you select the auctions and put them in the bidgroup then give it the price you are willing to pay. It will place the bid for you in the last few seconds of the auction.  If you want more than one you can set that too. Great way to get a good price.

---

### Post by MrCheese on 2007-03-06
re previous suggestions for wifi cards - I have an Atheros-based pc card in my laptop which works out of the box. I spent a long time trying to get several unsuitable cards going before I bought my card for a whole £10.

Hardware support is now pretty excellent - as long as you don't get suckered with Win32-only peripherals you can't really go wrong. I have a Pentium-4 (1.8GHz) Compaq laptop and a 3Ghz desktop system with NVidia graphics card, both running the same Ubuntu (6.06 LTS) with no hardware issues at all.

If you are buying a pc/laptop specifically to run Linux then you have nothing to lose by experimenting. Just take note of previous advice re graphics cards, modems etc.

---

### Post by punzak on 2007-03-06
I haven't been using Linux for very long, but I can unequivocally recommend that you stay clear of anything with an Intel 3945ABG wireless card or a Toshiba A105-S4046 laptop.

My $.02

---

### Post by mramsey on 2007-03-28
:) Well after much thought and alot of research I found a PC on ebay that fit the bill.  I found a Dell Optiplec GX260 SFF P-4 2.4 Ghz pc with no OS and a 40 GIG HDD for $99! I got it yesterday threw in a GIG of RAM and 25 minutes later...Bam...a fresh, clean running Ubuntu PC was born!

This is awesome! If it weren't for all of my pc games its the only OS I would own! Thanks to all of those who helped!:biggrin:

---

### Post by kittyhawk63 on 2007-03-28
> **mramsey said:**
> :) Well after much thought and alot of research I found a PC on ebay that fit the bill.  I found a Dell Optiplec GX260 SFF P-4 2.4 Ghz pc with no OS and a 40 GIG HDD for $99! I got it yesterday threw in a GIG of RAM and 25 minutes later...Bam...a fresh, clean running Ubuntu PC was born!
This is awesome! If it weren't for all of my pc games its the only OS I would own! Thanks to all of those who helped!:biggrin:

Congratulations!  If you have any problems to develop, come back to Ubuntuforums.com.  There is always someone here who can help.
kh

---

