---
title: "File permissions of mounted drive"
date: 2006-03-27
forum: Absolute Beginner Talk
---

### Post by Stuperfied on 2006-03-27
Hi all.

What I have:
Single drive with 10Gig XP NTFS partition, 20Gig User FAT32 and 10Gig Ubuntu. Ubuntu is recently installed on what was otherwise an XP box.

Problem:
I successfully mounted the FAT32 partition to the mnt/hda5 directory through the disk program in administration under system. Now when I try to edit my html files on that drive, it tells me that I cannot edit the files because I am not the owner. They have a 0755 permission, so I tried to change that in the file viewer but it wouldnt let me. I went to shell and entered ```
sudo chmod 0775 index.html
``` and it executed without error but the permissions of the file did not change.

Question:
Anyone know how I can access my files?

---

### Post by Sutekh on 2006-03-27
I don't know how the disk admin thing works, but I do know how to mount FAT32 partitions.
(Also chmod/chown can't function on Windows partitions as they are not compliant with Unix/POSIX permissions)

You need to edit the /etc/fstab - the configuration file that contains mounting information

This will create a backup and edit the fstab
```
sudo cp /etc/fstab /etc/fstab_backup
sudo nano /etc/fstab
```
Then add or modify this line
```
/dev/hda5   /mnt/hda5   vfat   iocharset=utf8,umask=000   0   0
```
Save the file (Ctrl+O) and exit (Ctrl+X), then issue
```
sudo mount -a
``` to refresh the mount points without needing to reboot.

---

### Post by Stuperfied on 2006-03-27
Thanks, i'll reboot into Ubuntu and give it a go.

---

### Post by Stuperfied on 2006-03-27
Im in Ubuntu now, I entered the sudo cp thing, then the nano thing and put in that line but now I dont know how to save it. I tried just closing the window but it didnt save the settings so I had to do it all again.

How do I save so I can do the ```
sudo mount -a
``` thing?

---

### Post by Stuperfied on 2006-03-27
whoops, sorry, found it in your post.

---

### Post by Stuperfied on 2006-03-27
It worked, I still had to reboot for the changes to take effect because the ```
sudo mount -a
``` command didnt do its job but the rest was exactly what I needed.

Thanks again.

---

