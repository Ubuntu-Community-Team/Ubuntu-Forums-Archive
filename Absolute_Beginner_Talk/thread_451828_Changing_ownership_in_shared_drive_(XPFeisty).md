---
title: "Changing ownership in shared drive (XP/Feisty)"
date: 2007-05-22
forum: Absolute Beginner Talk
---

### Post by Pai on 2007-05-22
I recently set up a dual boot system with Feisty and XP. As part of this set up, I have a shared drive (FAT32) in which both operating systems can read/write to.  One folder in this drive (D: on Windows, sda3 on Ubuntu) is "My Documents," which appears with a lock over it in Feisty.

So I can access files in this folder, but I can't add my own. When I try to add files to this folder, I receive the error: "You do not have permissions to write to this folder"
[img]http://img472.imageshack.us/img472/5884/screenshotfd9.png[/img]

Can I change it so that I can write to that folder? How would I do so? 

Anything to do with the *chown *command? 

As a related question, when I'm working in the terminal, how do I handle folder names that have a space in them, such as "My Documents"? The problem I had earlier is that the terminal interprets "/media/sda3/My Documents" as two different tokens.

Thanks in advance.

---

### Post by Ek0nomik on 2007-05-22
I presume that partition is NTFS?

---

### Post by Nekiruhs on 2007-05-22
```
sudo apt-get install ntfs-config
```
Will take care of the NTFS drives. And to deal with spaces just put it in quotes or precede each space with a \ (home/user/My\ Documents)

---

### Post by mitch.c on 2007-05-22
> **Pai said:**
> So I can access files in this folder, but I can't add my own. When I try to add files to this folder, I receive the error: "You do not have permissions to write to this folder"

Can I change it so that I can write to that folder? How would I do so? 

Anything to do with the *chown *command?
If it was a linux file system, chown and chmod would be your friend. A (v)fat filesystem needs to have the owner  and/or group set when mounted, so you need to edit /etc/fstab. Here's an example for a vfat partition I use on my system:
```
UUID=44D9-1B3B /home/shared vfat defaults,utf8,umask=002,gid=100 0 1
```
You need to use a gid for a group that exists on your system. You might try the plugdev group. To get the gid, type:
```
$ cat /etc/group | grep plugdev
```
Keep in mind you will have to re-mount the file system after making the changes.
> **Pai said:**
> As a related question, when I'm working in the terminal, how do I handle folder names that have a space in them, such as "My Documents"? The problem I had earlier is that the terminal interprets "/media/sda3/My Documents" as two different tokens.
Use a '\' to escape the spaces like this: /media/sda3/My\ Documents". Tab completion is your friend here.

-- 
Mitch

---

