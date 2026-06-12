---
title: "Master and Slave HD Ubuntu"
date: 2006-10-11
forum: Absolute Beginner Talk
---

### Post by deadgobby on 2006-10-11
Allo,
 I have WD 80 gig HD and that is now Master and fresh installed 6.06 lts on it. The old HD a WD 40 gig has dapper on it as well and the slave drive. Every then looks good in bios. Now how can I get the information off the slave to master? Most threads I have read is for dual boot with different o/s. 
Thanks
Gobby

---

### Post by PriceChild on 2006-10-11
Well you can reinstall/configure grub to allow booting of the second dapper still...

And as for mounting to read/write data... that's still fine.

Could you be more specific as to which you are after?

---

### Post by deadgobby on 2006-10-11
I want to grab saved files and such from the old HD to new. Basic transfer of data. I think or I recalled reading you can get Ubie to read off the secound HD.
GObby

---

### Post by Quintin Riis on 2006-10-11
IDE devices are configured thusly in Linux:

Primary   IDE device 0: /dev/hda
Primary   IDE device 1: /dev/hdb
Secondary IDE device 0: /dev/hdc
Secondary IDE device 1: /dev/hdd

Next is partitions.  1st partition of hda is /dev/hda1.  Third partition of hdd is /dev/hdd3.

Before you can access a filesystem it has to be 'mounted'.  Type 'mount' in a terminal to see what filesystems are currently mounted.  To view partitions on disk you can use 'sudo cfdisk /dev/hdx' where x is the drive you want to look at.  Note there is probably another way to do this, but that's what I'd do.  Look around and find where your partitions are located, cfdisk will give you the device and partition number.

Now you need to make an empty directory to mount the other partition in.  'mkdir ~/old_disk' or such.  Then you need to mount the old drive.  'sudo mount -o rw /dev/hdxx /home/myhome/old_disk'.

Hope this helps.  Please follow-up your post with the resolution.

---

### Post by deadgobby on 2006-10-11
Sure I'll do that. Be about a 1/2 hour. Got to do stuff. Like feed the kids. :D 
GObby

---

### Post by PriceChild on 2006-10-11
If all you want to do is mount then check out: [http://psychocats.net/ubuntu/mountlinux](http://psychocats.net/ubuntu/mountlinux)

---

### Post by deadgobby on 2006-10-12
Well I followed cats link to a T and haven problems mounting the slave. It is there and gparted sees it. But I am going to go a different route. Burn all my save files to CD, I think I can save all my FF bookmarks to CD too. The bookmarks and mp3's is the main thing. On my 160 gig I got every thing up and running. Like Easy Ubie, Automatix, and Jack. I tied to mirror the HD, but came to a stop too. Soooooooooo Go the long route sort of speaking. 
 I had to reload gnome on the old HD after I found that Gnome-sound was broken. Fixed it and would not boot to Gnome after that. At least I know some linux or I may have been hosed.
Gobby

---

### Post by Quintin Riis on 2006-10-12
I don't understand why you don't mount the drive and copy the files?

---

### Post by deadgobby on 2006-10-12
THE DRIVE WILL NOT MOUNT!!!!! Been and over and over and did every thing to the letter T. It is ok through. I ended up hosing the O/S system when I tried up dating to eft on the old HD afer I saved every thing. So it hosed. I like my bigger HD any ways and do not mind reloading. Eh pratice pratice.
Off to work I goooooo
Gobby

---

### Post by Quintin Riis on 2006-10-13
There is no reason that it shouldn't mount.

Possibilities: 
bad disk controller (10%) 
jumpers in wrong spot (15%)
user error (75%)

If you want further help please let me know what you see when you look at cfdisk and how you have tried to mount the disk.

[SIZE="1"]As an aside: Typing in all caps is generally considered yelling or FLAMING on the internet.  Use sparingly!  :)[/SIZE]

---

### Post by deadgobby on 2006-10-13
> **Quintin Riis said:**
> There is no reason that it shouldn't mount.

Possibilities: 
bad disk controller (10%) 
jumpers in wrong spot (15%)
user error (75%)

If you want further help please let me know what you see when you look at cfdisk and how you have tried to mount the disk.

[SIZE="1"]As an aside: Typing in all caps is generally considered yelling or FLAMING on the internet.  Use sparingly!  :)[/SIZE]
 Jumpers in the right spot.
No bad disk controller
No User Error
 Turns out to be that the HD cable was bad. Change cable out to mother board. Got the hard drive to mount....

---

### Post by Quintin Riis on 2006-10-13
:-D

One of the first things to check.  I got a PII for free recently that was "not working" and "randomly rebooting".

Similar issue.  It would work OK with one device on each channel, but with two it crapped out.  Once I'd isolated it and done a burnin on the CPU and HDD for two days I set it up as a file server for a client.

---

### Post by deadgobby on 2006-10-14
ya tell me about it. I should of done it the kiss way. Keep it simple stupid.

Gobby

---

