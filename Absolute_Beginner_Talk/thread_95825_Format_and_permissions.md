---
title: "Format and permissions"
date: 2005-11-27
forum: Absolute Beginner Talk
---

### Post by jriff on 2005-11-27
Hi All!

I have created a new partition on my disk, entered it into fstab to mount in /home/[user]/desktop/part3. Then I did a "sudo mkfs -t ext3 /dev/hda3". So far so good. Now, when I try to access my new mount point I get "Access denied". I can see that it reads "root" two times when I do a "ls -l". What have I done wrong :confused: 

- Jacob

BTW.: What is /proc?

---

### Post by ssam on 2005-11-27
in the options section of the fstab you can put "user" (dont change that yo your username), to give something like this
```

/dev/hda3     /home/[user]/desktop/part3   ext3     user    0  0
```

then a normal user should be able to mount it.

you may then need to use
```
sudo chown -R [user]:[user] /home/[user]/desktop/part3
```
to change the ownership to you (do change those [user]s to your username)

> 
The /proc file system really shows the power of the Linux Virtual File System. It does not really exist (yet another of Linux's conjuring tricks), neither the /proc directory nor its subdirectories and its files actually exist. So how can you cat /proc/devices? The /proc file system, like a real file system, registers itself with the Virtual File System. However, when the VFS makes calls to it requesting inodes as its files and directories are opened, the /proc file system creates those files and directories from information within the kernel. For example, the kernel's /proc/devices file is generated from the kernel's data structures describing its devices.

The /proc file system presents a user readable window into the kernel's inner workings. Several Linux subsystems, such as Linux kernel modules described in chapter  modules-chapter, create entries in the the /proc file system. 
from [http://www.tldp.org/LDP/tlk/fs/filesystem.html](http://www.tldp.org/LDP/tlk/fs/filesystem.html)

---

### Post by jriff on 2005-11-27
That's great! Thanks for that detailed explanation! That /proc dir. seems pretty smart - I'll have a closer look at it.

---

### Post by ssam on 2005-11-27
thanks for saying thanks.

it makes me happy and want to help more.

have fun with linux.

---

