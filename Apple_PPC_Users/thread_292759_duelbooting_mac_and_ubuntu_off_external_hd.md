---
title: "duelbooting mac and ubuntu off external hd"
date: 2006-11-04
forum: Apple PPC Users
---

### Post by tbluhp on 2006-11-04
I want to duelboot my mac os x and ubuntu from my external firewire hard drive how?

also what are the offical partions I need in order to make everything work?

---

### Post by linear on 2006-11-05
Read these; it requires a bit of work:
 
[http://www.ubuntuforums.org/showthread.php?t=84131](http://www.ubuntuforums.org/showthread.php?t=84131)
[http://www.ubuntuforums.org/showthread.php?t=40536](http://www.ubuntuforums.org/showthread.php?t=40536)
[http://www.ubuntuforums.org/showthread.php?t=91755](http://www.ubuntuforums.org/showthread.php?t=91755)
[http://www.ubuntuforums.org/showthread.php?t=89990](http://www.ubuntuforums.org/showthread.php?t=89990)
 		[IMG]http://ubuntuforums.org/images/misc/progress.gif[/IMG] 	 		 		 		 		 		 	 		 			 			 				 				[[IMG]http://ubuntuforums.org/images/buttons/edit.gif[/IMG]]("http://www.ubuntuforums.org/editpost.php?do=editpost&p=898083")

---

### Post by Kalvin on 2006-11-05
I think I lucked out because my install "just worked" when I attempted it today.

I installed Kubuntu Edgy via the Alternate Install CD.  I had partitioned my External FW drive with OSX - part HFS+ and part Free Space.

In the partition editor during the install I created an 8.5MB "NewWorld Boot Partition" named "NewWorld" at the beginning of the free space. This needs to be bootable (defaults when you select NewWorld).

Then I created my linux-swap partion.  Finally, the ext3 partition for the install.

It may be worth noting that I installed a second copy of OSX on that external HD earlier today. It was blown away when I reformatted it but I had booted to OSX from the External already.  I don't know if this makes a difference.

That's about the extent of my knowledge, if it doesn't work give the above links a shot!

Good Luck!

---

### Post by linear on 2006-11-06
Could this mean firewire booting is fixed in Edgy?

---

### Post by Kalvin on 2006-11-06
It appears so...

You do need to use the Alternate Install CD though, because the Graphical Installer cannot create the NewWorld boot partition and won't let you continue if the partition isn't on your drive.

I'd like to hear if anyone else has had the same success as I did. After reading some of the other stories I was expecting to attempt a boot and watch it fail spectacularly. ;)

---

### Post by linear on 2006-11-06
This may be it: [https://launchpad.net/distros/ubuntu/+source/initramfs-tools/+bug/37479](https://launchpad.net/distros/ubuntu/+source/initramfs-tools/+bug/37479)

---

### Post by pawright24@mac.com on 2006-11-07
Kalvin,
I downloaded the alternate CD for Edgy.  
When I partitioned I used manual partition and let the installer use the space for root and swap and I assume it uses the New World boot in the space alloted to Apple.

When I started on with the installation, however, it reported many files corrupted, such as aptitude.

Did I do something wrong?

I am installing on an external firewire drive with 120GB of room.
I have my Mac OS X on an internal drive.

I can use Disk Utility to partition ahead of installation, if that is advisable.
If so, what partitions and what size?

The "alternate" installer did see all of the disks and their partitions.

Any help will be much appreciated.

Paul Wright

---

### Post by pawright24@mac.com on 2006-11-07
Kalvin,
I downloaded the alternate CD for Edgy. 
When I partitioned I used manual partition and let the installer use the space for root and swap and I assume it uses the New World boot in the space alloted to Apple.

When I started on with the installation, however, it reported many files corrupted, such as aptitude.

Did I do something wrong?

I am installing on an external firewire drive with 120GB of room.
I have my Mac OS X on an internal drive.

I can use Disk Utility to partition ahead of installation, if that is advisable.
If so, what partitions and what size?

The "alternate" installer did see all of the disks and their partitions.

Any help will be much appreciated.

Paul Wright

---

### Post by izahn on 2006-11-07
I was excited when I read that you were able to install to an external HD as this is something I've wanted to do for a long time. Unfortunately, it doesn't seem to work for me. I followed your example and created three partitions on my firewire HD (using the alternative install cd), one new world boot, one ext3, and swap space. Install goes fine until the end, then yaboot fails to install, can't boot from the external drive. I'm trying to figure out if you did something different than I did, or what. Any thoughts?

---

### Post by Kalvin on 2006-11-08
I'm not sure about all of this as I'm still fairly new to linux and this was my first PPC install...but here it goes:

I'm using a 160GB FW Drive that I formatted in Disk Utility to have a 35GB HFS+ partition and the remainder I left as free space.

As I mentioned, I used the Alternate CD to add a NewWorld partition (named "NewWorld" in fact) of 8.5MB.  Then I created a 2GB Linux-Swap partition.  Finally, I created a 30GB ext3 partition.  Note that there is still free space on the drive!  I don't know if this makes the difference, but I've heard that Apple's booting process needs a small partition or some free space at the end of the drive.

Again, I also installed OSX onto the drive prior to trying this and it booted fine.  After that is when I formatted in disk utility above.

Definately give a shot to using Disk Utility before trying the install.  Not sure that was the key but it's a good start.

-Kalvin

---

