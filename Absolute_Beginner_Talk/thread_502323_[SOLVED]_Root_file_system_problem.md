---
title: "[SOLVED] Root file system problem?"
date: 2007-07-16
forum: Absolute Beginner Talk
---

### Post by ninja_in_pajamas on 2007-07-16
Every 22 startups, I get a message that says "hda/sda1 has been mounted 22times without being checked. Check forced.   Then it proceeds to do a system check.  Is there any reason why or any way I can make it stop doing this?

---

### Post by Skidpad on 2007-07-16
This is normal, and is the equivalent of XP's Disk Check. You can change the default setting (30 I think), or there are add-on programs to monitor when Ubuntu is going to perform this check. I use "Bonager" for this. It put a little icon in my system tray allowing me to instantly know how many boots before it does the check again.

More info (and how to change it): [Here]("http://ubuntuforums.org/showthread.php?t=300477")

---

### Post by ninja_in_pajamas on 2007-07-16
Skidpad, that helps but I would prefer not to go the Bonager route.  I tried using the code and I got back this message:
tune2fs 1.40-WIP (14-Nov-2006)
tune2fs: No such file or directory while trying to open /dev/sad/hda1
Couldn't find valid filesystem superblock.

I assume I need to check in fstab and see exactly what the drive is labeled but I don't recall how to do it.

---

### Post by Sbarton on 2007-07-16
As skidpad says it is a normal procedure for hdd to be checked, it takes very little time and IMO is worth allowing it to do so.
regards

---

### Post by Skidpad on 2007-07-16
> **ninja_in_pajamas said:**
> Skidpad, that helps but I would prefer not to go the Bonager route.  I tried using the code and I got back this message:
tune2fs 1.40-WIP (14-Nov-2006)
tune2fs: No such file or directory while trying to open /dev/sad/hda1
Couldn't find valid filesystem superblock.

I assume I need to check in fstab and see exactly what the drive is labeled but I don't recall how to do it.
Run df -h in a terminal, it'll show all drives and mount points.  

Here's mine:
jim@LinuxLaptop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
**/dev/hda2              19G  4.6G   14G  27% /**
varrun                220M   96K  220M   1% /var/run
varlock               220M     0  220M   0% /var/lock
procbususb             10M   88K   10M   1% /proc/bus/usb
udev                   10M   88K   10M   1% /dev
devshm                220M     0  220M   0% /dev/shm
lrm                   220M   18M  203M   8% /lib/modules/2.6.17-11-generic/volatile
/dev/hda1              18G   12G  5.9G  67% /media/windows

When I ran the tune2fs command, I had to change it from the example given, to  sudo tune2fs -c 50 /dev/hda2, because my Ubuntu/Linux filesystem is on hda2 - as **shown above**.  You'll need to to change your command to reflect your filesystem.  Try df -h so you can see where it is.  Post back if you need help.

---

### Post by kerry_s on 2007-07-16
You can turn it off in fstab.
gksu gedit /etc/fstab

```
/dev/hda2       /               ext2    defaults,noatime,errors=remount-ro 0       [B]1
[/B]
change the # on the end to "0"

/dev/hda2       /               ext2    defaults,noatime,errors=remount-ro 0       **0**
```

---

