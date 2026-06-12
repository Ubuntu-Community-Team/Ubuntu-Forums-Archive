---
title: "Still not clear to me: How to partition my Mac HD ???"
date: 2006-07-24
forum: Apple PPC Users
---

### Post by BlueBuntu on 2006-07-24
Hi all,

As walked through the forum, it's still not clear to me how to partition the Mac harddrive :confused: 

What is the software you actually used in partitioning your Mac HD ?

Was that something like "Parted" or "Gparted", or "iPartiton" ???

Please share your success stoty ;) 

P.S. my Mac is PB G4 12 inch with 80 G HD.

Thanks in advance,

Alez.

---

### Post by linear on 2006-07-24
There is a thread [here]("http://ubuntuforums.org/showthread.php?t=89960") that describes use of parted.
 
I went a different route: backed up up the hard disk, used Apple Disk Utility to partition (destructively), then restored OS X and finally installed Ubuntu.

---

### Post by BlueBuntu on 2006-07-24
Thanks linear,

Hmmmmm, for what you did, what is the "partition (destructively) :confused:

---

### Post by gThree on 2006-07-24
Destructively = Apple's Disk Utility wipes the drive first and then partitions it.  Old data ceases to be.

I've used it to partition a new drive and to erase/partition an old one.  No problems.

I've used GParted to erase an existing partition so I could reinstall.  No problem.

Best of luck ...

---

### Post by Nels on 2006-07-24
A couple weeks ago I tried out Ubunto on a PowerBook G4 OSX10.4.6. After using the the live CD I decided to install it on the machine as a dual boot. The way I did it, after many various attempts that didn't work, was to clone Tiger to an external HD, boot up using the new clone and through Disk Utility repartition the PowerBook's hard drive, erasing and overwriting it with zeros in the process. In Disk Utility I chose the two partition scheme, in my case 70G for OSX and 10g for Ubuntu. The 70G space I formatted as Mac OS Extended (journaled), while for the 10G partition it was imperative to select the create "Free Space" option. Without using the create "Free Space" option the installer will not be able to complete its function, and this way, using the live CD and choosing to allow the installer to create needed partitions, the Ubuntu installer will divide up the "Free Space" as it sees appropriate (in my case it created a nominal 500MB swap space and the remainder as a second partition for Ubuntu OS). 
I then recloned OSX back to the PowerBook, booted to that, inserted the live CD, shut down. Holding the option key as I started up, I selected the live CD when the boot option window came up. Once the desktop loaded I hit the install icon and walked through the six steps, step five being the one where you select the "Free Space" partition and allow the installer to repartition it.
All said everything on the PowerBook worked straight off excepting the Broadcom WiFi card with WPA. I still haven't been able to sort that out as I am such a newbie, though I can connect to the internet quite easily using an ethernet cable.
If you'd like you can look at this link that traces my installation saga: [http://ubuntuforums.org/showthread.php?t=209392&highlight=nels](http://ubuntuforums.org/showthread.php?t=209392&highlight=nels)
All the best!

---

### Post by BlueBuntu on 2006-07-26
Thanks a lot for a great information, Nels. That gave me another way to deal with the dual-boot stuff. :KS ,

Alez. :---) :^o =P~

---

### Post by MoonWyrd on 2006-07-31
I just tried Nels' instructions, but when I got to the point of choosing a partition to install ubuntu onto it would only give me the option of using the entire disk.   I tried both Dapper and Breezy.  Neither seemed to recognize
the existing partition for OS X or the free space I'd set aside for ubuntu.

One thing, I'm not positive I had Disk Utilities zero out the disk.  Is that
absolutely critical?

---

### Post by avtolle on 2006-07-31
I don't know; here is an alternative (but very similar) thread to Nels' dealing with partitioning/dual booting: [http://www.ubuntuforums.org/showthread.php?t=195414&highlight=Partition+OSX+Ubuntu](http://www.ubuntuforums.org/showthread.php?t=195414&highlight=Partition+OSX+Ubuntu)

---

