---
title: "installed XP and cannot boot Ubuntu"
date: 2007-06-28
forum: Absolute Beginner Talk
---

### Post by sahil1 on 2007-06-28
Hey, 

I had Vista when I choose to install Ubuntu fiesty fawn. Everything worked fine, but then i decided that vista is evil and re-installed XP on the same partition without touching the Ubuntu partition and the swap partition. After I installed XP i noted that Grub no longer loads at start-up and my computer is directly going into XP. Pressing escape on powering on does not do anything. I tried loading in the LiveCD and i got a  million erros with long numbers no words.  

Is there any way i can get my Ubuntu back, I don't have time to re-install and get it back to the way i had set it up perfectly. I will use any third party booloaders also if you can tell me.


Noob here.

Thanks in advance,

Sahil

---

### Post by jputman01 on 2007-06-28
as far as i know you probably wrote over grub with your xp, in my experience its always easier to install windows prior to ubuntu, easiest scenario would probably be to just reinstall ubuntu

---

### Post by r4ik on 2007-06-28
Try,

[http://knowledge76.com/index.php/Restore_Grub](http://knowledge76.com/index.php/Restore_Grub)

or,

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

Good luck !

---

### Post by dptxp on 2007-06-28
Windows thinks that it is the only operating system in this world.

---

### Post by Rabindranath on 2007-06-28
Try this,

It is a live cd. 

"http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828"

But personally I think it is better to reinstall ubuntu. Its only a matter of about 30 to 40 minutes.

---

### Post by sahil1 on 2007-06-28
I have a working LiveCD because it works fine on my other computer. Installing takes about 30 -40 Min, but the problem is that the LiveCD won't boot on the computer with the problem. 

Is there any way to boot without GRUB using something else?

---

### Post by r4ik on 2007-06-28
Your computer's BIOS must be set to boot from CD first; otherwise, Windows will just load up again. To get into the BIOS settings, you usually have to press one of these keys during boot-up: Escape, F1, F2, F12, or Delete. Usually your computer will tell you which key to use.

from,

[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

Good luck !

---

### Post by sahil1 on 2007-06-28
No, my BIOS is fine because GPARTED boots up fine. But i anyways checked it and it is set to boot in this order:

1: Removable storage
2: Cd/DVD
3: Hard Disk

and there is no removable storage attached to the computer when i run it. Grr. I might just wait for Gusty to re-install it. 

Thanks for all suggestion. Still accepting new ones.

---

### Post by r4ik on 2007-06-28
Disable the removable storage and it should boot.

---

### Post by dptxp on 2007-06-28
Your CD DRIVE may be the problem why you can not boot from Live CD. THe Live CD may not be
in as good condition as the GParted one. Load Live CD in Windows and check.

---

### Post by sahil1 on 2007-06-28
Disabled the Removale Storage and Loaded the LiveCD and it was fine in Windows. I downloaded OSL2000 BootManager. I think that My Linux partition is messed up or something beacuse the BootManager recognized the Linux partition and the Windows partition, but was unable to boot into Linux. I think formatting the partitions and re-installing will be less complicated.

Sahil

---

### Post by r4ik on 2007-06-28
It is up to you,

Good luck :)

---

