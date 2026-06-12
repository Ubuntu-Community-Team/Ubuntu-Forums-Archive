---
title: "Partition question"
date: 2007-07-20
forum: Absolute Beginner Talk
---

### Post by BlastOButter42 on 2007-07-20
Newbie question:
The main partition on my laptop's hard drive is 33GB. I want to install Ubuntu on the computer, but I don't want to shrink my main partition too much, so the new partition won't be very big. My question: if need to later, will I be able to shrink my original partition more and expand Ubuntu's partition into that space?

Thanks,
Robert

---

### Post by overdrank on 2007-07-20
> **BlastOButter42 said:**
> Newbie question:
The main partition on my laptop's hard drive is 33GB. I want to install Ubuntu on the computer, but I don't want to shrink my main partition too much, so the new partition won't be very big. My question: if need to later, will I be able to shrink my original partition more and expand Ubuntu's partition into that space?

Thanks,
Robert

Hi and yes gparted should be able to but I would not go lower than 5gb for ubuntu depending on which version you are choosing. Be sure to backup and  defrag windows before doing installation or resizing. Have you tried the live cd on your system?

---

### Post by az on 2007-07-20
> **BlastOButter42 said:**
> Newbie question:
The main partition on my laptop's hard drive is 33GB. I want to install Ubuntu on the computer, but I don't want to shrink my main partition too much, so the new partition won't be very big. My question: if need to later, will I be able to shrink my original partition more and expand Ubuntu's partition into that space?

Thanks,
Robert

You would need to shrink your first partition down by a value equal or greater than your second partition.  The reason is that you will not be able to expand the partition in one step, but copy its beginning to the beginning of the free space (and it must fit - it cannot write onto itself)  Once it is copied (moved) you will then extend its ending to the end of the drive.

If you don't shrink your first partition down enough, you will not be able to move your second (ubuntu) partition out of the way to extend it...

---

### Post by Shazaam on 2007-07-20
Short answer= yes.
Better thing to do is download and burn a gpartedlivecd, set your pc to boot from the cd first and do your partitioning there. it is a very handy thing to have. While you are at it download and burn a SuperGrubDisk too. With that you can fix any problems that pop up with grub.
DO THIS FIRST before any partitioning--- start Windows in safe mode; uninstall any software you don't need; do a disk cleanup then defragment the drive. After you are done defragmenting do it one more time in safe mode. THEN you can safely play around with partitioning.
Depending on the Linux distro installed sizes range from 50 megs to around 7-8 gigs depending on what you install so Ubuntu or similar can live happily with a 10 to 20gig partition. Just be carefull loading up music and videos on that partition as it could fill up fast. If space is a problem and you have some spare cash go out and buy a bigger hard drive, clone your installed system to the new drive and go from there.

[http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)
[http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)       <---read this

---

### Post by HermanAB on 2007-07-20
Yes and no.  Freeing up more space and putting it to proper use later isn't so easy.  I recommend that you install Ubuntu with whatever room you can spare at the moment.  Then figure out how to use VMware server and once you can comfortably run Windows  on VMware on Linux, you can re-install the machine and give the whole disk to Linux and run Windows in a window on VMware on the odd ocation that you need it.  The advantage is that you don't need to reboot anymore - Linux and Windows applications can then run side by side.

Cheers,

Herman

---

