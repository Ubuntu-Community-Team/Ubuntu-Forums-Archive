---
title: "Ubuntu Edgy Intel Core Duo iMac"
date: 2007-02-20
forum: Apple Intel Users
---

### Post by MilesmacMiles on 2007-02-20
Hi,

I have searched the forums and am of the belief that I have a (somewhat) unique problem. I have an Ubuntu Edgy Live CD, and am planning to install for triple booting. I am using the reFIT bootloader. I ALREADY had Windows installed (before I thought about linux) on top of my OSX installation and recently booted into linux (from my cd drive). I thought that the look and feel was beautiful and would like to get it running at the much faster speeds of running off of an External Harddrive.

The harddrive I have in mind is an 250 gb LaCie harddrive, which I partitioned already, to have a 60.00 gb (format free space) partition and 172.89 partitioned (format Mac OS X Extended Journaled). My question is this: After booting, the CD appears on the desktop, and says "Install" after double clicking this and following the steps, including giving the computer a name and setting my password and timezone, I arrived at the steps that led me through the partitioning.

I selected my external hard drive's partition, I knew it was the correct one because it said 60 gb. I then clicked "New" and formatted it so that Ubuntu would install there. I formatted it using the ext3 filesystem. The partition was titled /dev/sdb2.

The installer asked me where my mount points were, although I didnt fully understand this, I think it means the places where devices and hard drives are stored. As you can see in the first screenshot, I selected 60 gb for my / drive aka my entire linux hard drive and 200 megabytes for "Swap Space". My understanding of swap space is that if the amount of RAM available is too little to run the applications open, some of the backrounds applications will be taken out of RAM to allow other "Apps" to use more. 

I pretty much understand the top part of step 6, the part in which the Installer verifies your settings, (ie. Language, Name, Location), but got lost when the installer asked me where GRUB should be installed to. The default being hd0, I selected that on my first install attempt. It failed at 15% after the bar froze for a while. It was in the midst of creating the ext3 file system for my linux Hard Drive. The error message returned was:

 "The attempt to mount a file system with type swap in SCSI1 (0,1,0), partition #1 (sda) at none failed.

You may resume partitioning from the partitioning menu."

It gave me the option to Go Back or Continue. 
I have no idea what to do, and would be very much pleased if you shed some light on my case. 

Thanks,

Miles

---

### Post by flangemonkey on 2007-02-20
ok I will put my tuppenceworth in, I am a bit of a newbie, but I am getting there...

200MB is far too small for swap space, the guideline amount is twice the amount of RAM you have installed, up to about 2GB.

The mount points are (from a simplified Mac-like point of view) where you would like to put folders called /home, /mnt, etc.(you can spread them across several drives or even computers)

I would recommend having a 100MB /boot partition, although not entirely necessary, and for Ubunutu I'm not even sure if it is needed. The rest of the mount points (apart from swap) will be able to share the rest of the 57 or so GB left. (which I would now recommend as I gave each of my mount points a seperate HD partition and some lie empty and some are bursting at the seams... :/ )

The error 'partition #1 (sda) at none failed' if it is from the partition manager in the installer, I think you may struggle with installation, to the external drive, anyway.

hth

---

### Post by MilesmacMiles on 2007-02-20
Hmmmmm, thank you for your advice, how would I assign multiple mount points to a single drive? And also, I think I may succumb to my instincts and partition my INTERNAL drive...hmmmm....

Thanks, 
 
Miles

---

### Post by flangemonkey on 2007-02-22
multiple mount points:

for every Linux system (I have seen) you need many directories including /tmp /var /proc /home /usr, etc.

Mount points just point to where they are located, either "somewhere here on the HD" or "over there on that computer which seems to be on" and as far as I can tell, /boot has to be on the main internal drive. 

And not a RAID array, as I found to my dismay, well, more because I couldn't get the computer to believe it could boot :/, apparently you can be referencing /dev/mapper/<address to drive partiton> but it didn't work.

anyway, back on track, mounting can be used to mount .iso files or whole partitions using the form

mount <what> <where> [for files (.iso etc), you need a rough <how> on the end too] 

[See this page for exact instructions of how to mount an ISO image (command line style)]("http://www.techspot.com/vb/topic483.html")

hth,

Phill

---

### Post by MilesmacMiles on 2007-02-23
Thank You so much, Phil, this helps majorly. Now, I know exactly what to do. The only problem is this: When I try to boot into Ubuntu, it goes to the standard screen, and even when I boot off into Safe Graphics mode, once it stops loading, the screen messes up and goes all weird...it looks like its slanted sideways.
Im thinking this is because of my ATI video card...


Thank you, 
Miles

---

