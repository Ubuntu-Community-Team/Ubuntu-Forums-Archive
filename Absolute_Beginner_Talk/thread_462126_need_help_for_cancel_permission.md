---
title: "need help for cancel permission"
date: 2007-06-02
forum: Absolute Beginner Talk
---

### Post by sindbad_x on 2007-06-02
[SIZE="4"]Hi Brothers

I have Ubuntu 6.10

i found permission on all my drives and my folders, i can't copy or can or delete

when i entered on **[COLOR="Red"]root[/COLOR]** and write 

[COLOR="Blue"]chmod ug+rwx /media/hdb5/desk[/COLOR]

that is folder that i wanna to cancel permission on it, I  found this messagfe

[COLOR="Blue"]chmod: changing permissions of '/media/hdb5/desk' :read-only file system[/COLOR]

Please any one told me what can i doooo 

thx
[/SIZE]

---

### Post by taurus on 2007-06-02
What filesystem is /dev/hdb5 and what's up with the large font size?

Applications -> Accessories -> Terminal
```
sudo fdisk -l
df -h
```

---

### Post by sindbad_x on 2007-06-02
my drive is NTFS

what u mean this code?

is it mean fdisk (mean  format partition) or only cancel permission only

---

### Post by taurus on 2007-06-02
You cannot write to ntfs filesystem unless you use ntfs-3g.  Have you installed ntfs-3g and how do you mount /dev/hdb5?  Which release (Dapper, Edgy, or Feisty) are you running right now?  Do you mount it through /etc/fstab?

Post the output of these codes from a terminal here.

```
sudo fdisk -l
cat /etc/fstab
```

---

### Post by sindbad_x on 2007-06-02
forgive me coz it's my firist install Linux ubuntu

i don't wanna format my partition, it's all my hard

hdb5 size ----  65 G

i don't install  ntfs-3g and i don't know how??

there's my /etc/fstab

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hdb1
UUID=2a12292a-1ab2-41b8-8903-b1febea69197 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hdb5
UUID=13259F9E6BCF3169 /media/hdb5     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/hdb3
UUID=54380c6b-b11a-426b-8570-448579d7f8ae none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto 

My ver

Ubuntu 6.10 Edgy

and plz tell me what is mean of 

sudo fdisk -l
cat /etc/fstab

is it mean delete my partition or change it and my data save.

thx for help

---

### Post by taurus on 2007-06-02
If you want to write to /dev/hdb5, you must use ntfs-3g driver instead of ntfs since ntfs driver only allows to read from it.

Here's a link for you to look at.

[https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G](https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G)

---

### Post by sindbad_x on 2007-06-02
> **taurus said:**
> If you want to write to /dev/hdb5, you must use ntfs-3g driver instead of ntfs since ntfs driver only allows to read from it.

Here's a link for you to look at.

[https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G](https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G)

thx u for ur help, i made it

thxx

---

