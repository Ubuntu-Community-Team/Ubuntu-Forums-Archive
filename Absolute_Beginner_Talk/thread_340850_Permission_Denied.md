---
title: "Permission Denied"
date: 2007-01-17
forum: Absolute Beginner Talk
---

### Post by mgaskell on 2007-01-17
Hello All,

I am new to Linux - trying to cure a Windows addiction.

I have installed Ubuntu Edgy on a partition on my laptop. Everything boots fine in this dual boot configuration.

I was attempting to install beagle and it was recommended that I set extended attributes to my ext3 file system. I cannot do this because I keep getting a "permission denied" error using the terminal. Here is a sample:

mike@mike-laptop:~$ /etc/fstab
bash: /etc/fstab: Permission denied
mike@mike-laptop:~$ /dev/hda3
bash: /dev/hda3: Permission denied
mike@mike-laptop:~$ /dev/hda1
bash: /dev/hda1: Permission denied

I thought this had something to do with beagle so I removed the app from my system. This did not solve the problem.

Any help getting this error fixed and walking me through the process of setting extended attributes greatly appreciated.

Thanks,
Mike

---

### Post by taurus on 2007-01-17
You need to open it with an editor, and of course, you need to be root to edit system file so

```
gksudo gedit /etc/fstab
```

p.s.  I hope you know what you are doing with /etc/fstab because if you put in a wrong value, you won't be able to boot your machine!

---

### Post by riven0 on 2007-01-17
Anything requiring administrative previleges needs to be done with sudo. So instead of doing **gedit /etc/fstab** you'll need to do **sudo gedit /etc/fstab**

---

### Post by ComplexNumber on 2007-01-17
> **riven0 said:**
> Anything requiring administrative previleges needs to be done with sudo. So instead of doing **gedit /etc/fstab** you'll need to do **sudo gedit /etc/fstab**
for gedit, its best to use gksudo instead of sudo.

---

### Post by aysiu on 2007-01-17
Read this. It'll help.
[http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions)

---

### Post by TheRingmaster on 2007-01-17
just install automatix2 from here [Installation - Automatix Wiki]("http://www.getautomatix.com/wiki/index.php?title=Installation")

automatix2 will install beagle for you

---

### Post by mgaskell on 2007-01-18
Thanks all for the quick reply!

I got into the file using gksudo gedit but after reading the reply by taurus, I'm afraid to touch it without guidance. Here is what I got from the beagle-project.org site to set extended attributes:

"To set extended attributes, you should add the user_xattr property to the relevant file systems in your /etc/fstab file. For example:

/dev/hda3     /home     ext3     defaults,user_xattr     1 2

You can then remount the affected partitions as follows:

# mount -o remount /home"

Here is what my fstab file currently looks like:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda3
UUID=ab3b4834-2ec0-46fb-8948-e02dbfc8e705 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda1
UUID=01C1F28D4748654D /media/hda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/hda4
UUID=54939963-cfe3-4420-91e0-7533aab19be1 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

If I replace the "defaults,errors=remount-ro 0       1" under the "# /dev/hda3" line with "defaults,user_xattr     1 2"  will this set extended attributes without screwing anything else up?

Thanks again for working with a rookie.

Mike

---

