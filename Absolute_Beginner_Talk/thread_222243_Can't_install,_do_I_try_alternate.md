---
title: "Can't install, do I try alternate?"
date: 2006-07-23
forum: Absolute Beginner Talk
---

### Post by drifting on 2006-07-23
Hi Guys, some advice please.

Just built a new machine with the sole intention of running Ubuntu. Have been playing for a while with Ubuntu on a virtual PC, and fell in love with it.

Hardware.
MSI K9N Platinum, Athlon FX2 Dual core 2200 AM2,2GB ram, two HDD 80GB & 160GB Sata 2, Nvidia 7900GT. 

Created a bug report on Launchpad [Bug 53558] We're sorry; the installer crashed.

Have downloaded, standard i386, crash as above, also the AMD version, crash as above. Now I have just completed the download of the alternate install, is it worth trying? Reason I ask is that I installed XP just to confirm the Hardware was ok. And I really don't fancy re installing it again (40 Million SP's later)

Regards Paul.

---

### Post by mbrang00 on 2006-07-23
I had the same issue when i tried to install it on my machine...as obscure as it seems, it was the brand of dvd that i tried...


I burned it to a memorex dvd, did not work, could not get the installer to prompt, re burned another (memorex) same thing... took the same disk to my wifes computer..it was fine, ready to install... so i tried a burn to a dynex (best buy off brand)  worked like a charm...Ill tell you, i wouldnt have beleved it myself if it hadnt happend to me.


Just somthing to think about

---

### Post by lamego on 2006-07-23
matej,
First should have created a new thread, your question/problem has nothing to do with the current thread.

Booting from an external USB device is not trival, please give it a read:
[https://help.ubuntu.com/community/BootFromUSB](https://help.ubuntu.com/community/BootFromUSB)

---

### Post by steve.horsley on 2006-07-23
Yes, it is worth trying again with the alternate installer. I believe from reading this forum that it's more stable. 

You may get problems with grub configuration. I have seen several threads here where people have trouble with combined IDE and SATA configurations, so if you get grub problems, try removing one of the two drives.

---

### Post by drifting on 2006-07-23
Thanks for the suggestion, currently ghosting off the windows install to save time.
Think I may just wipe the second disk (Which I only use for Data) and try an install to that. Both of my HDD are SATA the only IDE are my DVDrom and DVD Burner, so may have a problem installing without them ;) 

Thanks Paul.

---

### Post by OU812 on 2006-07-24
Is the firmware on your drive(s) up-to-date?

john

---

### Post by drifting on 2006-07-24
> **OU812 said:**
> Is the firmware on your drive(s) up-to-date?

john

No idea John? they were fresh out of the package last week :D 

Will go take a look at the manuf's sites, hope to give it another go tonight.

Regards Paul.

---

### Post by drifting on 2006-07-26
Well good news, the alternate worked!!

Now the bad news the Network card does not! 

Will go have a troll of the forum I expect someone on here has an Nvidia inbuilt network card. Strange thing is it shows it in the hardware list, but it's just not getting an IP, must admit I had a few problems getting the dos driver for ghost to work with it as well.

Paul.

---

### Post by zoro on 2006-08-01
Well if you figure it out, let me know - I've been having the exact same problem and it's driving me insane :(

---

### Post by drifting on 2006-08-04
> **zoro said:**
> Well if you figure it out, let me know - I've been having the exact same problem and it's driving me insane :(

Well all I found was that you need to power off your machine, even go so far as to unplug it from the wall socket. Leave it for about 20 seconds and power it all back up. Mine then worked, like a few others on here I followed the instructions on another thread about disabling forcedeth? and installing the nv driver, but to be honest  forcedeth is still loading, and the card is still really iffy. So no sorry no solution as yet.

Paul.

---

### Post by zoro on 2006-08-08
Well to be honest, unplugging my pc for 20 seconds just so that my NIC **might** work doesn't sound so appealing :)
My only real alternative is to install a PCI NIC - and then I'd have *3* network ports on my PC. Seriously - is it really worth it?

I think I may just wait until my motherboard is supported by Ubuntu :(

---

### Post by Christmas on 2006-08-08
Yes go for the Alternate CD. The graphical installation is handled by Ubiquity which is new, as far as i heard it has some bugs.

---

### Post by zoro on 2006-08-08
There's an alternate CD now?

/me clueless :D

---

