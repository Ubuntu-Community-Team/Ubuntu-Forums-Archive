---
title: "[SOLVED] Hard drive: how change name label and restrict access to user"
date: 2008-03-17
forum: Absolute Beginner Talk
---

### Post by Ubunt2Etudiant2008 on 2008-03-17
Hi I have just newly installed ubuntu

i have 2 hard drives, i installed normally, home and system and all is on one drive

the other drive was still fat32 so i formatted it to ext3 with gparted

then i had to mount it, now it shows on my desktop labeled simply as "disk" 

**i have two questions**

question 1:
how do i change the name of my smaller 2nd hard drive?

question 2:
i have made a 2nd account for the children, how can i block access to the 2nd hard drive?

thanks

> root@rachel-desktop:~# fdisk -l

Disque /dev/sda: 8455 Mo, 8455200768 octets
255 heads, 63 sectors/track, 1027 cylinders
Units = cylindres of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd444d444

Périphérique Amorce    Début         Fin      Blocs    Id  Système
/dev/sda1   *           1         978     7855753+  83  Linux
/dev/sda2             979        1027      393592+   5  Extended
/dev/sda5             979        1027      393561   82  Linux swap / Solaris

Disque /dev/sdb: 6488 Mo, 6488294400 octets
255 heads, 63 sectors/track, 788 cylinders
Units = cylindres of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8df89a83

Périphérique Amorce    Début         Fin      Blocs    Id  Système
/dev/sdb1   *           1         788     6329578+  83  Linux


---

### Post by Nepherte on 2008-03-17
You can solve your second problem by working with users and groups. Create a new group and add yourself to it. Then change the ownership of the disk
```
chown -R username:groupname diskmountpoint
```
Afterwards you will have to restrict the "others" not belonging to the group from reading, writing and executing files (just right click on the map and go to the rights tab).

---

### Post by jken146 on 2008-03-17
Please post the output of ```
cat /etc/fstab
```

---

### Post by Ubunt2Etudiant2008 on 2008-03-17
automatically an icon on my desktop shows the 2nd hard drive labeled as "disk"

i right click it

and choose "properties"

then under "permissions" i want change so its only accessible to my admin account

but its all grayed out!

**how do i do it?**

-------------------------

when i log into the children's account the disk icon shows on the desktop too

i would prefer if it didn't

how do i block access to the 2nd drive so it cant be accessible from the children's account?

thanks

---

### Post by Ubunt2Etudiant2008 on 2008-03-17
here

> rachel@rachel-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=e77a7024-1093-4e87-97c2-bc3a2ae8b04c /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=ec134e62-85f3-42a9-a3ae-a5c0bc0247b7 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0


---

### Post by Ubunt2Etudiant2008 on 2008-03-17
> **Nepherte said:**
> You can solve your second problem by working with users and groups. Create a new group and add yourself to it. Then change the ownership of the disk
```
chown -R username:groupname diskmountpoint
```
Afterwards you will have to restrict the "others" not belonging to the group from reading, writing and executing files (just right click on the map and go to the rights tab).

sorry

what is my "chown -R username:groupname diskmountpoint"???

[B]is "groupname" where i put in a name i make myself?

what is my "diskmountpoint"?[/B]

sorry i am a newbie can someone please explain this in little simpler steps

thanks

---

### Post by jken146 on 2008-03-17
The smaller hard drive is sdb and the only partition on it is sdb1.  There is no entry for this in fstab, which is why it is automatically being mounted as "disk" in /media and showing up on the desktop.

Create a mount point: ```
sudo mkdir /mnt/smallerDrive
``` Of course, you can replace smallerDrive with whatever name you like.

Then add an entry to fstab:
```
gksu gedit /etc/fstab
```
Add this line to the end of the file: > /dev/sdb1 /mnt/smallerDrive ext3 defaults 0 0

Unmount sdb1: ```
sudo umount /dev/sdb1
```
Mount it again in the new place: ```
sudo mount -a
```

Then create a group, add yourself to the group, and change the ownership of /mnt/smallerDrive: ```
sudo chown -R userName:groupName /mnt/smallerDrive
```

Then change the permissions of /mnt/sdb1: ```
sudo chmod -R 660 /mnt/sdb
```

That should do the trick.

---

### Post by jken146 on 2008-03-17
> **Ubunt2Etudiant2008 said:**
> is "groupname" where i put in a name i make myself?
Yes, it is the name of the group you will create.  Go into System -> Administration -> Users and Groups to do this.

> what is my "diskmountpoint"?
See my previous post.

---

