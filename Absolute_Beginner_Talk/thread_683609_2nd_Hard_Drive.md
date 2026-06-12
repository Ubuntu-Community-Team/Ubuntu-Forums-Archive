---
title: "2nd Hard Drive"
date: 2008-01-31
forum: Absolute Beginner Talk
---

### Post by siresam88 on 2008-01-31
after windows corrupting for the nth time i have decided to try another Ubuntu out.. 

Will i be able to keep my 2nd drive in the pc or will the data get deleted with the installation ? 

would it be best for the install to take out the 2nd drive and then insert it after ?

Sam

---

### Post by taurus on 2008-01-31
Your data on second harddrive should be safe as long as you don't tell the installer to install Ubuntu on it or format it during the installing process.  No need to remove it.  But if you want to be real safe, remove it if you wish.  Then, reconnect it later and then add an entry in /etc/fstab so it would be mounted automatically each time you boot Ubuntu.

---

### Post by hyper_ch on 2008-01-31
it will be deleted if you say it should delete it.... if you don't say so (and don't select any such option - be careful there) it will not be deleted

Just to be 100% sure, just unplug the second drive... that way it can't be harmed at all...

---

### Post by kpkeerthi on 2008-01-31
Well... In the installation wizard, when you reach to the point of partitioning the disk, just make sure that you do not choose to format your second partition. Optionally, give it some meaningful mountpoint like /media/Storage so ubuntu mounts it automatically at boot. 

You can also have the disk removed and mount it later but I don't think you have to do all this.

---

### Post by siresam88 on 2008-01-31
> **taurus said:**
> Your data on second harddrive should be safe as long as you don't tell the installer to install Ubuntu on it or format it during the installing process.  No need to remove it.  But if you want to be real safe, remove it if you wish.  Then, reconnect it later and then add an entry in /etc/fstab so it would be mounted automatically each time you boot Ubuntu.


Ok so how would i add an entry then ? is that relativly straight forward ?

---

### Post by taurus on 2008-01-31
> **siresam88 said:**
> Ok so how would i add an entry then ? is that relativly straight forward ?

Should be real easy.  You just need to know what filesystem that second drive is and where you want to mount it.  Then, it would look something like

ntfs filesystem:
```
/dev/sdb1   /media/sdb1   ntfs-3g   defaults   0   0
```

fat32/vfat filesustem:
```
/dev/sdb1   /media/sdb1   vfat   defaults,umask=000   0   0
```

ext3 filesystem:
```
/dev/sdb1   /media/sdb1   ext3   defaults   0   1
```

---

