---
title: "Installation trouble"
date: 2006-09-12
forum: Absolute Beginner Talk
---

### Post by DCM71 on 2006-09-12
OK, my appologies, I hope this hasn't been asked before (but probably has).

I downloaded the ISO for ubuntu yesterday, burnt the image to disk, that went fine, disk is good.  The computer it is going on boots from the CD, to the virtual desktop, everything is fine.

Double click on install ubuntu, I go through the options 1 through 5, page 6 to start the installation, and the system always seems to hang at around the 67% mark, even if I leave it a loooong time.  no error messages, it just sits there.

I realy want to try a Linux OS, as am fed up of XP, so please PLEASE, someone give me some pointers.

Thanks in advance.

---

### Post by confused57 on 2006-09-12
You might want to try installing with the Dapper alternate cd.  Here's an excellent guide:
[http://users.bigpond.net.au/hermanzone/index.htm](http://users.bigpond.net.au/hermanzone/index.htm)

---

### Post by DCM71 on 2006-09-12
But I am not wanting a Dual Boot, the comp I am installing ubuntu will be purely for ubuntu, no Windows on it at all.  I have waited a long time to get a spare comp running to try Linux based OS.

---

### Post by skymt on 2006-09-12
It sounds like a bad burn to me. I've had the same problem in the past (around 45% for me), and it was solved by burning another copy.

If a second burn doesn't do the trick, use the alternate CD. It often works better. Keep in mind, the graphical installer is pretty much brand new.

---

### Post by dbd on 2006-09-12
Does it say what it is doing at 67%? If it is not a bad burn then that may give us a clue of the cause of problem.

---

### Post by bodhi.zazen on 2006-09-12
> **DCM71 said:**
> But I am not wanting a Dual Boot, the comp I am installing ubuntu will be purely for ubuntu, no Windows on it at all.  I have waited a long time to get a spare comp running to try Linux based OS.

As you said the CD burned without error, I second the advice to use the "alternate CD".

If you do not want Windows, when partitioning select "use entire disk". 8-)

---

### Post by DCM71 on 2006-09-12
OK, well I will go burn another disk and give it a go, or might just try the suse linux iso that came on a cover disk.

As for what it is doing, there is nothing except the virtual desktop that it boots to from the CD, a progress bar and thats it.

I have also chosen the whole disk route for the install.

---

### Post by DCM71 on 2006-09-13
Hi, thanks for all the help, it is installed now, this is what I did.

I booted from the original image, then went to system>admin>Partition Manager (is it Gimp?) and deleted ALL the partition info in there that ubuntu had put, and it went fine.

---

### Post by reubano on 2006-09-26
I was having a similar problem and fixed it by doing the following...


System > Administration > Gnome Partition Manager
on each partition that had a lock by it > right click > unmount (or deactivate)

then 

System > Administration > Disks
select the hd you are installing to, click partitions, and for each partition click 'enable'

restart (may not be needed but this is what I did)
install from live CD 

below is the system I now have:

ASUS-a8n-sli deluxe
WD 250GB SATA HD
dual boot with win2000 and ubuntu dapper drake

---

