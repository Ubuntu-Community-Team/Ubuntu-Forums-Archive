---
title: "How to not &quot;auto-mount&quot; other partitions"
date: 2006-10-23
forum: Absolute Beginner Talk
---

### Post by HW_Hack on 2006-10-23
Hi all --- After trying both Mandriva and SUSE ... I've finally got wireless working on Ubuntu Dapper Drake (thanks to this forum) so it looks like I'll be using Ubuntu on my dual boot Dell laptop for a while.

One mildly annoying thing is that Ubuntu shows my other 2 partitions on the hard disk on the upper left of the desktop (one is a Dell Maintenance partition) --- I have no use for these where to I tell the OS not to bother mounting these other partitions ??

Thanks

---

### Post by jorn on 2006-10-23
Go into:
> sudo gedit /etc/fstab
And put a # in front of those you don't want to be mounted at startup.
To find the correct partitions use:
> sudo fdisk -l

---

### Post by aysiu on 2006-10-23
```
gksudo gedit /etc/fstab
``` will work just fine if you're using Ubuntu, but you may want to back it up first, in which case I'd recommend either ```
gksudo nautilus
``` or ```
sudo nano -B /etc/fstab
```

---

### Post by jorn on 2006-10-23
Yes, aysiu, you are right, I just could't remember the "gksu" when writing.
From the beginning I got uset do just "sudo". Backing up is also very advisible.

---

### Post by anaconda on 2006-10-23
Dont comment the lines away. If you comment the lines away, then you have to be root to be able to mount the partitions. and you have to use the whole long mount -command eg.

sudo mount -t auto /dev/hda1 /mnt/storage  ...

if you have the line in your fstab you could just type:
mount /dev/hda1 
(or mount /mnt/storage  both of these work)
and the partition will be mounted with all the rights given to that partition in your fstab -file 

If you have the lines in your fstab -file, then any user can mount  those partitions.

just put "noauto" and "user" to the 4th column in your fstab -file and remove the "defaults" if it is there.

more information:
[http://www.tuxfiles.org/linuxhelp/fstab.html](http://www.tuxfiles.org/linuxhelp/fstab.html)

---

### Post by jorn on 2006-10-23
Thanks, anaconda, I'm also learning every day.

---

### Post by Jose Catre-Vandis on 2006-10-23
or, if you just want to hide the icons on the desktop (following on from anaconda's theme) do the following:

Open a terminal and enter

gconf-editor

Then when Configuration Editor opens up click apps > nautilus > desktop > volumes_visible.

Set it to false by unticking it. Then close it.

---

### Post by Ruskie on 2006-10-23
> **Jose Catre-Vandis said:**
> or, if you just want to hide the icons on the desktop (following on from anaconda's theme) do the following:

Open a terminal and enter

gconf-editor

Then when Configuration Editor opens up click apps > nautilus > desktop > volumes_visible.

Set it to false by unticking it. Then close it.

That's the less "intrusive" way. Partitions get mounted, but you don't see them on the desktop.
Since the maint partition should not be even touched however, I would avoid mounting it, like others said...

Ciao
M.

---

### Post by steve.horsley on 2006-10-23
It's my understanding that only partitions mounted in /media are shown on the desktop. I normally move the permanently mounted partitions to /mnt instead. Although of course, of they're noauto,user then you want to keep them in /media so they appear when wanted.

---

