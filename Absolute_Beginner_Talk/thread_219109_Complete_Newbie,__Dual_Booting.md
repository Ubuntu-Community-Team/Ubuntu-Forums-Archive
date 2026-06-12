---
title: "Complete Newbie,  Dual Booting"
date: 2006-07-19
forum: Absolute Beginner Talk
---

### Post by Dan Williamson on 2006-07-19
Hey,

I just got the Live CD for Ubutnu today and I love the UI and everything, but I don't want to install until I learn how to Dual-Boot properly as I tried with XP and Vista BETA 2 and it all went wrong.  I am running off the Live CD at the moment, but want to keep XP for programs such as Visual Basic and Macromedia Studio.

Any tutorials on how to dual-boot, I can pay for software if needed.

---

### Post by pestypest on 2006-07-19
ok first question is, do you want to dual boot with 1 HD or use 2 HD's? Are you going to use Dapper or Breezy? Are you going to use a AMD or Intel based system? dual processors or single?  let me know and i could help you as much as i can i have 2 laptops that i dual boot now. 1 with 2 HD's and 1 with 1 HD both have XP and Dapper on them.

---

### Post by aysiu on 2006-07-19
[http://www.psychocats.net/ubuntu/installing.html](http://www.psychocats.net/ubuntu/installing.html)

---

### Post by Dan Williamson on 2006-07-19
Thanks for the link,

Ok I am using erm Ubuntu 6.06 i'm on a Intel based processor with one processor, and I have one HDD which I think I need to split.

---

### Post by cstudent on 2006-07-19
> **Dan Williamson said:**
> Thanks for the link,

Ok I am using erm Ubuntu 6.06 i'm on a Intel based processor with one processor, and I have one HDD which I think I need to split.

You definately have to partition the drive into two partitions. Make Windows the main primary partition. You have to use something like Partition Magic or if the live CD has it, gparted. BACKUP YOUR DATA FIRST! When installing Ubuntu, let it place grub on the mbr.

---

### Post by Sonofmoog on 2006-07-19
Dual-booting Windows and Ubuntu is easy and effortless .. with a couple of caveats:

 - Once you install the Ubuntu bootloader into the MBR, you are committed to keeping Ubuntu.  When you decide to remove it is when you'll have problems.  It is not difficult to remove GRUB from the MBR, but most people new to dual-booting find it daunting.  It can be really scary turning on a PC with thousands of man-hours of work on it and be unable to boot the OS ..

 - Making changes to the bootloader configuration files can sometimes be tricky.  If you are new to this, resist the urge to experiment with different options and features.  Install it and forget it.  

Because sometimes dualbooting can be difficult, as you know from your experience, you need to buy some insurance.  Download the Smart Boot Manager, and create several floppy disks that will allow you to boot either OS.  SBM is a must-have tool, and it is free for personal use.

[http://btmgr.webframe.org/](http://btmgr.webframe.org/)

---

