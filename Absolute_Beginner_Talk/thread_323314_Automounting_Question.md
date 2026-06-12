---
title: "Automounting Question"
date: 2006-12-21
forum: Absolute Beginner Talk
---

### Post by monkeymonkeymonkey on 2006-12-21
My media card reader only works if i restart and log in gnome with the card inserted. It doesn't work when I log into a XGL session or without the card inserted on restart. I found out that my reader is /dev/sdd1. I'm looking for help to edit my fstab file to get the media reader to always mount on startup no matter what session I choose or if i had the SD card inserted.

My /ect/fstab
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=9c4ed634-4a74-41d6-bfcb-b70c4fe64986 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=082CC9522CC93C06 /media/sda1     ntfs    user,noauto,nls=utf8,umask=007,gid=46 0       1
# /dev/sda5
UUID=f584bd9a-038a-46de-85c6-eb9950dce955 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto     0       0

```

My /etc/mtab
```

/dev/sda2 / ext3 rw,errors=remount-ro 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
/sys /sys sysfs rw,noexec,nosuid,nodev 0 0
varrun /var/run tmpfs rw,noexec,nosuid,nodev,mode=0755 0 0
varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0
procbususb /proc/bus/usb usbfs rw 0 0
udev /dev tmpfs rw,mode=0755 0 0
devshm /dev/shm tmpfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
lrm /lib/modules/2.6.17-10-generic/volatile tmpfs rw 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw 0 0
/dev/sdd1 /media/CANON_DC vfat rw,nosuid,nodev,quiet,shortname=mixed,uid=1000,gid=1000,umask=077,iocharset=utf8 0 0

```

Thanks I have pics of my son that I want to put on my computer or upload and hate having to restart.

---

### Post by taurus on 2006-12-21
Open a terminal, Applications -> Accessories -> Terminal, and open a text editor.

```
gksudo gedit /etc/fstab
```
Then, add this line to the end of it.

```

/dev/sdd1   /media/CANON_DC   vfat   iocharset=utf8,umask=000   0   0

```
Reboot and it should be mounted automatically...

---

### Post by ahaurw01 on 2006-12-21
I had a similar problem with a usb external drive and usb flash drives. What worked for me was to check the boxes for 'mount removable drives' and 'mount removable media' in Preferences > Removable drives and media preferences (in GNOME, not sure if it's the same in your xubuntu). Originally I put entries in my fstab file, but realized if I just deleted them (or commented out with '#' just to play it safe) they would mount automatically when plugged in. 

I hope this works, it sure was a pain for me to restart every time I wanted to plug in a usb keychain.

---

### Post by monkeymonkeymonkey on 2006-12-21
thanks ahaurw01 sometimes the simplest solution is the best but those boxes are checked.

I added that file to my /ect/fstab file but it doesn't automount, I can fire up a terminal and enter mount /dev/sdd1 and it will mount.
Now that its half fixed any help?

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=9c4ed634-4a74-41d6-bfcb-b70c4fe64986 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=082CC9522CC93C06 /media/sda1     ntfs    user,noauto,nls=utf8,umask=007,gid=46 0       1
# /dev/sda5
UUID=f584bd9a-038a-46de-85c6-eb9950dce955 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/sdd1	/media/CANON_DC vfat	iocharset=utf8,umask=000   0   0

```

---

### Post by taurus on 2006-12-22
Did you mount it with this command after you modified your /etc/fstab?

```
sudo mount -a
```

---

