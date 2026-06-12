---
title: "MacBookAir2,1 does not boot with Ubuntu 9.04 nor 8.10"
date: 2009-06-07
forum: Apple Hardware Users
---

### Post by fdimeglio on 2009-06-07
Hello,

I would like to install Ubuntu 9.04 or 8.10 on my MacBookAir2,1. 

I could quite easily to it with the first version of the MacBookAir (version 1,1) even if it was a bit slow.

With the latest version of the MacBookAir (2,1) this is another story.

After the initial Ubuntu boot screen and selection of my language and options, the install just purely hang with a black screen and then I have to even reset the SMC (via CTRL+OPTION+SHIFT + 5seconds POWER) to be able to have access to my external CD drive after the reboot.

Any person who was able to do this install ???

Thank you for your help,

Fabrice

---

### Post by fdimeglio on 2009-06-09
Does anybody have a response ?

Fabrice

---

### Post by atte on 2009-06-24
Press F6 at the boot menu and tick NOACPI, select the first option in the menu (try ubuntu) and delete splash and quiet.

I managed to install 9.04 with encrypted root partition but now I have a problem getting it to boot... will update this thread when I worked out what was wrong.

---

### Post by atte on 2009-06-25
Well, I am using rEFIt as boot manager and grub on the Ubuntu partition. When I use noacpi and apic=force I manage to boot about half of times (only tried 4 times yet).

So it is possible, just have to figure out how to make it work every time :-)

---

### Post by rileyporter on 2009-06-26
I have a macbookair 2,1 and I have got ubuntu to install.  I used the bootcamp option.  And now I hold ALT when booting and select "Windows" then it loads linux.  It is a bit buggy.. The first boot attempt didnt work.. but the 2nd seems to.. Weird..

---

### Post by cputoaster on 2009-07-15
FYI, works about half the times with grub64 too (see [http://ubuntuforums.org/showthread.php?t=995704](http://ubuntuforums.org/showthread.php?t=995704))

---

