---
title: "Dual-Boot Question"
date: 2007-04-04
forum: Absolute Beginner Talk
---

### Post by tbdbitlnumber1fan on 2007-04-04
Sorry if I sound like a noob, but if you dual-boot Windows XP with Ubuntu 6.10 does it delete any files on Windows XP.

---

### Post by oilchangeguy on 2007-04-04
no

---

### Post by tbdbitlnumber1fan on 2007-04-04
thanks

---

### Post by mikeyphi on 2007-04-04
> **tbdbitlnumber1fan said:**
> Sorry if I sound like a noob, but if you dual-boot Windows XP with Ubuntu 6.10 does it delete any files on Windows XP.

No - assuming you didn't/don't take the option of using the whole disk during the install process. If you choose to allow the installer to repartition your disk and only use free space, you will have both OSs and a menu screen at bootup allowing a choice of OS to use!

---

### Post by Maestro23 on 2007-04-04
> **tbdbitlnumber1fan said:**
> Sorry if I sound like a noob, but if you dual-boot Windows XP with Ubuntu 6.10 does it delete any files on Windows XP.

No, you install Ubuntu into its own partition(s) ( "/"=root, /home and swap).  You will want to do a "manual" partition when it comes to installing it.  


Good read on partitioning: [http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

---

### Post by metzy85 on 2007-04-04
ok i have roughly his same question but a little more wut should i put in for my root file system

---

### Post by sammyd253 on 2007-04-04
From what I've been hearing, Ubuntu only needs about 3GB to install, and all of these files will go to the root.  However, you want to give this partition some breathing room.  It wouldn't be a bad idea to give your root partition around 10GB or so.  Then you take the rest of your space and dedicate that to your /home partition. (This is where you can keep all of your personal files, preserving them in case you need to upgrade/reinstall Ubuntu)

Also be sure to account for your /swap partition.  Make this double the amount of system memory you have in your system.  (If you have 2GB of memory, make your /swap partition 4096MB)

Hope this helps!

---

### Post by metzy85 on 2007-04-04
I AM SO LOST NOW :( 
ok i am at the preparing to mount pionts screen in the instilation i have alreayd partiioned me hardrive right and it is asking me for root file system and i have no idea wut that is and wut exactly is a swap drive my partion for me linux is 14 gb do i need a swap drive

---

### Post by Pisi-Deff on 2007-04-04
> **sammyd253 said:**
> Make this double the amount of system memory you have in your system.  (If you have 2GB of memory, make your /swap partition 4096MB)
Actually, if he has that much RAM it's pointless to use that much space for swap.
It would never be actually used fully. A 2048MB swap (or less) would be more useful.

Edit:// A swap partition is like a pagefile for windows. And yes, you need it (well, probably not if you got 16GB RAM tho).

---

### Post by oilchangeguy on 2007-04-04
i agree. if your computer needs to use swap/virtual memory, then it's got problems.

---

### Post by sammyd253 on 2007-04-04
Alright, let me try and break this down.

As stated before you need 3 partitions to successfully install Ubuntu.  They are:

/           - This is the root partition, and it is typically formatted using the ext3 file system.

/home   - This is the home partition.  This is where your personal settings will be stored, such as bookmarks, pictures, music, etc.  I believe this partition is typically formatted in the ext 3 file system as well.

/swap    -  This is your swap partition.  This partition is here in case your RAM becomes full.  Typically you make it double the size of your current system memory.  For example, I have 2GB of memory installed in my computer.  Therefore I would make the size of my /swap partition 4GB, or 4096MB.  This file system is formatted as a Linux Swap partition.

So to sum up the answer to your question, your root file system will be ext 3.  You DO need a swap partition as well.  The swap file system will be Linux swap, and make the size of this partition double the amount of your system memory.

*edit* - Listen to the other guys, you really don't need 4GB for your swap.  That's my mistake.  I only wrote that because that is the "typical" way of doing it.  However, 2GB these days will rarely fill, unless of course you're using a heavy application (or many) that need the memory.

---

### Post by metzy85 on 2007-04-04
that is the partion of the hardrive sy and i have 512 ram and can i install a swap after i have installed the linux

---

### Post by metzy85 on 2007-04-04
ok now i am losted more i got it installed and i have all these drives i have my primary hard drive i have dell uility drive i have this 3.3gb one i think is for my restore and i have my hda2 and hda4 how can i get this more organized two like three the restore one my primary and one for my linux



and wut does unmount volume mean

---

### Post by metzy85 on 2007-04-04
[http://i149.photobucket.com/albums/s43/metzy85/Screenshot.png](http://i149.photobucket.com/albums/s43/metzy85/Screenshot.png) 


[http://i149.photobucket.com/albums/s43/metzy85/Screenshot-DisksManager.png](http://i149.photobucket.com/albums/s43/metzy85/Screenshot-DisksManager.png)



[http://i149.photobucket.com/albums/s43/metzy85/Screenshot-Computer-FileBrowser.png](http://i149.photobucket.com/albums/s43/metzy85/Screenshot-Computer-FileBrowser.png)
these are some screen shota of my comps status

---

### Post by sammyd253 on 2007-04-04
I'm having a really difficult time understanding your posts.  If I were you, I would start from scratch again and take a look at that partitioning web site that was posted in this thread a little while ago.  With some concentration, I'm sure you can figure it out.  If you can't, then you have much more research to do about partitioning and file systems, and I wouldn't recommend trying to setup Ubuntu manually unless you know.  

As for what unmounting volume means... you're basically stopping the OS (Ubuntu) from communicating with a particular hard drive/removable drive/optical drive.

Example:
I put in my USB flash drive and it mounts as an E: drive.  When I select unmount volume on my USB flash drive it will no longer be accessed by Ubuntu.  Make sense?

---

### Post by metzy85 on 2007-04-04
says it is unable to unmount the drives i want to stop it from talking to

---

### Post by sammyd253 on 2007-04-04
Are these drives in use?

If you are viewing contents from the drive you are trying to unmount, Ubuntu may not let you unmount the drive.

If you have a file open that resides on the drive you are trying to unmount, Ubuntu will not let you unmount it.

If any scans or processes are accessing this drive, even in the background, Ubuntu will not let you unmount it.

If you are unsure of any access to or from the drive, restart your computer and then try to unmount the desired drive.  This should work.  If not, then you might have to make some modifications.

---

