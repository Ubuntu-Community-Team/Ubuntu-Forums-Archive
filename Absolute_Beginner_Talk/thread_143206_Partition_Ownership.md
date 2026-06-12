---
title: "Partition Ownership?"
date: 2006-03-12
forum: Absolute Beginner Talk
---

### Post by RRS on 2006-03-12
I'm dual booting Breezy and XP with a Fat32 partition for sharing files.
  
I've edited fstab to auto mount both the Fat32 and NTFS partitions but all permissions in both are denied with root shown as the owner of the folders in each.

Everything I've found in these forums and other sites indicate I should be able to access them as user.

Here's a copy of my fstab:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda3       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda6       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hda5       /media/share vfat iocharset=utf8,umask=000 0 0
/dev/hda1    /media/windows ntfs  nls=utf8,umask=0222 0    0

I used the instructions in the Unofficial Breezy User Guide and checked also the "Crazycat" guide and I think I did everything right but all folders in both hda1 and hda5 have all permissions blocked and list "root" as owner when I check their properties.

I have been able to copy and paste files and folders from "windows" to "share" but nothing else seems possible.

My primary short term goal is to be able to use Linux to "save" a seriously broken XP on another (my main) computer. I had planned a dual boot installation for it anyway but figured I'd test, and get used to, Ubuntu first on this machine.

Now I find myself booting into Linux most of the time already anyway and even as a beginner haven't managed to really break anything yet, at least not permanently.

I'll probably still have other questions regarding my ideas to rescue windows but that's probably for a new thread in a different forum.

Hope someone can help.
Thanks in advance.

---

### Post by Mustard on 2006-03-12
Hmmm..its a bit of a mystery.  Is it possible that because of drive errors that those partitions are mounting as read only?

Have you rebooted since making the changes or are have you just edited the /etc/fstab and run a mount -a command from terminal?

I'd like to see the output of this command to if you could..

```
sudo fdisk -l
```

---

### Post by RRS on 2006-03-12
Yes, I rebooted after making initial changes and I've also shut down and restarted a few times since. I rarely leave my computer running if I'm not gonna be using it for more then a couple hours.

Heres's the info you requested;

Disk /dev/hda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        1824    14651248+   7  HPFS/NTFS
/dev/hda2            3579        4865    10337827+   5  Extended
/dev/hda3            1825        3578    14089005   83  Linux
/dev/hda5            3650        4865     9767520    b  W95 FAT32
/dev/hda6            3579        3648      562212   82  Linux swap / Solaris

Thanks

---

### Post by Klejs on 2006-03-12
Have you tried the **chown** command?

Just enter:
```
sudo chown username /dev/device
```

That makes the user you entered the owner of the 
directory/device

Have fun!

---

### Post by RRS on 2006-03-12
[QUOTE=Klejs]
```
sudo chown username /dev/device
```
[/QUOTE]

Thanks, I'll try that later.

I just rebooted into windows so I can listen to BBC with a.m. coffee. (I haven't gotten realplayer working in Ubuntu yet, probably missed something during install but that's a minor problem I'll deal with later)

Thanks for quick replies. All advice and any suggestions are quite welcome.

Edit: Nope that didn't work. Tried rebooting also but properties still show owner as root.

BTW, after my last edit of fstab to automount both partitions when booting they now appear on the desktop so that's how I've been accessing them. Could this be part of my problem?

Thanks again.

---

### Post by RRS on 2006-03-12
Apologies for bump, thought the "edit" would have same results.

Just finished dual boot installation on my other computer with apparent success though.

---

### Post by Mustard on 2006-03-12
I've just been playing around with my vfat partition with windows 98se to and manually mounting it to try to see whats going on.  It's interesting to me that some of the system files I can't get write access to using the mount options from your fstab file for vfat.  I can however access the the files in my documents with read and write capability.  My permissions on some files seems to work and on others they don't.

I really don't know whats going on with it unfortunately.

---

