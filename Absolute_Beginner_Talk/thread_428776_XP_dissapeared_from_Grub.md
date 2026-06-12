---
title: "XP dissapeared from Grub"
date: 2007-04-30
forum: Absolute Beginner Talk
---

### Post by grim_d on 2007-04-30
I have (or had) a dual boot system, ubuntu and XP, both instlalations are on seperate hard drives.

i just upgraded to feisty fawn from dapper drake but i didnt "upgrade" i just did a fresh install, now my grub no longer shows XP as a bootable OS, 

what happened to it and how do i get it back? If i have to reinstall ubuntu that's ok.

cheers

---

### Post by Seisen on 2007-04-30
Did you follow the guide to dualboot  Windows and Ubuntu on two seperate hard drives.

---

### Post by bulldog on 2007-04-30
Just add an entry for you windows in menu.lst.
```
gksudo gedit /boot/grub/menu.lst
``` will open it.

It's a little depending on which partition and hdd windows is located,but it should look like this,
```
### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows XP Professional
rootnoverify		(hd1,0)
map          (hd0) (hd1)
map          (hd1) (hd0)   
savedefault
makeactive
chainloader	+1
```

---

### Post by kittyhawk63 on 2007-04-30
Do you remember your GRUB setting for Windows in Feisty? If not...

Set your Windows drive to slave.

Set your Linux drive to master.

Put your Live CD into the CD Rom drive.

Reboot

Install Feisty with the install feature. Make sure you choose to install it on the drive that you want Linux.

Once installed shut down...remove disk, reboot,  and you will see both drives on GRUB.

This works. There may be an easier method.

---

### Post by grim_d on 2007-04-30
Thanks bulldog that worked perfectly, i didnt realise it would change the grub, i had a lot of trouble with a dual boot the first time i tried ubuntu and its not something i like dealing with lol.

Anyway thanks again, now to figure out how to do everything else in feisty

---

### Post by bulldog on 2007-04-30
> **grim_d said:**
> Thanks bulldog that worked perfectly, i didnt realise it would change the grub, i had a lot of trouble with a dual boot the first time i tried ubuntu and its not something i like dealing with lol.

Anyway thanks again, now to figure out how to do everything else in feisty

Basically the same as in Edgy and Dapper.:) 
But if there's a problem,just ask,there a lot of folks who can help.

---

