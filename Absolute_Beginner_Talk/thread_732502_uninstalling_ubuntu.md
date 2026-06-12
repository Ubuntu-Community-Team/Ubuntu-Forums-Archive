---
title: "uninstalling ubuntu"
date: 2008-03-23
forum: Absolute Beginner Talk
---

### Post by angel_zone on 2008-03-23
i had recovered my NT boot loader again using super Grub and booted to windows i was about using partition magic to delete ubuntu partition but it keeps telling me can not delete unsupported formate??? so how can i delete these partitions

---

### Post by Oldsoldier2003 on 2008-03-23
> **angel_zone said:**
> i had recovered my NT boot loader again using super Grub and booted to windows i was about using partition magic to delete ubuntu partition but it keeps telling me can not delete unsupported formate??? so how can i delete these partitions

use a  [GParted Live CD]("http://gparted-livecd.tuxfamily.org/")

---

### Post by angel_zone on 2008-03-23
> **Oldsoldier2003 said:**
> use a  [GParted Live CD]("http://gparted-livecd.tuxfamily.org/")

i'm doing this right now i just wanted any body to tell me the right steps..is it like partition magic? just delete the partition and reboot?

---

### Post by Oldsoldier2003 on 2008-03-23
> **angel_zone said:**
> i'm doing this right now i just wanted any body to tell me the right steps..is it like partition magic? just delete the partition and reboot?

yes delete the partition, then apply the change. After you reboot you can use windows based tool to format the unallocated space

---

### Post by angel_zone on 2008-03-23
o.k i tried i booted from the live cd and started G parted but it did not work!! it tells me unable to delete please unmount any logical partition having a number higher than 8 .. what is this?

---

### Post by angel_zone on 2008-03-23
any other ideas??

---

### Post by angel_zone on 2008-03-23
i can't delete the main exe partition and the swap either!! thre is a lock sign besides it what does that means?

---

### Post by Oldsoldier2003 on 2008-03-23
> **angel_zone said:**
> i can't delete the main exe partition and the swap either!! thre is a lock sign besides it what does that means?

are you booting from a live cd? because the lock sign usually means the partition is mounted

---

### Post by angel_zone on 2008-03-23
> **Oldsoldier2003 said:**
> are you booting from a live cd? because the lock sign usually means the partition is mounted

yes i'm working from the live cd so what can i do next?

---

### Post by Oldsoldier2003 on 2008-03-23
> **angel_zone said:**
> yes i'm working from the live cd so what can i do next?

you could try opening a terminal and unmounting the partition, I can't remember if Gparted has that option available or if you need to use a terminal command....

---

### Post by angel_zone on 2008-03-23
so what about the exe partition?

---

### Post by angel_zone on 2008-03-23
> **Oldsoldier2003 said:**
> you could try opening a terminal and unmounting the partition, I can't remember if Gparted has that option available or if you need to use a terminal command....

how can i unmount the partition using the terminal??

---

### Post by angel_zone on 2008-03-23
> **angel_zone said:**
> how can i unmount the partition using the terminal??

what is the command i should use guys :mad:

---

### Post by ad_267 on 2008-03-23
the command is umount /dev/partitionToUnmount

Edit: and it is umount, not unmount.

Type man umount for more info

---

### Post by angel_zone on 2008-03-23
> **ad_267 said:**
> the command is umount /dev/partitionToUnmount

Edit: and it is umount, not unmount.

Type man umount for more info

o.k is it always that hard?? ubuntu@ubuntu:~$ umount/dev/sda8
bash: umount/dev/sda8: No such file or directory

---

### Post by ad_267 on 2008-03-23
You need a space between umount and the device to unmount.

If you're running the ubuntu live cd I'm pretty sure you can just unmount these in nautilus by right clicking on the drives and selecting unmount

---

### Post by angel_zone on 2008-03-23
> **ad_267 said:**
> You need a space between umount and the device to unmount.

If you're running the ubuntu live cd I'm pretty sure you can just unmount these in nautilus by right clicking on the drives and selecting unmount

i did!!!! but gparted close by his own what can i do

---

### Post by ad_267 on 2008-03-23
> **angel_zone said:**
> i did!!!! but gparted close by his own what can i do

What do you mean by gparted close by his own?

Did you succeed in unmounting the partitions containing your ubuntu installation? Make sure the partitions you are unmounting are the ones in gparted that you're trying to remove.

---

