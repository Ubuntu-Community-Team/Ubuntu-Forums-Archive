---
title: "ready to upgrade to gutsy but will my current dual boot get messed up"
date: 2007-10-20
forum: Absolute Beginner Talk
---

### Post by videocheez on 2007-10-20
I currently have a dual boot set up with feisty and xp pro.  Windows is on a RAID0 drive and Ubuntu is on an eSATA drive.  The Ubuntu drive is set in bios as primary and windows drive as secondary.  I used GRUB utility to modify menu.lst file so that after 10 seconds if don't toggle down to load ubuntu, windows will automatically load.  
When installed feisty the first time i disconnected all of the windows drives because the first time i tried to install it, I i wrote over my windows MBR.  
If i use the upgrade tool to install gutsy, will i have to modify the dual boot set-up in the menu.lst file.? Should i disconnect the windows drives again or will the upgrade tool only affect the drive the Ubuntu is currently on.  Any help will be appreciated.  Thanks in advance.

VC

---

### Post by barkej on 2007-10-20
Gutsy should detect your Windows partition and take care of the settings for dual boot for you. I don't see that you would have any trouble.

---

### Post by videocheez on 2007-10-20
Ok.  I suppose I will give it a try.  Just to be safe, I think I will disconnect the drive that windows is on.
Thanks for the information.

---

### Post by HW_Hack on 2007-10-20
My dual boot (dual disk) upgrade when fine --- don't disconnect the XP drive --- could foul up GRUB ---just upgrade - should be fine

---

