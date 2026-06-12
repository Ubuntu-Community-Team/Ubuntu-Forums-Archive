---
title: "Can't automount windows share"
date: 2007-11-20
forum: Absolute Beginner Talk
---

### Post by bowens44 on 2007-11-20
I am trying to use fstab to automount some windows shares but can't get it to work. If I go to 'storage media' in dolphin, I see the share but it isn't mounted. If I 'sudo mount /home/backups' it mounts and is accessible. This is my fstab file:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=98ca1978-9d74-4fba-8a82-97f99fd38651 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=26d20293-3e17-48b0-ae2c-d91140cfbaea none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/hdc        /media/cdrom1   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0
#windows shares
//192.168.5.100/linux_bkups /home/backups smbfs rw,credentials=/etc/samba/smb.auth 0 0


smb.auth is :
username=myusername
password=mypassword

---

### Post by MegaJim on 2007-11-20
this probably happens because the mount is happening before the network is active, you could try to add the auto option and see if it helps

---

### Post by bowens44 on 2007-11-20
> **MegaJim said:**
> this probably happens because the mount is happening before the network is active, you could try to add the auto option and see if it helps

Unfortunately , no help.

---

### Post by MegaJim on 2007-11-20
In that case it is probably best to mount your filesystem using cifs, there's a guide on how to do this here: [http://ubuntuforums.org/showthread.php?t=288534&highlight=mount+samba](http://ubuntuforums.org/showthread.php?t=288534&highlight=mount+samba)

---

### Post by bowens44 on 2007-11-20
I have made some progress but something is still not quite right. At least I think it's not quit right. I am now able to mount all shares at boot with cifs in my fstab file. However, I expected to see an icon the desktop for the shares. There isn't one. i noticed that when I was modifying the fstab file, I would save it after I added each share and then the icons for the shares would appear on the desktop. I like the icons, is there something I have to do to ensure that they are created?

---

### Post by Inxsible on 2007-11-20
Unless you mount the drives/shares under /media, they will not get desktop icons. Where have you mounted them?

---

### Post by bowens44 on 2007-11-20
> **Inxsible said:**
> Unless you mount the drives/shares under /media, they will not get desktop icons. Where have you mounted them?

They are mounted as /media/data /media/mp3s and /media/backups but no icons are on the desktop.

---

