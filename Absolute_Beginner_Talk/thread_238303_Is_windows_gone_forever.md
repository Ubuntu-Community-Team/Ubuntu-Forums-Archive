---
title: "Is windows gone forever?"
date: 2006-08-17
forum: Absolute Beginner Talk
---

### Post by chester on 2006-08-17
I am about to finalize my installation of Ubuntu and I have a very basic question (i am loading it off of the live cd). Will I still be able to get to windows after I do this? The computer only has a single hard drive with about 14 gigs of free space, but am I actually "getting rid" of windows forever? (I don't know how many of you folks are married, but this is one of those questions that will definitely have ramifications on my marriage......)

---

### Post by savethesquirrels on 2006-08-17
Running the Live CD and NOT installing Ubuntu will not harm Windows. If you install it though and delete the partition or format the hard drive it will get rid of Windows. I am not sure, but I believe Ubuntu may detect the Windows partition and help you setup a dual boot environment, so when you turn on the computer you will have the choice of either Windows or Ubuntu to boot. 

Always backup your computer before installing something like this though just in case.

---

### Post by darkenedday on 2006-08-17
Lol, no you shouldn't lose windows, when you go to partition your HD, it should ask if you either want to resize the current windows partition, use the free space already there, or erase the entire disk, after so select whichever option to keep windows (1 or 2) it will install GRUB boot loader which, when you power on your PC will allow you to choose between either Ubuntu or windows

---

### Post by xxFelixDCatxx on 2006-08-17
yea... you're windows partition is gone if you selected install on disk. sorry, but the only way to get windows back is to reinstall it.  there's a how-to somewhere that specifies dual booting...

---

### Post by anaconda on 2006-08-17
Windows doesn't wanish anywhere, if you install ubuntu to your 14GB of free space.

But if you decide to delete ubuntu later, THEN windows won't boot anymore, until you fix your mbr (master boot record) back to  what it was...

hmmm.. playing with computer affects marriage? huh.. some people take computers waay too seriously.  :)

---

### Post by theratster on 2006-08-17
If you do it right, it won't wipe out windows

When you run the installer, be sure to select to customize your own partitions using the partition manager. That will allow you to set up multiple hard drive partitions, one for Ubuntu, one for the Ubuntu swap, and the leftover for windows.

For example, I have a 38 GB harddrive with Windows XP. I set up to leave 30 GB for Windows, 7 GB for Ubuntu, and 1 GB for swap. Then, whenever you boot your system, it will give you a choice: to either boot into Windows, or boot into Linux.

---

### Post by sanderella on 2006-08-17
We have 2 computers: one for windows and one for ubuntu. There are some windows programs that just won't work on ubuntu....yet:)

---

### Post by sean_ on 2006-08-17
> **chester said:**
> I am about to finalize my installation of Ubuntu and I have a very basic question (i am loading it off of the live cd). Will I still be able to get to windows after I do this? The computer only has a single hard drive with about 14 gigs of free space, but am I actually "getting rid" of windows forever? (I don't know how many of you folks are married, but this is one of those questions that will definitely have ramifications on my marriage......) No, when I installed Ubuntu (latest) it didn't ask me to install GRUB, but instead, it installed GRUB automatically.

---

### Post by aysiu on 2006-08-17
I would not install anything unless you:

1. Have backed up your important data
2. Have an easy way to reinstall Windows should you mess up
3. Know Ubuntu better and actually know what you're doing

As others have said, the live CD won't harm your Windows installation unless you click the **install** button on the desktop.

Play around with the live CD for two weeks--that's my advice. Read a lot before you install anything. Slow is good, especially if a bad installation will adversely affect your marriage.

---

