---
title: "HE:P! Screwed something up and can't reinstall"
date: 2007-06-04
forum: Absolute Beginner Talk
---

### Post by AlucardOni on 2007-06-04
Ok, to make a long story short I decided this last weekend to load ubuntu and vista on my home built and dual boot, I installed 7.04 on a 114gb partition and gave it a 512mb swap file and gave the rest of the 250gb drive to vista ultimate.

I was sadly unaware of the fact that Vista kills Grub.

After extensive searching I found a way to bring Grub back and add vista to the menu.lst file for dual boot and did so.

Sadly Ubuntu would now not load due to an error, in a panic I booted from the live-cd and went to fix my mistake, no go due to not being able to access my file system.

Attempted reinstall of 7.04 but got messg of "The attempt to mount a file system with type ext3 in scsi2 (0,0,0) partition #1 at / failed.  You may resume partitioning from the partitioning menu." during partitions formatting (only gets to 5%).

I then attempted to load Vista and that setup failed at start as well.

I am now deciding to abandon the dual boot and just run Ubuntu 7.04 using the guided method but am still recieving the same error.

Anyone?

Thanks,

Alucardus

---

### Post by blue_shift on 2007-06-04
If your MBR's got ugly I suppose you could format the whole disk, but I've not got a more technical solution. Someone else may have a more elegant solution.

---

### Post by AlucardOni on 2007-06-04
I've tried to repartition the whole drive and format the whole drive several times and I still get the same error on install.

-Alucardus

---

### Post by lsalminen on 2007-06-04
You could try using the Gparted live CD...that might let you format it better.

---

### Post by AlucardOni on 2007-06-04
I used the Gparted app on the 7.04 live CD to do several formats, are you talking about something seperate than that, like an Fdisk CD or something of that nature.

-alucardus

---

### Post by Dougie187 on 2007-06-04
I know there is a way to add ubuntu into window's chain loader.
 Just for future reference (from experience) I know that if you want vista and ubuntu to dual boot, it works best if you install your vista first and your ubuntu second. Then if you have to reinstall windows you would have to reinstall your ubuntu (or at least reinstall grub). One other thing you can check out is the super grub disk.

I will check and see if i can get you some links to info.

EDIT:
Here are some links that might help
[http://apcmag.com/5045/how_to_dual_boot_vista_with_linux](http://apcmag.com/5045/how_to_dual_boot_vista_with_linux)
[http://freshmeat.net/projects/supergrub/](http://freshmeat.net/projects/supergrub/)

Let me know if you need anymore help.

For the first link, focus on the ***Reinstall GRUB*** section

---

### Post by AlucardOni on 2007-06-04
Dougie187 thank you so much for those links, they will definetly help if I try and set up the dual boot again.

Only one problem though, there is no OS on the HDD anymore, its been formated numerous times.

I'm starting to wonder if I managed to just completly hose this HDD.

-Alucardus

---

### Post by Dougie187 on 2007-06-04
Sounds like it. If no OS is on it. I would say just start from scratch if you can.

---

### Post by floke on 2007-06-04
If you still have issues, try the alternative installer. Has powered through for me several times when live cd couldn't do the partitions for want of chucking errors at me.

---

### Post by AlucardOni on 2007-06-04
I'm sorry, I'm a noob with ubuntu, "alternative installer", where and what is this?

I was also looking at another site while the last two posts where being done and I may be able to save this HDD by creating a Bootable CD of SuperFdisk and using its Erase MBR option.

I wish I wasn't stuck at work right now so I could work on this.

-Alucardus

---

### Post by Dougie187 on 2007-06-04
[Alternate Installer]("http://ftp.osuosl.org/pub/ubuntu-releases/feisty/ubuntu-7.04-alternate-i386.iso")

---

### Post by AlucardOni on 2007-06-04
Never mind, I apparently need to get new glasses, I will try the alternate when I get home and see if that works.

-Alucardus

---

### Post by handydan918 on 2007-06-04
The alternative installer is basically an Ubuntu disk that doesn't do "live". It just gives you an installation, but no "preview" of the O/S. But since you have already seen it,...
Just download the appropriate .iso for your system (PPC, x86, 64 bit, whatever) and burn  a cd as usual.

---

### Post by AlucardOni on 2007-06-05
Ok, have tried to use the SuperFdisk boot CD and got nothing, as in nothing on the screen whatsoever, and have also tried the alternative install but all that did was cause my sys to go into an endless restart loop.

I can't think of anything else, I may give up and find another HDD to install on.

Last chance, any thoughts.

-Alucardus

---

