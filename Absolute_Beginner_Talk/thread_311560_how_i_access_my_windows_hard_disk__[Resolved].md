---
title: "how i access my windows hard disk ? [Resolved]"
date: 2006-12-03
forum: Absolute Beginner Talk
---

### Post by tiptip on 2006-12-03
Hello,

From the menu.lst file i know it is on /dev/sda2  but how i access it ?
i also know i need to use "mount -t" but it does work :(
(it is SATA drive with NTFS on it)

---

### Post by atoponce on 2006-12-03
You need to create a folder or partition to tell the system "where" to access the data.  Something like:

```
sudo mkdir /windows
```From there, aysiu put a good tutorial on his site about mounting Windows drive.  You can find that [tutorial here]("http://www.psychocats.net/ubuntu/mountwindows.php").

A word of note, though.  By default, you will not be able to write to an NTFS drive.  You can however write to any FAT* partition.

---

### Post by turbojugend_gr on 2006-12-03
Type the following in a terminal, after each command you need to press enter. I will try to expalin what you did there, the explanations are starting with an asterisk.

```

cp /etc/fstab ~/fstab_bak *we create a backup of the file we are gonna mess with.
sudo gedit /etc/fstab *we open gedit text editor with root priviledges.

```

Now there add the following line:
```

dev/sda2 /winxp   ntfs    defaults,nls=utf8,umask=007,gid=46 0       1

```

now again in a terminal issue the command "sudo mount -a" to remount all drives in fstab. You can now access your drive in /winxp, or whatever you changed that with.
This file (fstab) is the one that tells Linux which drives to mount upon start up, how and where. If you don't wish to mount your windows partition on start up, say so I 'll hit back with the mount command.

Let me know how it did.

---

### Post by tiptip on 2006-12-03
> **turbojugend_gr said:**
> Type the following in a terminal, after each command you need to press enter. I will try to expalin what you did there, the explanations are starting with an asterisk.

```

cp /etc/fstab ~/fstab_bak *we create a backup of the file we are gonna mess with.
sudo gedit /etc/fstab *we open gedit text editor with root priviledges.

```

Now there add the following line:
```

dev/sda2 /winxp   ntfs    defaults,nls=utf8,umask=007,gid=46 0       1

```

now again in a terminal issue the command "sudo mount -a" to remount all drives in fstab. You can now access your drive in /winxp, or whatever you changed that with.
This file (fstab) is the one that tells Linux which drives to mount upon start up, how and where. If you don't wish to mount your windows partition on start up, say so I 'll hit back with the mount command.

Let me know how it did.

```
$ sudo mount -a
mount: mount point /winxp does not exist
```
:(

---

### Post by yabbadabbadont on 2006-12-03
Did you forget to run "sudo mkdir /winxp" first?  ;)

---

### Post by tiptip on 2006-12-03
oh 

lol :oops: 

/hide :-$ 

it's working fine now \\:D/ 
thx guys

---

