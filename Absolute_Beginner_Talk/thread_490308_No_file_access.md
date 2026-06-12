---
title: "No file access"
date: 2007-07-02
forum: Absolute Beginner Talk
---

### Post by notbitmonk on 2007-07-02
I have two hard disks, 1 SATA and 1 PATA.  The SATA hard disk contains XP (90 gb partition) and Kubuntu (20 GB partition) and the PATA contains my data files (work and entertainment).  The PATA drive is NTFS.  Several days ago I installed the two OSs (again) but this time Kubuntu did not recognize the PATA drive automatically.  I went to System Settings | Advanced | Drives and Filesystems, entered in Administration Mode and added the drive with a mount point located in /media/DataDrive.  I also enabled it to automatically mount on startup.  My problem is that when I try to access the drive, on error message says that I do not have permission to read the drive.  If I look into properties, it says that the owner is root and users and groups are forbidden (to read and write to the disk).  In my previous installation, I didn't have trouble accessing this drive, how can I get access to the drive now?

---

### Post by Raineer on 2007-07-02
Sort of a stab in the dark, but can you verify ntfs-config is installed?  If not, follow [this]("http://ubuntuforums.org/showthread.php?t=217009") thread.

---

### Post by Malta paul on 2007-07-02
hi, It might be a good idear to check if your disk is recognized by your system. >applications>terminal then type 'sudo fdisk -l "  
With NTFS format you can read or copy file, to wite you need Ntfs-3g
this my help  you [http://psychocats.net/ubuntu/index](http://psychocats.net/ubuntu/index) 
Good luck ;)

---

### Post by notbitmonk on 2007-07-02
The disk is recognized as I can see it from the Disk and Filesystems window (it even tells me how much of the disk is used and the partition type).  My only problem is getting the permissions to get into the disk.

---

### Post by Outrunner on 2007-07-02
I'm not very good with permission problems but I think this should do it:

```
sudo chmod 755 /media/DataDrive
```

---

### Post by meborc on 2007-07-02
can you post your /etc/fstab file?

i strongly suggest though, that you install the ntfs-config package and set up access to your ntfs partitions from it!

---

### Post by notbitmonk on 2007-07-02
I can show you the contents tomorrow as the computer is a different one.  If the ntfs-config package needs to be downloaded, I'm out of luck as the computer is in a location without internet access (unless I can download it now and take to the computer tonight).  Outrunner, I'll also try your suggestion tonight. Thanks.

---

### Post by notbitmonk on 2007-07-05
Contents of fstab:
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc /proc proc defaults 0 0
# /dev/sda2
UUID=973c7b16-afe4-4f61-ac74-bd7373b20c97 / ext3 nouser,defaults,errors=remount-ro,atime,auto,rw,dev,exec,suid 0 1
# /dev/sda5
UUID=b05ae57d-2766-473b-929a-f1f0333e3e7c none swap sw 0 0
/dev/hdd /media/cdrom0 udf,iso9660 user,atime,noauto,rw,dev,exec,suid 0 0
/dev/hdc /media/cdrom1 udf,iso9660 user,atime,noauto,rw,dev,exec,suid 0 0
/dev/hda1 /media/DataDrive auto nouser,atime,auto,rw,nodev,noexec,nosuid 0 0

I believe that auto *nouser,atime,auto,rw,nodev,noexec,nosuid* are groups that control access.  I tried changing it to reflect the groups from the cdrom but I do not have write access to the file (changing to user, suid and dev instead of nouser, nosuid and nodev).  Although I have no idea of what those groups are, I believe that by changing them I'll have at least read access until I can download the Ntfs-3g.

---

### Post by notbitmonk on 2007-07-05
bump

---

### Post by notbitmonk on 2007-07-05
bump

---

