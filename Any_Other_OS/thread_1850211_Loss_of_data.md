---
title: "Loss of data"
date: 2011-09-26
forum: Any Other OS
---

### Post by roger3000 on 2011-09-26
Hi, 

I run Linux Mint 9 KDE 4 on a Dell laptop.

I had an issue after backuping my ~/Documents/ folder with Back In Time (GUI for grsync if I am correct).

Now, I have the folder tree in both my source and destination, but no file in any of the folders. 
A right click - Properties on my ~/Documents/ (source) gives me a size of 90+Go, suggesting the data are still there, somewhere... but where??

```
 
~ $ mount
/dev/sda7 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/dev/sda5 on /home type ext4 (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
/home/manu/.Private on /home/manu type ecryptfs (ecryptfs_check_dev_ruid,ecryptfs_sig=32bff7b67516cf5d,ecryptfs_fnek_sig=f5d8bf828c4a63e4,ecryptfs_cipher=aes,ecryptfs_key_bytes=16,ecryptfs_unlink_sigs)
/dev/sdb1 on /media/ito type ext4 (rw,nosuid,nodev,uhelper=hal)

```

Many thanks for your help!!

---

### Post by hyper2hottie on 2011-09-26
Just an idea.  What happens if you cd into a directory and run "ls -a".  Maybe it somehow changed all your files to hidden.

---

### Post by Perfect Storm on 2011-09-26
Moved to Other OS/Distro Talk.

---

### Post by roger3000 on 2011-09-26
> **hyper2hottie said:**
> Just an idea.  What happens if you cd into a directory and run "ls -a".  Maybe it somehow changed all your files to hidden.

Hi, 

Thanks for the tip. 

I did not mention that Showing hidden files did not change a thing: 
```
~ $ cd /home/Documents/Personnel/Eloise/Barbapapa
```(in which my daughter had the complete anime collection :) )
```
~/Documents/Personnel/Eloise/Barbapapa $ ls -a
.  ..


```
ie: empty folder ...:mad:

---

### Post by mips on 2011-09-26
Don't write or install anything to that drive. You can still recover the data. Install testdisk/photrec on another machine and transfer the hard drive to that machine and recover it on there.

---

### Post by roger3000 on 2011-09-27
> **mips said:**
> Don't write or install anything to that drive. You can still recover the data. Install testdisk/photrec on another machine and transfer the hard drive to that machine and recover it on there.
Hi, 
Thanks for your help, 

I'll try that :)

I might have a clean backup from few weeks ago, so I think there is only a limited loss of data...

---

