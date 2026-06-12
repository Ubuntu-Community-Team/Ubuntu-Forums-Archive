---
title: "chown from root to user in root mounted disk not working"
date: 2007-10-23
forum: Absolute Beginner Talk
---

### Post by renegade_0503 on 2007-10-23
I recently installed a FAT32 PATA HDD for storage-only on my dual boot system (Feisty + XP). The system boots up from the first SATA HDD. My problem is I am unable to change the user and group setting of the files on the PATA disk from root to my user name. 

This is what I have tried so far:

1. manually mount disk such that: allow all users can read/write 
sudo mount /dev/sda1 /root/temp_device/dev1 -t vfat -o charset=utf8, umask=000

2. cd /root/temp/dev1
ls -l file1.txt 
-rwxrwxrwx 4 root root 11970 2007-10-21 10:36 file1.txt

3. Change ownership from root to my user name (user_a)
sudo chown user_a:user_a file1.txt

The message I get is: "chown: changing ownership of 'file1.txt': Operation not permitted"

How to change the ownership of user and group to user_a? What is the umask value in the mount command to set permissions to: rwxr-xr-x (755)?

---

### Post by kidders on 2007-10-24
FAT filesystems don't support ownership & access control, so trying to "chown" files in one has no meaning. In such circumstances, Linux typically makes the user that mounted the filesystem appear to be the owner of anything in it, for convenience.

---

