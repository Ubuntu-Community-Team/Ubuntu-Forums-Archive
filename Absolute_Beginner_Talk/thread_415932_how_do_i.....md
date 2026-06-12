---
title: "how do i...."
date: 2007-04-20
forum: Absolute Beginner Talk
---

### Post by keef247 on 2007-04-20
gain access to a screwed up partitions home directory so that i can copy the contents to another hard drive so that i can do a fresh install and then copy the contents back to the new install's home directory?
if that didnt make sense....
i have a screwed up partition that i cannot fix... i want to keep my contents of my home dir and move them to another drive then copy them to a new formatted installation of ubuntu.
how do i do this.
litterally every command i need to enter please.
cheers

---

### Post by taurus on 2007-04-20
Do you have a seperate /home?  Otherwise, post the layout of your disk then.

```
sudo fdisk -l
```

---

### Post by bwhite82 on 2007-04-20
Can you even boot into it? If yes, then it is as simple as:
> 
sudo cp /home/username /media/sdaX

Where username is obviously YOUR username and sdaX is the harddrive you are copying to.

---

### Post by bwhite82 on 2007-04-20
If no, then you have to boot into a LiveCD and find out which partiton is the screwed up one (sda1, hda0, etc) and in a console:

> sudo mkdir /media/sdaX
sudo mount /dev/sdaX /media/sdaX
sudo cp /media/sdaX/home/username /media/sdaY

---

### Post by keef247 on 2007-04-20
root@ubuntu:~# sudo fdisk -l

Disk /dev/hda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        4542    36483583+   7  HPFS/NTFS
/dev/hda2            4543       19079   116768452+  83  Linux
/dev/hda3           19080       19457     3036285    5  Extended
/dev/hda5           19080       19457     3036253+  82  Linux swap / Solaris

Disk /dev/hdb: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb2   *           1       24792   199141708+   7  HPFS/NTFS

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1

---

### Post by keef247 on 2007-04-20
right got it mounted cheers guys

---

