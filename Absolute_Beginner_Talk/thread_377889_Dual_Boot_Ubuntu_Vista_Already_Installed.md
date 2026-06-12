---
title: "Dual Boot Ubuntu Vista Already Installed"
date: 2007-03-06
forum: Absolute Beginner Talk
---

### Post by tm0054 on 2007-03-06
Here is another dual-booting question:

I would love to dual boot Ubuntu with my already existing install of Vista.

Here is my situation:

Vista is already installed on my laptop and I don't have an installation disc so if anything goes wrong it could fry my Vista install and I'd have no way of reinstalling it from scratch. I do have the ability to create factory install and saved state discs, but I'm afraid that they won't work if my partitions get messed with. Maybe the Factory Install would install Vista from scratch? I have an Acer Aspire 5610-4357. I'd create the Factory discs using their e-Backup software (I know it's e-something).

My hard drive is already partitioned into two equally sized parts (at about 52 GB) - one for the OS and one 'Data' drive.

Is there a safe and easy way to create a dual-boot system under these circumstances? As much as I love Ubuntu I need to keep my install of Vista.

---

### Post by mikewhatever on 2007-03-06
If there is absolutely no way to recover your Vista, I would not try installing Ubuntu. Theoretically, the data partition can be resized though. 

Why did you buy a PC with Vista, if you wanted to try Ubuntu? How come you have no recovery DVDs or similar? Don't you know that MS does that kind of stuff? Don't you know how they 'killed' Netscape with IE6?

---

### Post by PurplePenguin on 2007-03-06
Why didn't you receive an install disc?  Hopefully for you, Vista doesn't suffer from the typical need to reinstall Windows every 6 or 8 months...

---

### Post by Ambimom on 2007-03-06
Why not run Parallels (not sure if VMWare is Vista ready yet)?  It will give you both operating systems provided you have enough RAM on your laptop; and since the Ubuntu will just be a file on your Vista hard drive, you can burn a copy of it to a CD or DVD (or copy to an external drive).  That way even if you have to reformat your Vista, you will have your Ubuntu installation intact.

I've tried both virtual and dual boot and each has its advantages and disadvantages.

All in all, I love having the use of both operating systems at the same time and not having to reboot from one to the other all the time.  Without Microsoft restore disks, restoring the master boot record would be rather difficult.

---

### Post by watson540 on 2007-03-06
Very amusing because I just bought a laptop, heh. It came from hp ALSO with no recovery cd/dvd media. They want you to make your own recovery media, here is the funny part though. I went to backup the preinstalled xp mce with all of their ad and bload. It said something like 14 cds to friggin back it up!!. keep that shizzle. In any case your recovery stuff is on a WHOLE seperate partition so all you have to do is resize the partition that vista is on. you're not going to screw anytihng up unless you're plain dumb and decide to format the whole hard drive instead of just resizing the existing one and throwing ubuntu on it. nothing to worry about

---

### Post by ssican on 2007-03-07
tm0054,  See is how to: HOW TO DUAL-BOOT VISTA WITH LINUX (UBUNTU) (VISTA INSTALLED FIRST): [http://apcmag.com/5046/how_to_dual_boot_vista_with_linux_vista_installed_first](http://apcmag.com/5046/how_to_dual_boot_vista_with_linux_vista_installed_first)

---

### Post by Detonate on 2007-03-07
Shipping new computers without the disks for the OS has become very common in the industry.  You are expected to make your own disks, and the new computer comes with a program on it to help you do this.  In my experience, I have been called on to help repair broken systems several times that the owner did not do this, and it certainly complicates my helping them.

Go ahead and make your recovery disks.  I have no experience yet with Vista, but I would think that if you install Ubuntu and it somehow messes up your Vista install, you would be able to reinstall Vista from those disks.  Be sure and backup any files you have first.

If this were a desktop, I would say purchase a separate hard drive for your Ubuntu if you are really apprehensive about messing up the Vista install.

---

### Post by tm0054 on 2007-03-07
Thanks for all the help!

I managed to successfully get the dual boot working last night. Using Vista's drive management I simply shrunk my data partition by 20 gigs leaving 20 gigs of unallocated space. Then I loaded the Ubuntu CD and chose the 'Install to the largest continuous space' option for the location of the install. I updated the menu.lst file in /boot/grub/ and now it'll load either OS- and my Vista partitions are completly in tact! Now I just need to get Ubuntu working with my wireless connection and it will probably be my primary OS!

---

