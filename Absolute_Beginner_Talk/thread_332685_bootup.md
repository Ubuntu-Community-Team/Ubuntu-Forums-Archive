---
title: "bootup"
date: 2007-01-06
forum: Absolute Beginner Talk
---

### Post by kuvera on 2007-01-06
I reinstalled Windows on my main partition and Grub is not shown to choose linux partition. How can I reactivate it?

cheers,
kuvera ([Budapest Tégla]("http://tegla-haz.hu"))

---

### Post by Sasa_Ivanovic on 2007-01-06
well this is very simple :

- either you deleted the linux partrition
- or you deleted the partrtion the GRUB was on ( the windows partrition )

Insert your Live CD and start installation, tell us what you see in gparted.

---

### Post by sailor2001 on 2007-01-06
the only way I am aware of is to get a MEMPIS live disk and log in as root/root/ and then installation center/ repair grub/root

---

### Post by CroEragon on 2007-01-06
Grub is not showing Linux (you see Windows) or Grub is not showing at all (boot straight to Windows)?

---

### Post by Sasa_Ivanovic on 2007-01-06
type :
```

fdisk -l

```

---

### Post by Bigbluecat on 2007-01-06
If you have re-installed Windows after Linux it will overwrite grub in the MBR. Windows does not like to have another OS there.

You need to re-install grub to the MBR. You can do this with the LiveCD.

Before you do this did you modify (add or subtract) any partitions. If so we may need to edit your menu.lst file as well.

The following is cut from a helpful post by Bulldog (it's quicker than typing):rolleyes:

You have to boot into the live ubuntu cd to accomplish this,
When you get to the desktop open a terminal and enter. 

This will get you a grub> prompt

   ```
sudo grub
```This will return a location which you have to use in the next command.
```
find /boot/grub/stage1
```      [LEFT]
[/LEFT]
 
Enter the location given by the previous command in the next command. 
     [LEFT]```
root (hd?,?)
```[/LEFT]
 
Next enter the command to install grub to the mbr
     
```
setup (hd0)
```Exit the grub shell
     
```
quit
```Now Grub will be installed to the mbr.

Hopefully after this you have grub back. You may still need to edit your menu.lst to get windows to boot.

---

