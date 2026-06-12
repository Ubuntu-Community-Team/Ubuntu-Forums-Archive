---
title: "take ownership - operation not permitted ??"
date: 2007-12-02
forum: Absolute Beginner Talk
---

### Post by SnakeHips on 2007-12-02
I'm trying to take ownership of my 2nd hard drive (ex winxp) ,i've searched the threads and tried various things to no avail ,here is what i have so far ,any ideas pls...



sudo nano /etc/fstab

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc           proc         defaults                    0  0  
# /dev/sda1
UUID=65e34077-8e6c-428c-b683-fffe5449330d  /               ext3         defaults,errors=remount-ro  0  1  
# /dev/sda5
UUID=a6e20c4f-7cd1-4bc5-9d57-47f2a59a815e  none            swap         sw                          0  0  
/dev/hdc                                   /media/cdrom0   udf,iso9660  user,noauto                 0  0  
/dev/hdd                                   /media/cdrom1   udf,iso9660  user,noauto                 0  0  
/dev/fd0                                   /media/floppy0  auto         rw,user,noauto              0  0  
/dev/sda1                                  /media/sda1     ext3         defaults                    0  0  
/dev/sda5                                  /media/sda5     swap         defaults                    0  0  
/dev/hda1                                  /media/hda1     vfat         defaults                    0  0  
/dev/hda2                                  /media/hda2     vfat         defaults                    0  0  
/dev/hda3                                  /media/hda3     vfat         defaults                    0  0  


pete@pete-desktop:~$ sudo chown pete:pete /media/hda1
chown: changing ownership of `/media/hda1': Operation not permitted
pete@pete-desktop:~$

---

### Post by Vadi on 2007-12-02
I think root stole it from you. Try doing "sudo su" to become root, and do that again.

---

### Post by SnakeHips on 2007-12-02
I figured you was right ,tnx for the prompt reply................i tried it and get the same..........

pete@pete-desktop:~$ sudo su 
Password:
root@pete-desktop:/home/pete# sudo chown pete:pete /media/hda1
chown: changing ownership of `/media/hda1': Operation not permitted
root@pete-desktop:/home/pete# 

curiously i dont seem to have an entry for /dev/hda ??? maybe im looking in the wrong place ??

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc           proc         defaults                    0  0  
# /dev/sda1
UUID=65e34077-8e6c-428c-b683-fffe5449330d  /               ext3         defaults,errors=remount-ro  0  1  
# /dev/sda5
UUID=a6e20c4f-7cd1-4bc5-9d57-47f2a59a815e  none            swap         sw                          0  0  
/dev/hdc                                   /media/cdrom0   udf,iso9660  user,noauto                 0  0  
/dev/hdd                                   /media/cdrom1   udf,iso9660  user,noauto                 0  0  
/dev/fd0                                   /media/floppy0  auto         rw,user,noauto              0  0  
/dev/sda1                                  /media/sda1     ext3         defaults                    0  0  
/dev/sda5                                  /media/sda5     swap         defaults                    0  0  
/dev/hda1                                  /media/hda1     vfat         defaults                    0  0  
/dev/hda2                                  /media/hda2     vfat         defaults                    0  0  
/dev/hda3                                  /media/hda3     vfat         defaults                    0  0

---

### Post by SnakeHips on 2007-12-02
bump

---

### Post by SnakeHips on 2007-12-02
Hmmmmm ,seems although the drive is mounted? it cant be seen ?

pete@pete-desktop:~$ sudo blkid /dev/hda
pete@pete-desktop:~$

---

### Post by Vadi on 2007-12-02
Maybe try /dev/hda1 instead of /mevia/hda1 ?

---

### Post by the Didey on 2007-12-02
I'm having the same trouble as snake hips. I have 4 partitions: 2 i need to rename and 2  i need to unmount and not mount at startup.

my chown command does the exact same thing. not permitted

I get the same message whe I try to use gksudo nautilus

EDIT: I just notice SnakeHips is using Feisty 7.04....I'm on Gutsy 7.10.


I don't know if it matters but 3 of the partitions are from my windows hard drive (which is a separate drive). they are FAT32, FAT32, FAT16 and NTSF

if helpful:



# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb2
UUID=2d4e8088-9ec6-4057-a08b-57a483e7c7b4 /               ext3    defaults,errors=remount-ro 0    $
# /dev/sdb4
UUID=c1648c1e-cf7f-4975-a6f8-fff537e30fea /home           ext3    defaults        0       2
# /dev/sda1
UUID=07D6-011C  /media/sda1     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sda2
UUID=AE142A5A142A25B5 /media/sda2     ntfs    defaults,umask=007,gid=46 0       1
/dev/sda3       /media/sda3     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sdb1
UUID=474F-B0CB  /media/sdb1     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sdb5
UUID=b2f0747a-98fe-4a33-bcaa-25beab502448 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0

---

### Post by schorsch on 2007-12-02
Vfat partitions do not support permissions as linux or ntfs partitions. You have to set the right permissions when you mount the partition so an entry in /etc/fstab will do the trick.

```
/dev/hda1 /media/hda1 vfat rw,nosuid,nodev,utf8,umask=077,gid=1000,uid=1000, 0 1
```
Replace the values for gid and uid with the values for your user and group:
```
grep *username* /etc/passwd
```
Umount the drive and remount it:
```
sudo umount /dev/hda1
sudo mount /dev/hda1
```
... and your user should have write permmissions.

---

### Post by SnakeHips on 2007-12-02
Ah ha ,gettin somewhere....

pete@pete-desktop:~$ sudo blkid /dev/hda
pete@pete-desktop:~$ sudo blkid /dev/hda1
Password:
/dev/hda1: UUID="4752-EA36" TYPE="vfat" 
pete@pete-desktop:~$

---

### Post by SnakeHips on 2007-12-02
Ok ,thanks everyone ,this fix has worked....



Vfat partitions do not support permissions as linux or ntfs partitions. You have to set the right permissions when you mount the partition so an entry in /etc/fstab will do the trick.

Code:

/dev/hda1 /media/hda1 vfat rw,nosuid,nodev,utf8,umask=077,gid=1000,uid=1000, 0 1

Replace the values for gid and uid with the values for your user and group:
Code:

grep username /etc/passwd

Umount the drive and remount it:
Code:

sudo umount /dev/hda1
sudo mount /dev/hda1

... and your user should have write permmissions.

---

### Post by schorsch on 2007-12-02
Nice to read that. Can you please mark this thread as solved as it may help others, too?

---

### Post by the Didey on 2007-12-02
This also worked for me for 3 out of 4 partitions

The one that isn't working is the "DellUtility" partition so that might have something to do with it.

i don't really need to be the owner on that so I think I'll figure out how to avoid it mounting at startup.

Many thanks to Schorsch

---

### Post by schorsch on 2007-12-02
I use a Dell laptop and you do not have to mount the "DellUtility" partition at boot under linux as it only provides the function to restore the preinstalled system from delivery state. Just put a dash ("#") in the first place of the corresponing line in "/etc/fstab" and you should be safe. It only matters if you will use it via grub.

---

### Post by the Didey on 2007-12-02
thanks schorsch that did the trick.

I just wanted it not to mount at boot anyway....who cares who owns it.

---

### Post by Screaming Monkey on 2007-12-06
Thanks SnakeHips for the post and schorsch for the solution.  This helps!  Nice and concise too.

---

