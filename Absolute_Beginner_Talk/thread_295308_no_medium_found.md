---
title: "no medium found"
date: 2006-11-07
forum: Absolute Beginner Talk
---

### Post by drx0 on 2006-11-07
I can't mount a CD in either of my two DVDRW drives.  They are working in Windows on the same PC -- NOT a configuration problem.
It fails with the GUI mounter and with the sudo mount...

Any ideas?  Thanks much in advance!

Btw, my fstab file is as follows:

admin@admin-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb1
UUID=6db68e34-858b-46fe-89fb-2de0ea2e0db3 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sdb5
UUID=f534c70c-133d-40ac-bdbd-bdd020f13010 none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdb        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0

---

### Post by Ecthelion on 2006-11-08
CD/DVD-readers/writers can't be found in fstab...

How did you installed Ubuntu if none of your cd-drivers can mount a cd?
Do you find your dvd-drives in the list you get when you do:

```
hal-device-manager
```

?

---

### Post by drx0 on 2006-11-09
I just booted from the Ubuntu Edgy Beta CD I burned on a Windows PC.  I will try the command you specified and get back on result.  Suppose it doesn't show up -- how/where do I find/load a DVD-RW driver in Edgy 6.10?

Thanks again!

---

### Post by Ecthelion on 2006-11-09
I don't see how you would boot up from a cd if Ubuntu wouldn't recognize your cd/dvd drives...
So that means you probably will find them in the list...

> It fails with the GUI mounter and with the sudo mount...

How did you do it wih the sudo mount?
I mean what was the exact command you used?

> I just booted from the Ubuntu Edgy Beta CD I burned on a Windows PC
Why Edgy Beta?

---

### Post by Ecthelion on 2006-11-09
I'm sorry I seem to have given wrong information:

[QUOTE=Ecthelion]CD/DVD-readers/writers can't be found in fstab...[/QUOTE]

This isn't true...

They should be in fstab.

Since yours are in your fstab, it is a proof that they are recognized...

I can't really see a reason why you can't mount them then...

---

### Post by drx0 on 2006-11-09
yes, I see them here.  but they won't mount any CD.

---

### Post by drx0 on 2006-11-09
sudo mount /dev/hda
and
sudo mount /dev/hdb

I also tried the Places-Computer-CD...-mount

---

### Post by Ecthelion on 2006-11-10
> sudo mount /dev/hda
and
sudo mount /dev/hdb

as far as I can recall you mount your disks to nowhere...

> **Coming from man mount page:**

The standard form of the mount command, is
              mount -t type device dir
       This  tells the kernel to attach the file system found on device (which
       is of type type) at the directory dir.  The previous contents (if  any)
       and  owner  and  mode of dir become invisible, and as long as this file
       system remains mounted, the pathname dir refers to the root of the file
       system on device.


So you should mount it to a location:
```
sudo mount /dev/hda /media/<name of the folder you use>
```

---

### Post by Ecthelion on 2006-11-10
Someone else with the same problem recently started a [thread]("http://ubuntuforums.org/showthread.php?t=296460")

[QUOTE=Radiera]This happened because of the new idiotic fstab lines.
in your console type sudo nano /etc/fstab.
Modify the cd-rom line so it will look like that:
/dev/hdc /media/cdrom0 auto user,noauto 0 0[/QUOTE]

---

### Post by Ben Sprinkle on 2006-11-10
So what your saying is that when you pop the dvd/cd in your drive, it won't mount it and display a shortcut on your desktop?
Mine does that, mabey your hardware isn't compatible or came unplugged.
Another alternative is check thier fans for dust clog, it can really muck up connections from lack of breathing.

---

### Post by drx0 on 2006-11-16
Changing the sudo nano /etc/fstab by Modify the cd-rom line so it will look like the following did not work:
/dev/hdc /media/cdrom0 auto user,noauto 0 0

After that change, they did not work at all.  Without the change, they mount if you restart the computer, but the desktop mounter doesn't work nor do the command line mount commands.  Burning software doesn't work at all.

---

### Post by Ecthelion on 2006-11-16
> Changing the sudo nano /etc/fstab by Modify the cd-rom line so it will look like the following did not work:
/dev/hdc /media/cdrom0 auto user,noauto 0 0

That's because you don't have a /dev/hdc

If you try that trick, you should use this:

/dev/hda /media/cdrom0 auto user,noauto 0 0
/dev/hdb /media/cdrom1 auto user,noauto 0 0

You could try it.. but make sure to backup your fstab first ;-)

---

### Post by Xizorbg on 2006-11-24
Hiya-

Still using 6.06.  I am having the same prob with my Pioneer DVD-120s.  I tried reinstalling the gnome-volume-manager, as well as changing my fstab.  In my device manager, it shows both my DVD-Reader (the Pioneer) which is hdd and my Plextor writer, which is hdc.  They are connected well.  Can someone please tell me what the deal is?  The Plextor mounts fine and I just want to be able to backup my DVDs.

Thanks so much,
X](*,)

---

### Post by jeromio on 2006-11-30
I moved this machine from Centos to Kubuntu 6.10 (which I point out only to assure you that the drives themselves are fine). The CDROM drive works fine and USB drives work fine. But the DVD burner is not working. I can _sort_of_ read DVDs. But not at all reliably. When I insert a disc, it mounts, but then after a very short time period, perhaps 30sec, the drive unmounts. So I can list contents, open or copy small files, but anything large craps out. What happens is that it gets automounted but the user and group are 4294976295. And then, poof!, the drive is unmounted.

My /etc/mtab:
> dev/mapper/VolGroup00-root / ext3 rw,errors=remount-ro 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
/sys /sys sysfs rw,noexec,nosuid,nodev 0 0
varrun /var/run tmpfs rw,noexec,nosuid,nodev,mode=0755 0 0
varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0
procbususb /proc/bus/usb usbfs rw 0 0
udev /dev tmpfs rw,mode=0755 0 0
devshm /dev/shm tmpfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
lrm /lib/modules/2.6.17-10-generic/volatile tmpfs rw 0 0
/dev/hde1 /boot ext3 rw 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw 0 0
/dev/sde1 /media/SEA_DISK vfat rw,nosuid,nodev,quiet,shortname=mixed,uid=1000,gid=1000,umask=077,iocharset=utf8 0 0
/dev/hdc /media/dvdrecorder udf ro,noexec,nosuid,nodev,user=jeromio 0 0

My /etc/fstab (note the commented out line - tried a suggestion from this forum, didn't change things):
> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc /proc proc defaults 0 0
/dev/mapper/VolGroup00-root / ext3 nouser,defaults,errors=remount-ro,atime,auto,rw,dev,exec,suid 0 1
# /dev/hdc1
UUID=1fd79868-c906-4bfd-bc6c-ae1afc3f5679 /boot ext3 nouser,defaults,atime,auto,rw,dev,exec,suid 0 2
/dev/mapper/VolGroup00-swap none swap sw 0 0
#/dev/hdc /media/dvdrecorder auto user,atime,noauto,rw,nodev,noexec,nosuid 0 0
/dev/hdc /media/dvdrecorder auto user,noauto 0 0
/dev/hdd /media/cdrom1 auto user,atime,auto,ro,nodev,noexec,nosuid 0 0


Any ideas?

---

### Post by Ecthelion on 2006-12-01
[QUOTE=jeromio]> # /dev/hdc1
UUID=1fd79868-c906-4bfd-bc6c-ae1afc3f5679 /boot ext3 nouser,defaults,atime,auto,rw,dev,exec,suid 0 2
/dev/mapper/VolGroup00-swap none swap sw 0 0
#/dev/hdc /media/dvdrecorder auto user,atime,noauto,rw,nodev,noexec,nosuid 0 0
/dev/hdc /media/dvdrecorder auto user,noauto 0 0
/dev/hdd /media/cdrom1 auto user,atime,auto,ro,nodev,noexec,nosuid 0 0
[/QUOTE]

What I think is strange is that you have a hard-disk called hdc1 and your dvd called the same (hdc).
... And you have no hda or hdb...
Did you change this fstab yourself?
If you did, what did you change?
It doesn't look like the list the install would have made (correct me if i'm wrong)

---

### Post by Ecthelion on 2006-12-01
> **Xizorbg said:**
> Hiya-

Still using 6.06.  I am having the same prob with my Pioneer DVD-120s.  I tried reinstalling the gnome-volume-manager, as well as changing my fstab.  In my device manager, it shows both my DVD-Reader (the Pioneer) which is hdd and my Plextor writer, which is hdc.  They are connected well.  Can someone please tell me what the deal is?  The Plextor mounts fine and I just want to be able to backup my DVDs.

Thanks so much,
X](*,)

Please post your fstab...

---

### Post by www.rzr.online.fr on 2007-08-10
I got the same error with an old cdrom, my drive is working correctly, but the CD is damaged ... do you know a solution to recover it ?
--
[http://rzr.online.fr/q/recover](http://rzr.online.fr/q/recover)

---

