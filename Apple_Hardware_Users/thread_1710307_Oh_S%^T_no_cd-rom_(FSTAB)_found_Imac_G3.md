---
title: "Oh S%^T no cd-rom (FSTAB) found Imac G3"
date: 2011-03-19
forum: Apple Hardware Users
---

### Post by snafu006 on 2011-03-19
Oh S%^T no cd-rom found Imac G3 so yep i just now found out the cdrom is now mounting tryed sudo mount /dev/cdrom i get> snafu@Linksys:~$ sudo mount /dev/cdrom
mount: can't find /dev/cdrom in /etc/fstab or /etc/mtab  and i tryed sudo mount /dev/scd1 same thing so i went and got fstab file and it showing this > cat /etc/fstab /etc/mtab
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/hda3 during installation
UUID=6c30b5f1-c5b9-46ed-895b-e27f5f1b43fd /               ext4    errors=remount-ro 0       1
# swap was on /dev/hda4 during installation
UUID=bc3b653e-ea2f-4d9e-bb98-0a19542aab4f none            swap    sw              0       0
# /dev/scd0 /media/cdrom0 udf,iso9660 user,noauto 0 0
/dev/hda3 / ext4 rw,errors=remount-ro 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
none /sys sysfs rw,noexec,nosuid,nodev 0 0
none /sys/fs/fuse/connections fusectl rw 0 0
none /sys/kernel/debug debugfs rw 0 0
none /sys/kernel/security securityfs rw 0 0
none /dev devtmpfs rw,mode=0755 0 0
none /dev/pts devpts rw,noexec,nosuid,gid=5,mode=0620 0 0
none /dev/shm tmpfs rw,nosuid,nodev 0 0
none /var/run tmpfs rw,nosuid,mode=0755 0 0
none /var/lock tmpfs rw,noexec,nosuid,nodev 0 0
none /lib/init/rw tmpfs rw,nosuid,mode=0755 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,noexec,nosuid,nodev 0 0
gvfs-fuse-daemon /home/snafu/.gvfs fuse.gvfs-fuse-daemon rw,nosuid,nodev,user=snafu 0 0This is not right lol what can i do?

---

### Post by snafu006 on 2011-03-20
*bump*

---

### Post by rockhopper on 2011-03-20
Either specify a mount-point: ```
sudo mount /dev/cdrom /home/user/cdmount/
``` or add a line to /etc/fstab. My /etc/fstab shows:

```
/dev/cdrom        /media/cdrom0           udf,iso9660 user,noauto                 0       0
```

---

### Post by snafu006 on 2011-03-23
Still Not mounting i can hear the drive spin up as soon as i type but its still not working what next.
sudo mount /dev/cdrom /home/user/cdmount/

---

### Post by snafu006 on 2011-03-23
Can someone just give me there full cat /etc/fstab /etc/mtab file please thankyou

---

### Post by rockhopper on 2011-03-23
> **snafu006 said:**
> Still Not mounting i can hear the drive spin up as soon as i type but its still not working what next.
sudo mount /dev/cdrom /home/user/cdmount/

What kind of an error do you get?

---

