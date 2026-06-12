---
title: "Problems with mounting drives"
date: 2006-08-30
forum: Absolute Beginner Talk
---

### Post by cellarmation on 2006-08-30
Hi, this is my first post so i thought it should be in the beginner forum. I have installed the 64bit ubuntu 6 and it works, so there is a good start.

I have made a seperate fat32 partition as i have a dual boot of windows xp and ubuntu, this allows me to share files between them. The problem that i am having is when i turn ubuntu on, when i look in the computer thing, ubuntu recognises the fat32 drive and all the ntfs drives as removeable drives e.g. a cd drive. So it wont open them properly, this goes away as soon as i refresh the folder, but it always does it first thing.

This is a pain as i have firefox and thunderbird store there profiles on this partition(so ubuntu and xp can share profiles). As the drive doesnt properly mount untill i go into the computer folder and click refresh firefox just crashes.

Could i have done something wrong in adding the partions to the pmount list?
I did this and used method 1 : [https://help.ubuntu.com/community/MountingWindowsPartitions](https://help.ubuntu.com/community/MountingWindowsPartitions)

---

### Post by taurus on 2006-08-30
If you want to mount your fat32 partition, assuming it's /dev/hda2, in Ubuntu and want to read and write to it, as a regular users, then you need to modify your /etc/fstab and add this line the the end of it...

```
gksudo gedit /etc/fstab <-- to edit /etc/fstab
```
```
/dev/hda2   /media/share   vfat   defaults,umask=0000   0   0
```
Then from a terminal, run

```
sudo mkdir /media/share <-- create a mount point for your /dev/hda2
sudo mount -a <-- to mount it
```

---

### Post by whizbaby on 2006-08-30
Are you in the plugdev group? If not, type
sudo adduser YOURUSERNAME plugdev.
Still the same problem?
Then either ask yourself if you added the correct drives (what did you type exactly and what's your HD setup (partitioning) like?)
or manually enter the drives in fstab so they are mounted at boot time and not on request (I can tell you how the moment I know a bit more about your partition table).

---

### Post by cellarmation on 2006-09-02
ok i have had a play and i still cant get it to work, i think i see what you are trying to get me to do. I have probably just made the entry in the fstab thing wrong.

My Hard Drive configoration is as follows:
```

Hard Disk 1 - Partition 1 - 100g ntfs (windows xp) - /dev/hda1
             - Partition 5 - 14g ntfs (files) /dev/hda5
Hard Disk 2 - Partition 1 - 70g Extended 3 (linux) /dev/hdb1
             - Partition 3 - 70g Windows Virtual Fat (sharedfiles) /dev/hdb3
              - Swap Partition - 3g memory swap

```
I currently have access to only the linux partition easily, but hda1,hda5 and hdb3 if i click and refresh in the computer.

I would like access to hda1,hda5 and hdb3 regually without having to refresh them in the computer.

I tried using this code that you suggested but it didnt seem to work, it brought up some error when i tried to open the drive after rebooting. I may not have edited it correctly for the drive. Can you tell me what entries i need to make, or what i need to do?
Thank you for your help!

---

### Post by whizbaby on 2006-09-02
This is what *my* ntfs-hd entry looks like:
/dev/hda1       /media/hda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1

if the mount point (directory) /media/hda1 exists (if it doesn't, create: sudo mkdir /media/hda1) you should be able to mount your first ntfs partition with the same entry (besides gid=46 is the static group plugdev). This is what the entry for a vfat looks like:

/dev/hdb3       /media/hdb3     vfat rw,user,auto,utf8,gid=46   0  0

(remember: **mount -a** mounts all current entries in fstab)
Anything happening?
p.s.: if you encounter *some error* why not posting it? What do your entries look like? You're our only debugger... (this means: be verbose)

---

### Post by cellarmation on 2006-09-02
from playing around with what you all have said, and making new mount points i think i have sorted it. Thanks guys ^^

---

