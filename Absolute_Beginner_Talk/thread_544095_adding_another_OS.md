---
title: "adding another OS"
date: 2007-09-05
forum: Absolute Beginner Talk
---

### Post by garyed on 2007-09-05
I'm already dual booting Ubuntu Studio & XP with each on their own separate HD.
I want to add Windows 98 & triple boot but I'm not sure of the best way to do it.
My XP drive is formatted FAT32 all one partition.
1 - Would I be better using the XP drive or the Linux drive?
2 - Would I use gparted to partition the drive?
3  - Or would it be easier to use XP to dual boot with 98?
Any ideas

---

### Post by bam1234567 on 2007-09-05
Id say option 3 would be the best only for you. (Me? I don't like windows) but whatever you do don't triple boot~Big mistake!

---

### Post by sumguy231 on 2007-09-05
> Big mistake!
How so? It wouldn't be *easy* but it's possible.

---

### Post by dpar on 2007-09-06
Ya, I've had no problems whatsoever triple booting.

---

### Post by alienexplorers on 2007-09-06
Tried triple boot and had nothing but problems.  Went back to dual boot.

---

### Post by HermanAB on 2007-09-06
Hmm, dual booting is so 20th century... ;)

I don't do that anymore.  It is far more convenient to install VMware/Virtualbox/Qemu and install multiple systems as guests.  This way, you can run Windoze in a window without having to reboot.

Also, it is better to experiment on a virtual system (running Linux on VMware on Linux) than to accidentally screw up your base system.  I have at least 10 different systems that I can run at a moment's notice to test something and my base system always remains in good shape.

Just my tuppence worth!

H.

---

### Post by bam1234567 on 2007-09-06
I've tried it for ubuntu 2000 pro and XP i ended up just wiping the hard drive and intalling ubuntu and only ubuntu. I had nothing but problems just like alienexplorers. Well, that and i just plain hate windows. I was trying to make a guide on how to do it right but DAMN! I couldn't get i right for 2 weeks. Maybe the chipset has something to do with it? I don't know, but MOST, not all, have had probs with it. So i avoid it. As long as i have Mac OS and ubuntu, i'll be happy forever. :)

---

### Post by ayenack on 2007-09-06
Will 98 install alongside XP? I know that if you have NT4 installed you can't install 98 straight of it takes some real messing around. XP is NT4 with some bells and whistles so am not sure if the same applies. I've had NT4 (NT4 Installed first) and XP on the same PC with Ubuntu but never 98.

---

### Post by bodhi.zazen on 2007-09-06
> **garyed said:**
> I'm already dual booting Ubuntu Studio & XP with each on their own separate HD.
I want to add Windows 98 & triple boot but I'm not sure of the best way to do it.
My XP drive is formatted FAT32 all one partition.
1 - Would I be better using the XP drive or the Linux drive?
2 - Would I use gparted to partition the drive?
3  - Or would it be easier to use XP to dual boot with 98?
Any ideas

Umm ...

Not sure what the problems other have had, but it should be fairly straight forward.

First, I must ask why windows 98 ???

At any rate, I would use gparted from a live CD to resize your partitions. Does not matter where you install windows 98.

You will then need to re-install grub : [uwiki]RecoveringUbuntuAfterInstallingWindows[/uwiki]

Then you will need to edit grub to "map" and "hide" the windows partitions from each other.

See this link : [http://users.bigpond.net.au/hermanzone/p15.htm#Operating_system_Entries](http://users.bigpond.net.au/hermanzone/p15.htm#Operating_system_Entries)

Scroll down just a little to the windows sections.

As long as you read and understand what you will be doing it will all go well. If you do not read, well there can be a number of problems ...

Ask if you have questions after reading or get into trouble ...

---

### Post by bam1234567 on 2007-09-06
You know, i'm really not sure. (Again I hate Windows) You might want to google that, or find a guide on that.

---

### Post by wolfen69 on 2007-09-06
install virtualbox and run 98 there.

---

### Post by SpiritIsReality on 2007-09-06
howdy

I followed some of this, how to install and boot 145...
[http://www.justlinux.com/forum/showthread.php?t=147959](http://www.justlinux.com/forum/showthread.php?t=147959)
I boot 5 or so, changes
looking forward to virtualbox

trails

---

