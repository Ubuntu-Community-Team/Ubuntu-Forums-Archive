---
title: "missing partition"
date: 2006-08-19
forum: Absolute Beginner Talk
---

### Post by TriJump on 2006-08-19
I've created a partition that I have formated as FAT32 for a go between Windows and Ubuntu.  However, XP recognizes the partition as being there and will allow me to write to it, but Ubuntu says that it is inaccessible.  If I try to use the terminal to mount it using sudo mount /dev/hda5 I get the error saying cant find /dev/hda5 in /etc/fstab or /etc/mtab.  I looked in fstab and saw no mention of hda5, any idea as to why it would not be there, and how to add it to my fstab file? Thanks

Edit:  I was thinking, can I just add an entry to my fstab file manually?  Or would that not work?

---

### Post by TFX360 on 2006-08-19
You can manually add a drive to /etc/fstab

I have my Windows disks there (NTFS)

Looking for you how-to add a FAT32 one.

brb

Here ya go something like this. Backup your fstab first!

```
cp /etc/fstab /etc/fstab.bck
```

/dev/hda5 /media/stuff vfat rw,uid=1000,gid=1000 0 0


Kind regards,


TFX

---

### Post by TriJump on 2006-08-19
Awesome, thanks for the help

---

### Post by TriJump on 2006-08-19
when i try and edit my fstab file - I get an error saying I do not have permission to do so.  I am the only user on this machine so I thought that I would have all permissions.

---

### Post by TFX360 on 2006-08-19
Your welcome! Thanks for the reply!


Kind regards,


TFX

---

