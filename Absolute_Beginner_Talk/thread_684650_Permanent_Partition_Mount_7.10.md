---
title: "Permanent Partition Mount 7.10"
date: 2008-02-01
forum: Absolute Beginner Talk
---

### Post by romphill on 2008-02-01
Is it possible to permanently mount a FAT32 partition so that when Ubuntu loads, the other partition loads as well.

max@pavilion:~$ sudo fdisk -l
[sudo] password for max:

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x585f6825

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          64      514048+  82  Linux swap / Solaris
/dev/sda2              65        2674    20964825   83  Linux
/dev/sda3            2675        9201    52428127+   b  W95 FAT32
max@pavilion:~$ 


That's what I've got right now.  sda2 has linux, sda3 I use to store music, movies, photos, and documents.  The plan/hope is that once I get XP reinstalled I'll be able to open everything from that partition whether I'm in ubuntu or XP.

Either way, my issue right now with Ubuntu is that anytime I want play music, I have to right click on the drive and click mount.  I'm hoping I  can permanently mount the partition and also not havei t show up on my desktop.

Thanks

Also, I did find several threads about permanently mounting an XP partition, but this is FAT32 and not NTFS so I wasn't sure if there were any differences.

---

### Post by airbornemist6 on 2008-02-01
Indeed, you can edit your FSTAB, and there is no actual difference between mounting an NTFS and a FAT32, other than I believe you have to specify that it is vfat. Unfortunately, I'm about to go to class so I can't find a thread for you. But you should be able to use the same threads you found for NTFS.

---

### Post by taurus on 2008-02-01
Edit /etc/fstab from a terminal with

```
gksudo gedit /etc/fstab
```
and add this line to the end of it.

```
/dev/sda3   /media/sda3   vfat   defaults,umask=000   0   0
```
Save it.  Then, create a new mount point for it.

```
sudo mkdir /media/sda3
```
Now, reboot.  Your /dev/sda1 will be mounted to /media/sda3 each time you boot Ubuntu now.

---

### Post by Malta paul on 2008-02-01
You could try: 'sudo mount -a  Then reboot:)

---

### Post by rbc on 2008-02-01
To address the last issue. I believe when any device is mounted in /media, it will show up on the desktop. To change this, press Alt +F2 then type "gconf-editor" (without the quotes). Navigate through apps/nautilus/desktop, then uncheck "volumes visible".

---

### Post by romphill on 2008-02-01
Thanks guys, problem's solved.

One issue that did arise is my wallpaper...I'm guessing that wallpaper files are accessed before the other drive during boot because if I reboot with a wallpaper that's in the newly mounted drive, the screen comes up black...is this correct or is something else going on?

---

### Post by Nythain on 2008-02-01
wallpaper is usually loaded way after partitions are mounted... in fact, wallpapers are loaded untill you log into your Desktop Environment, whereas partitions are mounted like before almost anything is done

---

