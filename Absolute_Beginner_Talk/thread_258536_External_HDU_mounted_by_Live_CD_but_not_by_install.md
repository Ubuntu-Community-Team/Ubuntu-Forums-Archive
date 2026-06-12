---
title: "External HDU mounted by Live CD but not by installed Ubuntu"
date: 2006-09-16
forum: Absolute Beginner Talk
---

### Post by gertva on 2006-09-16
Hai All

I cannot figure out this: If I boot my PC from the Live CD 6.06, the exteral LaCie hard disk is found and mounted correctly (data is on an NTFS partition). 

When I start the same PC with the Ununtu I installed from the same CD, the  LaCie hard disk is found but not mounted. 

Anyone an idea how I can fix this? I'll probably be something very stupid again... 

thanks

gert


PS -- This might be helpfull:

Schijf /dev/hda: 40.0 GB, 40007761920 bytes
255 koppen, 63 sectoren/spoor, 4864 cylinders
Eenheden = cylinders van 16065 * 512 = 8225280 bytes

Apparaat Boot      Start         Einde    Blokken  Id  Systeem
/dev/hda1               1           8       64228+  de  Dell Utility
/dev/hda2   *           9        2349    18804082+   7  HPFS/NTFS
/dev/hda3            2350        4864    20201737+   f  W95 Ext'd (LBA)
/dev/hda5            2350        2731     3068383+   b  W95 FAT32
/dev/hda6            2732        2861     1044193+  82  Linux-swap / Solaris
/dev/hda7            2862        3662     6434001   83  Linux
/dev/hda8            3663        4864     9655033+  83  Linux

Schijf /dev/sda: 251.0 GB, 251000193024 bytes
255 koppen, 63 sectoren/spoor, 30515 cylinders
Eenheden = cylinders van 16065 * 512 = 8225280 bytes

Apparaat Boot      Start         Einde    Blokken  Id  Systeem
[B]/dev/sda1               1       30515   245111706    7  HPFS/NTFS
[/B]

In **BOLD** the device I'm talking about...

---

### Post by kidders on 2006-09-16
Post the contents of your /etc/fstab. Therein lies the answer :-P

---

### Post by gertva on 2006-09-16
this is it: 

[FONT="Courier New"][SIZE="1"]# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda7       /               reiserfs notail          0       1
/dev/hda1       /media/hda1     vfat    defaults,utf8,umask=007,gid=46 0       1
/dev/hda2       /media/hda2     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
/dev/hda5       /media/hda5     vfat    defaults,utf8,umask=007,gid=46 0       1
/dev/hda8       /media/hda8     reiserfs defaults        0       2
/dev/hda6       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
[/SIZE][/FONT]

---

### Post by kidders on 2006-09-16
Yip... as I suspected, there is no reference to your partition in your /etc/fstab.

If you add the following to the end of the file, things'll come alive for you. Be careful though ... one mistake can render your system unbootable!

```

/dev/sda1 /mnt/lacie ntfs ro,noexec,auto 0 0

```

Here's a step by step:

[LIST=1]
[*]Check that /dev/sda1 exists
[*]Add the above line to your /etc/fstab
[*]Do a "sudo mkdir /mnt/lacie"
[/LIST]

Now, whenever you boot your machine, the hard disk will be automatically mounted at /mnt/lacie. To save having to reboot right away, type "mount /mnt/lacie".

One additional note: If you intend to use your PC on occasion without the external drive attached, change the "auto" to a "noauto", to prevent errors. You can then mount your disk on demand, whenever you want to use it.

---

### Post by gertva on 2006-09-17
Thank you kidders.

we're getting there... 

If I mount it, I get "Permissions denied".

But if I use "sudo mount /mnt/lacie" the mounting is successful. 
Only, I can only read the drive with root rights when I start "gksudo nautilus".

Any idea?

---

### Post by kidders on 2006-09-17
> If I mount it, I get "Permissions denied".
Yep, typically only root has permission to mount filesystems, under normal circumstances. You can override this behaviour in your /etc/fstab.

> I can only read the drive
This is also normal for filesystems that don't have good security support. You can override this behaviour too, in your /etc/fstab.

Check out the NTFS section of the man page for "mount" ... specifically, the "user", "users", "gid", "uid" and "umask" mount options.

Additionally, Linux's write support for NTFS is still experimental. Although you can enable it if you really want to, it is not yet considered "safe" to do so. Tbh, you'd be far better off switching to a decent Linux filesystem at some stage.

---

