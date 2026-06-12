---
title: "Using a new ntfs usb HDD in feisty"
date: 2007-12-26
forum: Absolute Beginner Talk
---

### Post by geekchicohio on 2007-12-26
Hi all,
Thanks to the consumeristic orgasm of X-mas, I've got a brand new 250GB usb hard drive (a Seagate FreeAgent, if you're curious) and I just plugged it in.
I'm unable to write to this thing because it's NTFS, as near as I can tell.  I can't change its' permissions, I can't do anything because it's NTFS.
I was under the impression feisty meant no more ntfs headaches.
If anyone can let me in on what I need to do to get feisty to start USING its built in ntfs-3g drivers. Or anything else I can do to gain permission to write to this drive, please let me know.

Additionally, my plans for this drive right now are to migrate my music/photos/docs to it and then make some hardware changes to my computer and install a fresh copy of GUTSY.

Thanks a lot all.

---

### Post by taurus on 2007-12-26
You have to first install ntfs-3g driver.  Then, use it to mount your ntfs partition/drive and you can now write to it.

---

### Post by geekchicohio on 2007-12-26
Why have I been led to believe these are included/built-into Feisty Fawn?
(This may be a rhetorical question if i actually AM just an idiot, and they aren't.) But it seems live I've read everywhere that they were. I assumed that an NTFS hard drive would now "just work" like so much else in linux seems to these days.

---

### Post by taurus on 2007-12-26
You just install it either from synaptic or from a terminal.

```
sudo apt-get update
sudo apt-get install ntfs-3g
```
Then, you would mount it as

```
sudo mkdir /media/sda1
sudo mount -t ntfs-3g /dev/sda1 /media/sda1
ls -la /media
```
Assuming /dev/sda1 is the drive you want to mount.

---

### Post by geekchicohio on 2007-12-26
Alrighty, I've done all of this and now when I try to drag a file into the drive I'm still told I don't have permission to do so.
Please refresh my ever-failing memory on the best way to open this drive up for any user to read/write to.

---

### Post by taurus on 2007-12-26
Can you post the outputs of these commands from a terminal?

```
sudo fdisk -l
mount
```

---

### Post by geekchicohio on 2007-12-26
```

Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1        9240    74220268+  83  Linux
/dev/hda2            9241        9729     3927892+  82  Linux swap / Solaris

```
and
```

/dev/hda1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.20-16-generic/volatile type tmpfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)
/dev/sda1 on /media/FreeAgent Drive type ntfs (rw,nosuid,nodev,umask=222,utf8)

```

---

### Post by taurus on 2007-12-26
How did you mount your /dev/sda1?  Did you just plug it in and it's automated?  Interesting that /dev/sda1 doesn't show up from the output of the "sudo fdisk -l".

---

### Post by geekchicohio on 2007-12-26
I plugged it into a USB port and an icon showed up on my desktop for it. When I tried to drag a file onto the icon, I was told I didn't have permission and so I came here.
I've run Dapper twice and feisty twice and I've had more things occur on my PC without logic or explanation this time around than the other 3 combined. But since a recent hard-drive crash I was planning on putting my few remaining files on this new HD, making some hardware tweaks, and then upgrading to Gutsy.
I've been using Ubuntu for around a year, now, I guess. But only recently decided to start doing more than webbrowsing again, so a lot of what I remember how to do with the OS has rusted out of my brain.

---

### Post by taurus on 2007-12-26
You cannot copy files to it because the automate uses ntfs driver instead of ntfs-3g.  You need to unmount it and then remount it again but this time, use ntfs-3g.

```
sudo umount /dev/sda1
sudo mkdir /media/sda1
sudo mount -t ntfs-3g /dev/sda1 /media/sda1
ls -la /media
```

---

### Post by geekchicohio on 2007-12-26
In following your instructions, I got this:
```

Error reading bootsector: Input/output error
Failed to startup volume: Input/output error
Failed to mount '/dev/sda1': Input/output error
NTFS is inconsistent. Run chkdsk /f on Windows then reboot it TWICE!
The usage of the /f parameter is very IMPORTANT! No modification was
made to NTFS by this software.
```
My desktop icon for the HD didn't come back.

---

### Post by taurus on 2007-12-26
Which command did you run to get that message?

---

### Post by geekchicohio on 2007-12-26
```
sudo mount -t ntfs-3g /dev/sda1 /media/sda1
```

---

### Post by taurus on 2007-12-26
You did install ntfs-3g driver, right?  Can you post the output of this command?

```
sudo apt-get install ntfs-3g
```

---

### Post by geekchicohio on 2007-12-26
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ntfs-3g is already the newest version.
The following packages were automatically installed and are no longer required:
  libemeraldengine0
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.

```

---

### Post by chessercizes on 2007-12-26
hey
umm if i understand your problem, try doing:

```
sudo aptitude install ntfs-config
```

and then going System - NTFS Config
and enable write to external disk

hopefully that helps =)

---

### Post by geekchicohio on 2007-12-26
No luck with ntfs-config. I tried it earlier, as well.

---

### Post by geekchicohio on 2007-12-26
Possible breakthrough? I just ran fdisk -l again for shits and giggles and got something new:
```

Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1        9240    74220268+  83  Linux
/dev/hda2            9241        9729     3927892+  82  Linux swap / Solaris

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       30401   244196001    7  HPFS/NTFS

```

---

### Post by taurus on 2007-12-26
Try to mount it again and see what happens this time.

```
sudo mount -t ntfs-3g /dev/sda1 /media/sda1
ls -la /media
```

---

### Post by geekchicohio on 2007-12-26
Alright. As has been standard operating procedure for this particular install of linux. It just starts and stops working when it damn well pleases.
Now, as I've said I plan to put my important files on this sucker and then I'm going to give my PC a fresh install of gutsy.
In order to properly mount this thing, can I get some sort of condensed version of the proper path to take? (ntfs-3g is NOT built INTO gutsy?)

---

