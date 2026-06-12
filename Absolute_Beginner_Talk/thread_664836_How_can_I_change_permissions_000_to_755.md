---
title: "How can I change permissions 000 to 755 ?"
date: 2008-01-11
forum: Absolute Beginner Talk
---

### Post by Me! on 2008-01-11
Hi all

I have a directory with 000 permissions on the server !

I used (as a root):
```
chmod 755 DIR
```

but is not work !!

How can I change it ?

Thank you

---

### Post by disturbedite on 2008-01-11
maybe you made a typo, check the command carefully.

---

### Post by geirha on 2008-01-11
What filesystem is the directory on?

---

### Post by Me! on 2008-01-11
> **disturbedite said:**
> maybe you made a typo, check the command carefully.

Thank you , but I retype it many time !!

---

### Post by Me! on 2008-01-11
> **geirha said:**
> What filesystem is the directory on?

How can I know ?

---

### Post by taurus on 2008-01-11
Where does that DIR locate?  What is the mount point of that DIR?

```
df -h
sudo fdisk -l
```

---

### Post by Martin Witte on 2008-01-11
> **Me! said:**
> Hi all

I have a directory with 000 permissions on the server !

I used (as a root):
```
chmod 755 DIR
```

but is not work !!

How can I change it ?

Thank you

Please bear in mind that Unix/Linux is case sensitive - 'DIR' and 'dir' are different directories; and that you must have sufficient privileges to change the permissions, maybe you need to access root privileges with ```
sudo chmod 755 dir
```

---

### Post by Me! on 2008-01-11
> **taurus said:**
> Where does that DIR locate?  What is the mount point of that DIR?

```
df -h
sudo fdisk -l
```
```

df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/vzfs             62914560  60454700   2459860  97% /
/tmp                  62914560  60454700   2459860  97% /var/tmp

sfdisk -l
cannot open /proc/partitions
```

it is under user dir /home/user/www/vb
vb is 000

---

### Post by geirha on 2008-01-11
```
stat -f DIR
``` should show which filesystem it is on, but seeing that the dir is in your homedir, it's more or less answered.

However, the error you got running "sfdisk -l" (which should have been "sudo fdisk -l") is a bit alarming. Have you run chmod with the -R option, and with sudo or as root, prior to trying to change this dir's permissions?

Could you paste the error message you get when you run chmod 755 on the dir (/home/user/www/vb)?

---

### Post by Me! on 2008-01-11
> **geirha said:**
> ```
stat -f DIR
``` should show which filesystem it is on, but seeing that the dir is in your homedir, it's more or less answered.

However, the error you got running "sfdisk -l" (which should have been "sudo fdisk -l") is a bit alarming. Have you run chmod with the -R option, and with sudo or as root, prior to trying to change this dir's permissions?

Could you paste the error message you get when you run chmod 755 on the dir (/home/user/www/vb)?

 File: "vb"
    ID: 0        Namelen: 255     Type: UNKNOWN (0x565a4653)
Blocks: Total: 15728640   Free: 610486     Available: 610486     Size: 4096
Inodes: Total: 5000000    Free: 4559275 

error message is:
```
chmod: changing permissions of `vb': Operation not permitted
```

thank you

---

### Post by Me! on 2008-01-12
what can I do ?

---

### Post by geirha on 2008-01-12
There's something seriously wrong with that filesystem. This could mean you just have an error in that filesystem, but it can also mean your harddrive is about to crash, or possibly your memory is corrupt. 

You should try booting the ubuntu CD, then run ```
sudo fdisk -l
``` in a terminal, and run fsck on all linux-partitions. For example, if /dev/sda1 is listed as a linux-partition, run ```
sudo fsck /dev/sda1
``` (fsck is short for filesystem check)

If it gives you any errors, post them here.

---

