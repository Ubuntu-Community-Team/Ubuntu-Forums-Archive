---
title: "Dual boot with existing Win XP"
date: 2005-12-26
forum: Absolute Beginner Talk
---

### Post by esteban2x on 2005-12-26
I'm ready to install ver 5.04 Ubuntu over Windows XP. I'm doing it for a friend.
He has a 60 gig hard drive and is only using 30 gigs. How do i get Ubuntu to dual boot and leave all his windows shit on the computer?

---

### Post by bagel on 2005-12-26
Hello there;

How is XP partitioned? All on one partition or different drives?

If he has different drives, then it is rather easy:
Just select the partition you want to use for Ubuntu in the installation dialog(be careful not to format the whole disc, or the one with WinXP on it :) ). When installing the bootloader, a Windows-boot-entry should be created automatically.

If all the 60G are on one partition, you have to apply a partition resizing tool, such as     **Partition Magic**(for Win) first.

Greetings, 
bagel

---

### Post by esteban2x on 2005-12-26
You guys here on this forum are amazing. Yes the XP is using the whole partition.  Is there a free program I can use. I used to have partition magic but it was old. Thanks. Yea, Once I get his computer up and running...his is the guinea pig, I'll be installing on mine.

---

### Post by kjacks on 2005-12-26
check this out:

[https://wiki.ubuntu.com/WindowsDualBootHowTo]("https://wiki.ubuntu.com/WindowsDualBootHowTo")

I was in the exact same place as you about a month ago.  The Ubuntu install disk will let you resize your Windows partition and install Ubuntu.  Just be sure to back everything up and read the instructions carefully.  I didn't have any problems but that's the advice I was given.

---

### Post by Sef on 2005-12-27
Why don't you download, burn, and install Ubuntu 5.10 (Breezy) instead of 5.04 (Hoary.)   It's moe up to date.  I used to dual boot my computer, and it installed without any problems.

---

### Post by esteban2x on 2005-12-29
So I just download the newer version, burn it and run it? Then I get to the partitioning and how will I know I'm not destroying my XP? Thanks

---

### Post by bavs on 2005-12-29
well it was real breezy going through the partition thing during the installation.  dont worry it will tell u where everything is just create a new partition from free space and make sure u create a swap space partition as well about 2gig would be nice thats what i have done.

---

### Post by towsonu2003 on 2005-12-29
[QUOTE=kjacks]
[https://wiki.ubuntu.com/WindowsDualBootHowTo]("https://wiki.ubuntu.com/WindowsDualBootHowTo")[/QUOTE]
 follow this step by step. 

[quote=esteban2x]how will I know I'm not destroying my XP?[/quote]well, basically, you won't destroy it if you follow each and every step, but you have no way of knowing that in theory=> so, before you start the installation, **backup every possible thing** in Windows in case something goes wrong...

---

### Post by prizrak on 2005-12-30
Also run the disk defrag in windows it will make sure that nothing gets overwritten.

---

### Post by Sef on 2005-12-30
This is from another post of mine:

> I just have set up a dual boot with XP and Ubuntu. Make sure that the windows is installed first, if it isn't installed. When partitioning, keep the windows partition as the bootable partition (bootable is set to yes,) and make sure the root partition's bootable is set to no.

Also follow these directions that Herman wrote. I followed them when installing Ubuntu.

[http://www.users.bigpond.net.au/hermanzone/](http://www.users.bigpond.net.au/hermanzone/)

---

### Post by techmonk on 2006-01-01
Hello!  This forum is great!  I recently purchased a new machine with WinXP already installed (taking up the entire disk), but want to learn about Linux.  I am concerned about the NTFS issues, but with the info presented here my (current) questions appear to have been answered already.  I look forward to the experience.  Thanks!

---

