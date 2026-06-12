---
title: "'06 MacPro 1,1 ubuntu version?"
date: 2017-12-09
forum: Apple Hardware Users
---

### Post by dflint2 on 2017-12-09
I'm kinda new to linux. 
I've used mint on an old laptop.

My ex-boss gave me his '06 MacPro 1,1, (stock X5150 stock vid card, 16gig ram) with a cinema display. 
I'm playing around making it into a linux box because I don't want to spend any money and OSX only has outdated browsers. 
I would like to use it for the kids homework and or steam / browsing. 

Plopped in an old ssd drive and removed the other HD, boots just to linux now.
Currently running the latest ubuntu 17.1 something, it works, just a little boggy. 

Any recommendations for a zippier version I should try?
Maybe a cheap ebay upgrade that would increase performance?

Thanx in advance.

---

### Post by mörgæs on 2017-12-09
Hi, welcome to the fora.

First let's see the hardware. Please copy and paste ```
sudo lshw -sanitize > lshw.txt
``` into the terminal, run it and post lshw.txt in CODE tags.

---

### Post by kevin160 on 2017-12-09
Congratulations on acquiring some giant silver goodness!  

So you know, El Capitan can be installed quite simply onto a Pro 1,1.  See [https://forums.macrumors.com/threads/2006-2007-mac-pro-1-1-2-1-and-os-x-el-capitan.1890435/](https://forums.macrumors.com/threads/2006-2007-mac-pro-1-1-2-1-and-os-x-el-capitan.1890435/) for starters.  

Ubuntu runs very well, too.  The only real problem I've struggled with is getting power management (hibernate) working properly.  Since these old machines use 120W at idle, this may be a concern for you.  

The 1,1 shipped with either an ATI X1900XT or an NVIDIA 7300 GT.  If you really only have one of these cards, you NEED to upgrade.  Video cards that have PCIe 2 will run into bottlenecks due to the Pro's PCIe 1.0 slots, but they will still work.  I would suggest finding something from around 2010-2012 time frame.  I have an ATI 5770 in mine.  My NVIDIA 660 Ti works, too, but it needs 2 power cables and might stress the caps in your 10 year old power supply.  See [https://forums.macrumors.com/threads/mac-pro-1-1-10-9-2-tiamo-graphic-card-suggestions.1712192/](https://forums.macrumors.com/threads/mac-pro-1-1-10-9-2-tiamo-graphic-card-suggestions.1712192/) for eBay options.  

Most cards from after 2010 shouldn't need flashing of a "mac" ROM, but you do miss the Apple logo at boot-time.  Since you are already booting straight to Linux, this shouldn't be an issue for you.  

Since you already have an SSD installed, do the video card upgrade and it'll be a totally usable machine.  I used my Pro 1,1 as my daily driver (including gaming) until about 2 years ago.

---

### Post by mörgæs on 2017-12-10
> **kevin160 said:**
> 
The 1,1 shipped with either an ATI X1900XT or an NVIDIA 7300 GT.

These cards are fine in my world. As a first step I suggest installing Lubuntu in stead of Ubuntu rather than buying more hardware.

---

### Post by kevin160 on 2017-12-12
> **mörgæs said:**
> These cards are fine in my world. As a first step I suggest installing Lubuntu in stead of Ubuntu rather than buying more hardware.

This is certainly one way to go.  But, I see the exact model of Powercolor ATI 5770 I currently have installed for $20 on eBay, so why not take advantage of the upgradeability of the Pro.  

The performance difference will allow Unity or Gnome instead of LXDE/Lubuntu.  

And if the OP wants to run MacOS El Capitan, the upgrade is required.  There will be screen tearing and other unpleasant artifacts otherwise.

---

