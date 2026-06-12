---
title: "Trouble w/ mounting smb share on boot..."
date: 2006-04-25
forum: Absolute Beginner Talk
---

### Post by echo $USER on 2006-04-25
For some reason I get an access denied message when I enter my passwd to mount my samba share on boot.  But if I run sudo mount -a and enter my sudo and smbpasswd in the terminal it will mount correctly.  Can anyone help me out?  Thanks.  Here is my /etc/fstab and /etc/mtab:

# /etc/fstab: static file system information.
#/dev/hda2 / ext3 rw,errors=remount-ro 0 0
proc /proc proc rw 0 0
sysfs /sys sysfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
tmpfs /dev/shm tmpfs rw 0 0
usbfs /proc/bus/usb usbfs rw 0 0
tmpfs /lib/modules/2.6.12-10-386/volatile tmpfs rw,mode=0755 0 0
tmpfs /dev tmpfs rw,size=10M,mode=0755 0 0
//192.168.0.2/Media /mnt/media smbfs rw 0 0

This is my /etc/mtab after running "sudo mount -a"

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda1       /media/hda1     ntfs    noauto,nls=utf8,umask=0222     0       0/dev/hda3       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
//192.168.0.2/Media   /mnt/media      smbfs   nls=utf8,umask=0222  0     0

---

### Post by echo $USER on 2006-04-26
anybody?

---

### Post by echo $USER on 2006-04-26
somebody?

---

### Post by auroraborealis on 2006-04-26
Just throwing this out because I don't use Samba, but maybe mount is happening before networking is set up. Someone with better knowledge of the boot sequence could maybe answer.

---

### Post by echo $USER on 2006-04-26
Mounting remote filesysystems happens after networking interface is configured and started.

i was reading [this]("http://kim.biyn.com/Linux/how_to_mount_samba_windows_shares_at_boot_time_via_fstab"),
 and i think the problem is im putting in the wrong passwd.  I was using my smbpasswd when it requires my windows passwd.  I'll try it when i get home and see if that is the answer.

---

