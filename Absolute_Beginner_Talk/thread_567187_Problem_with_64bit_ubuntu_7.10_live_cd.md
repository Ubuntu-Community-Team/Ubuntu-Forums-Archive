---
title: "Problem with 64bit ubuntu 7.10 live cd"
date: 2007-10-04
forum: Absolute Beginner Talk
---

### Post by kishe on 2007-10-04
I got Intel core2duo e6430 processor. Every time I try to load the Ubuntu 7.10 64bit CD and select install, my screen goes black and computer reboots itself like 60 seconds later.

I thought all core2duos were 64bit compatible?

---

### Post by nowshining on 2007-10-05
have u tried creating a report on bugs.launchpad.net yes u'll have to register, and reporting this bug, Gutsy is still in Beta so best to report now. Also did you try a reburn, memtest, test of the CD at boot time, etc.. Did you burn also at a slow speed? If you ordered the CDs then do the tests, etc.. to check out the CD and memory of the computer.

---

### Post by kishe on 2007-10-05
> **nowshining said:**
> have u tried creating a report on bugs.launchpad.net yes u'll have to register, and reporting this bug, Gutsy is still in Beta so best to report now. Also did you try a reburn, memtest, test of the CD at boot time, etc.. Did you burn also at a slow speed? If you ordered the CDs then do the tests, etc.. to check out the CD and memory of the computer.

I burned it on two different CDs, one cd-rw and another cd-r, I also used two different burning software. None, memtest, test of the cd or anything works past Grub because it wont load the kernel (my guess is that the livecd kernel doesnt have support for Intel CPUs turned on)

Writing bug report as we speak :)

---

### Post by nowshining on 2007-10-05
oops in my last post I said ordered.. :P u can't order them now lolz.. and good to know..

---

### Post by RomeReactor on 2007-10-05
Hi. kishe, how much RAM does your system have?

---

### Post by kishe on 2007-10-05
> **RomeReactor said:**
> Hi. kishe, how much RAM does your system have?

2gb DDR2 800mhz

---

### Post by nowshining on 2007-10-05
I myself figured out u prob. had enough ram due to the fact ur computer uses a 64-bit processor :D...

---

### Post by kishe on 2007-10-05
I tested 32bit gutsy CD and it gave somesort of ata_300 error and left me in to initramfs console.

i got no pata hardware on my computer, only sata.

---

### Post by nowshining on 2007-10-05
maybe another error to report to launchpad I think.

---

### Post by kishe on 2007-10-09
solved!

apparently abit ib9 motherboard has two different sata chips and newest kernel doesnt like the other one.

---

### Post by RomeReactor on 2007-10-09
So you got Ubuntu working on it? 

Congratulations! :popcorn:

---

