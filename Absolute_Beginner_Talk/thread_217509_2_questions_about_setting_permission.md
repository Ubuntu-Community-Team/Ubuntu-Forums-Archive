---
title: "2 questions about setting permission"
date: 2006-07-17
forum: Absolute Beginner Talk
---

### Post by gargoyle on 2006-07-17
2 questions about setting permission
I created a group of folder to access my partitions. I used the same setting in the fstab for each folder but some how one of the is different then the other. 

(1) How do you view the permission for a single directory?
I would like to view just the permission for the following
**/home/ed100/fat_g**

I know that I can use **ls -l**to list permission for the current directory. However why can I not use the following to view only one directory
**ls -l fat_c**

(2) How would I change the permission on directory **fat_c**
Would I just use the following 
chmod 755 fat_c

Do have to unmount the directory first to do this?

---

### Post by ProjectGod on 2006-07-17
utilities in linux assume - without any parameters included - and look in the "." ... which is basically the current directory... so you have to use an absolute path e.g. 

ls -l /home/ed100/fat_c

if you hate typing out long directory structures... use the [tab] key on your keyboard to complete the directories / files

once again absolute paths are used... for perm changing

sudo chmod 775 /home/ed100/fat_c

---

### Post by geco on 2006-07-17
> **gargoyle said:**
> 2 questions about setting permission
I created a group of folder to access my partitions. I used the same setting in the fstab for each folder but some how one of the is different then the other. 

Folders and partitions *aren't* the same thing, so you should specify if you want to manage just folders (so you can use "chmod") in linux partitions or partitions (such as FAT) in your Linux box.

> **gargoyle said:**
> 
(1) How do you view the permission for a single directory?
I would like to view just the permission for the following
**/home/ed100/fat_g**

I know that I can use **ls -l**to list permission for the current directory. However why can I not use the following to view only one directory
**ls -l fat_c**

to see folders' permissions:
```

user@localhost:~$ ls -ld folder_name

```

you can specify either local or global path

> **gargoyle said:**
> 
(2) How would I change the permission on directory **fat_c**
Would I just use the following 
chmod 755 fat_c

Do have to unmount the directory first to do this?

you cannot change permissions of a partition with chmod, this will not work, you can use mount options "gid" and "uid" instead, see
```

man mount
man fstab

```
for more informations, I'm sorry but now I don't have time to explain it to you :(

---

### Post by steve.horsley on 2006-07-17
1:
**ls -ld /home/ed100/fat_g** should do the trick. If you miss out the -d, then it will show the directory contents rather than the directory itself.

2:
Be careful here. Changing the directory permissions of the mount point will not change the permissions of the mounted drive as far as I know. If the mounted drive has permissions embedded in the filesystem (as ext2/3 and reiserfs have) then those will be used. If not, then you must specify the permissions that will be applied as an option when the drive is mounted (umode option).

Here is an example from my /etc/fstab that mounts a FAT drive:
> /dev/hda9       /mnt/E     vfat    defaults,utf8,umask=007 0       1

See this page: [http://ubuntuguide.org/wiki/Dapper#Windows](http://ubuntuguide.org/wiki/Dapper#Windows)

---

### Post by aysiu on 2006-07-17
I don't believe a FAT32 partition supports *chmod*. It's all about the *umask* and how you mount it in the /etc/fstab

---

### Post by gargoyle on 2006-07-18
I solved my problem with permission.
I was trying to set the permission on the wrong partition.

Thanks for the replies.

---

