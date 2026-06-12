---
title: "Installing on and booting from usb hd"
date: 2006-09-16
forum: Absolute Beginner Talk
---

### Post by dcahill on 2006-09-16
Hi,

I have been unsuccessfully trying to install Ubuntu 6.06.1 Desktop on an 80 GB usb Samrtdisk connected to a Thinkpad T43 (I do not want to modify the internal HD).

The graphical installer starts and says that its "Creating a file system for  / in partition #1 of SCSI3 (0,0,0) sdb" and then starts "Installing the System". It reaches 15% and waits there for a long time finally indicting that it "Failed to create a file system". I clik ok on the warning message and it starts the partitioner again and hangs at 5%. 

I looked at the disk with GParted and it shows three partitions:

/dev/sdb1 ext2 73.13 GB 1.27 GB boot
/dev/sdb2 extended 1.43 GB
/dev/sdb5 linux-swap 1.43 GB

I can only see a lost and found directory on that disk.

The CD is ok, I checked it. Aslo using the Alternate CD exactly the same happens.

Can Ubuntu be installed and booted from a USB drive or should I look somewhere else?

Regards,
Dennis.

---

### Post by daller on 2006-09-16
Why don't you backup the internal HD to the USB HD, and then install Ubuntu to the internal HD?

---

### Post by mixmaster on 2006-09-16
> **dcahill said:**
> 
Can Ubuntu be installed and booted from a USB drive or should I look somewhere else?

Regards,
Dennis.
I have it installed on and booting from a 1Gb USB memory stick so it must be possible to do it from a USB hard disk.

For the memory stick, I had to jump through a few hoops.  I basically created a 700Mb FAT32 boot partition and populated it with a hacked version of the live CD.  

This thread shows how it was done on Breezy.  I can't believe Dapper is that different
[http://ubuntuforums.org/showthread.php?t=80811](http://ubuntuforums.org/showthread.php?t=80811)

---

### Post by azimuth on 2006-09-16
"Can Ubuntu be installed and booted from a USB drive or should I look somewhere else?"


Dennis, I am running Ubuntu on a USB drive. I preformated two partitions on the drive for use with XP (data only) and left 32GB unformated. The Live CD found my unformated section and installed without a hitch. I know it can work, you may have to tickle some things on your setup. This was my first Linux install of any kind and I went with the outboard drive because I didn't know what I was getting into :D 

If my install would have went sour, I'd have oped for a couple of beers and tryed it tommorow.

---

### Post by dcahill on 2006-09-17
Thanks for the replies!

My experiments with Linux have been somewhat frustrating. I started out about a month back with Knoppix live CD and I realized then that I would need an HD install. Ubuntu looks like the best choice for that but installing to a usb drive as I need does not seem to be that simple. I guess it would be much easier to install on the internal HD but it’s a company laptop and I’m not allowed to play with it!

My first try was to follow the procedure for Breezy but can’t get past Step 2. I’ll try today with a small NTFS partition for XP and the rest unformatted and see what happens. 

Regards,
Dennis.

---

### Post by dcahill on 2006-09-17
Azimuth!

It worked, thank you!

I created a small NTFS partition on the usb drive and ran install without any problems at all. Now I can boot into Ubuntu form the usb drive.

Regards,
Dennis.

---

### Post by retep57 on 2006-09-17
yes i had that funny 15%  thing as well, i did the  ntfs  partition thing an  still not work
 i had to resize the partition a  bit fiddly but the 606lts disk let me do that ,  funny  the 1st time it tried to put the instalation on a 2gb partition on my new external 60gb  hdd,, hmmm sorted now though, i have run a bunch of things, even did a work unit for boinc  wcg etc,  maybe the install routine needs some fine tuning, prob not many have tried to boot from external hdd, glad we have   got it running now  :) cheers

---

### Post by cotcot on 2006-09-17
Installing on pendrive is possible according to the wiki in my signature.
For partitioning I have the best expoerience with the GParted LiveCD.

---

