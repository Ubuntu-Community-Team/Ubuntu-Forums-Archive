---
title: "dual boot"
date: 2006-09-18
forum: Absolute Beginner Talk
---

### Post by daveboy on 2006-09-18
how do i dualboot 
i have 2 copys of xp and ubuntu

---

### Post by xpod on 2006-09-18
WHAT.....You want to put 2 XP`s AND 2 Ubu`s on it.
Surely not:confused: 

To put just one of each on you would need to either have 2 hd`s or partition the single one so as to put XP on there first then the required Ubunto partitions after that.

Personally i use "fdisk" on a 98 bootdisk to format a partition for xp(the first third of hd)then install xp to it. THEN i use gparted on the ubunto live cd(or it`s own cd)
to create my ubunto partitions.
 Once i then run the actuall "installer" i chose the "manually edit partition table" option and make sure my xp one is not checked for formatting then proceed and all the rest is done for you including the setting up of the "grub" for dualbooting..

If you want more specific advice im not the man to ask...still learning myself:biggrin: 

Good luck

---

### Post by bulldog on 2006-09-18
Just make a partition for XP and leave enough free space for ubuntu.

Ubuntu needs about 10 GB to install but my experience is that's not much.

Howmany GB is your hdd?

It's all about what you will do with your install
Will you use XP as your primary OS then make this partition a little larger.

On the other hand if you want to use Ubuntu to explore and you want to download some stuf,it should be at a minimum of 20 GB.

---

### Post by Brunellus on 2006-09-18
Dual Boot howto:

[https://help.ubuntu.com/community/WindowsDualBoot?action=show&redirect=WindowsDualBootHowTo](https://help.ubuntu.com/community/WindowsDualBoot?action=show&redirect=WindowsDualBootHowTo)

---

### Post by daveboy on 2006-09-18
GB are 80
XP as my primary OS i have ubuntu on as well
how doi get to ubuntu

---

### Post by bulldog on 2006-09-18
Did you actual install Ubuntu?

If so you should  see a bootloader at startup called GRUB.
Now you can choose to boot Ubuntu or XP.

[It's possible you must hit escape to see the boot menu,watch your screen]

---

### Post by Brunellus on 2006-09-18
> **daveboy said:**
> GB are 80
XP as my primary OS i have ubuntu on as well
how doi get to ubuntu
windows overwrites the MBR with its own bootloader.  IF you installed Windows AFTER Ubuntu, you will need to reinstall the GRUB bootloader on the MBR.  Follow these instructions:

[Recovering Ubuntu after installing Windows]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows?highlight=%28GRUB-install%29")

---

