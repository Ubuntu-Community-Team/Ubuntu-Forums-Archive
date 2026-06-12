---
title: "Simple fstab question."
date: 2007-02-04
forum: Absolute Beginner Talk
---

### Post by Roasted on 2007-02-04
Whenever I boot up, my windows parition of my SATA drive mounts on my desktop. It's sda1.

How can I prevent it from doing that? I'm familiar with fstab, I just wasn't sure how to prevent it.



# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=bc849096-62a5-415a-a0c6-fddda79007cd /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=343CEEAE3CEE6A76 /media/sda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda2
UUID=27a1e042-5389-4887-b630-88989d5ca538 none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdb        /media/cdrom1   udf,iso9660 user,noauto     0       0

---

### Post by dcstar on 2007-02-04
> **Roasted said:**
> Whenever I boot up, my windows parition of my SATA drive mounts on my desktop. It's sda1.

How can I prevent it from doing that? I'm familiar with fstab, I just wasn't sure how to prevent it.



# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=bc849096-62a5-415a-a0c6-fddda79007cd /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=343CEEAE3CEE6A76 /media/sda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda2
UUID=27a1e042-5389-4887-b630-88989d5ca538 none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdb        /media/cdrom1   udf,iso9660 user,noauto     0       0

```
sudo gedit /etc/fstab
```
and comment out the line thus:
```
# /dev/sda1
#UUID=343CEEAE3CEE6A76 /media/sda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
```

---

### Post by taurus on 2007-02-04
Just change the mount point in /etc/fstab to something else like /mnt/sda1.  And of course, don't forget to create that new mount point or it won't be able to mount to it.

```
gksudo gedit /etc/fstab
```

```
sudo mkdir /mnt/sda1
```

---

### Post by Cobikegeek on 2007-02-04
Just comment out the line of code in fstab like below.

# /dev/sda1
#UUID=343CEEAE3CEE6A76 /media/sda1 ntfs defaults,nls=utf8,umask=007,gid=46 0 1

---

### Post by amohanty on 2007-02-04
In this line 
> 
UUID=343CEEAE3CEE6A76 /media/sda1 ntfs **defaults**,nls=utf8,umask=007,gid=46 0 1

replace the bold part with **user,ro**.

This will allow users to mount it and make it readonly.

HTH
AM

---

### Post by Roasted on 2007-02-04
I didn't realize I'd have to comment out the second line. I saw the line where /dev/sda1 was and it already was commented out, I was like uh, whaaat? 

Also, if it's mounted to /media/sda1, why does it appear on desktop? Or is that just how the OS works? Mounts to desktop + media?

And what's the difference between gksu gedit and sudo gedit?

---

### Post by amohanty on 2007-02-04
> **Roasted said:**
> I didn't realize I'd have to comment out the second line. I saw the line where /dev/sda1 was and it already was commented out, I was like uh, whaaat? 

Also, if it's mounted to /media/sda1, why does it appear on desktop? Or is that just how the OS works? Mounts to desktop + media?

And what's the difference between gksu gedit and sudo gedit?

No you dont have to comment out the /dev/sda1 part. if you dont want to mount it you comment out the line **after** it.

It appears on the desktop because its mounted as sata media and because of the **defaults** option in the abovementioned line.

gksu shows up a dialog to enter su passwd.
sudo does the same on the command line.

HTH
AM

---

### Post by mailbinoy on 2007-02-04
> **Roasted said:**
> I didn't realize I'd have to comment out the second line. I saw the line where /dev/sda1 was and it already was commented out, I was like uh, whaaat? 

if you comment out the line in /etc/fstab, the partition will not be mounted.
> 
Also, if it's mounted to /media/sda1, why does it appear on desktop? Or is that just how the OS works? Mounts to desktop + media?

try this to stop it showing on the desktop. I use Kubuntu, so i cant confirm this will work for you.
Applications --> System Tools --> Configuration Editor --> apps --> nautilus --> desktop; Uncheck "volumes visible."
> 
And what's the difference between gksu gedit and sudo gedit?

both gksudo and sudo are used to run a application (program) with root privileges. gksudo will ask you the password in a dialog box while sudo will ask it on the command line.

---

