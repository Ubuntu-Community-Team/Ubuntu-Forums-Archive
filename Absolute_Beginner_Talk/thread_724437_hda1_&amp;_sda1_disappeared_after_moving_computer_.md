---
title: "hda1 &amp; sda1 disappeared after moving computer to a new location"
date: 2008-03-14
forum: Absolute Beginner Talk
---

### Post by neoMAX on 2008-03-14
I unhooked my computer and took it to my mom's place and now my other partitions/drives are gone in ubuntu!

Here's what's in fstab:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda5
UUID=ff731372-c018-4a16-ba1b-8e35d5037ad3 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda1
UUID=F228999728995B83 /media/hda1     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda5
UUID=9AF86C363922A3FE /media/sda5     ntfs    defaults,umask=007,gid=46 0       1
# /dev/hda6
UUID=5bad15f0-50f0-41c7-8791-8f26e0b09746 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0
```

They're there (above) but I don't see them in the file browser and my backgrounds/mp3s from sda5 aren't working :(

Please help!

---

### Post by neoMAX on 2008-03-14
Oh, by the way, I booted XP last night and it worked, then I booted ubuntu this morning, they were there, then I shut down and took my computer to my mom's and set it back up, and they're gone...

---

### Post by Oldsoldier2003 on 2008-03-14
> **neoMAX said:**
> I unhooked my computer and took it to my mom's place and now my other partitions/drives are gone in ubuntu!

Here's what's in fstab:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda5
UUID=ff731372-c018-4a16-ba1b-8e35d5037ad3 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda1
UUID=F228999728995B83 /media/hda1     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda5
UUID=9AF86C363922A3FE /media/sda5     ntfs    defaults,umask=007,gid=46 0       1
# /dev/hda6
UUID=5bad15f0-50f0-41c7-8791-8f26e0b09746 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0
```

They're there (above) but I don't see them in the file browser and my backgrounds/mp3s from sda5 aren't working :(

Please help!
check the phyical hard drive connections. you may have jostled something loose on the trip.

---

### Post by neoMAX on 2008-03-14
> **Oldsoldier2003 said:**
> check the phyical hard drive connections. you may have jostled something loose on the trip.

They are connected properly. The BIOs recognizes them, and I'm booting from them. :(

---

### Post by Diabolis on 2008-03-14
For some reason your partitions aren't mounting automatically, juts do
```
sudo mount /media/sda#
```

add the "auto" option to your partitions.

---

### Post by neoMAX on 2008-03-14
Okay, I typed that in terminal, and here's what I get:

```

$LogFile indicates unclean shutdown (0, 0)
Failed to mount '/dev/sda5': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the 'Safely Remove Hardware' icon in the Windows
          taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/sda5 /media/sda5 -o force

    Or add the option to the relevant row in the /etc/fstab file:

            /dev/sda5 /media/sda5 ntfs-3g defaults,force 0 0


```

I do have windows, but this sata drive is my media drive and I do not have a backup of it. It's very important that I do not mess it up. What should I do next?

I guess I did do an unclean shutdown. I just held the power down this morning...

---

### Post by Diabolis on 2008-03-14
I recommend you to backup your files and chage the file system of your partition from ntfs to fat32, its is more compatible with linux.

---

### Post by tubunu on 2008-03-14
I've had a similar issue recently, whereas I could see my partitions in fstab, but they weren't showing up. So after failing to mount them with the mount command, I followed the advice I got there:

```
mount -t ntfs-3g /dev/sda5 /media/sda5 -o force
```

(where you substitute the partition number for the one you got) Works immediately and after logging out and back in, both partitions showed up. Good luck.

---

### Post by neoMAX on 2008-03-14
Okay, I'll give -force a whirl... Wish me luck :( I really don't wanna lose my data

---

