---
title: "Mounting an external hard drive"
date: 2007-02-27
forum: Absolute Beginner Talk
---

### Post by Foudre on 2007-02-27
Ok, so I'm trying to mount my nice 300 gig external hardrive, problem is, though linux detects it, it even asks me what i want to do about it, open to view, or do nothing. If i click on the open to view, nothing happnes, and its not in the storage media, now i've forgotten how to edit ftab or even the name of it (think its ftab) i assume thats how i'd mount it, but i got it to open fine last night when i booted form the livecd/install cd, its just because this damned static drive setup on dapper and previous version, i heard they are going to try and make it detect on boot each time, and making it less static on the new version of ubuntu, anyways i'm using dapper, i've got a tight setup and would be nice to use my nice big hard drive so i don't have to boot to windows to put stuff on it

---

### Post by taurus on 2007-02-27
What's the output of this command with your external harddrive plugged in?

```
sudo fdisk -l
```

p.s.  The name of the file you want to edit is called /etc/fstab.

---

### Post by Foudre on 2007-02-27
Disk /dev/sda: 78.5 GB, 78518522880 bytes
255 heads, 63 sectors/track, 9546 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           7        6272    50331645    7  HPFS/NTFS
/dev/sda2            6273        9406    25173855   83  Linux
/dev/sda3            9407        9542     1092420   82  Linux swap / Solaris
/dev/sda4            9543        9546       32130   83  Linux

Disk /dev/sdc: 319.9 GB, 319941488640 bytes
255 heads, 63 sectors/track, 38897 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       38898   312442484    c  W95 FAT32 (LBA)



guessing that sdc1 is my external

---

### Post by taurus on 2007-02-27
Yes, it is.

Do this from a terminal.

```
sudo mount -t vfat /dev/sdc1 /media/usbdrive -o iocharset=utf8,umask=000
df -h
```

---

### Post by Foudre on 2007-02-27
not sure if it worked but i can't access the drive

:~$ sudo mount -t vfat /dev/sdc1 /media/usbdrive -o iocharset=utf8,umask=000 df -h
Usage: mount -V                 : print version
       mount -h                 : print this help
       mount                    : list mounted filesystems
       mount -l                 : idem, including volume labels
So far the informational part. Next the mounting.
The command is `mount [-t fstype] something somewhere'.
Details found in /etc/fstab may be omitted.
       mount -a [-t|-O] ...     : mount all stuff from /etc/fstab
       mount device             : mount device at the known place
       mount directory          : mount known device here
       mount -t type dev dir    : ordinary mount command
Note that one does not really mount a device, one mounts
a filesystem (of the given type) found on the device.
One can also mount an already visible directory tree elsewhere:
       mount --bind olddir newdir
or move a subtree:
       mount --move olddir newdir
A device can be given by name, say /dev/hda1 or /dev/cdrom,
or by label, using  -L label  or by uuid, using  -U uuid .
Other options: [-nfFrsvw] [-o options] [-p passwdfd].
For many more details, say  man 8 mount .
kage@kage-laptop:~$ sudo mount -t vfat /dev/sdc1 /media/usbdrive -o iocharset=utf8,umask=000 df
Usage: mount -V                 : print version
       mount -h                 : print this help
       mount                    : list mounted filesystems
       mount -l                 : idem, including volume labels
So far the informational part. Next the mounting.
The command is `mount [-t fstype] something somewhere'.
Details found in /etc/fstab may be omitted.
       mount -a [-t|-O] ...     : mount all stuff from /etc/fstab
       mount device             : mount device at the known place
       mount directory          : mount known device here
       mount -t type dev dir    : ordinary mount command
Note that one does not really mount a device, one mounts
a filesystem (of the given type) found on the device.
One can also mount an already visible directory tree elsewhere:
       mount --bind olddir newdir
or move a subtree:
       mount --move olddir newdir
A device can be given by name, say /dev/hda1 or /dev/cdrom,
or by label, using  -L label  or by uuid, using  -U uuid .
Other options: [-nfFrsvw] [-o options] [-p passwdfd].
For many more details, say  man 8 mount .


is what outputs, and i still can't access it either via url to in, or in the media folder


how would i add a usb drive to fstab,

---

### Post by taurus on 2007-02-27
It should be two lines.

```

sudo mount -t vfat /dev/sdc1 /media/usbdrive -o iocharset=utf8,umask=000 [Return]
df -h [Return]

```
And if you want to add it to your /etc/fstab, then

```
gksudo gedit /etc/fstab
```
and add this line to the end of it.

```
/dev/sdc1   /media/sdc1   vfat   iocharset=utf8,umask=000   0   0
```
Save it.  Now, create a new mount point and mount it.

```
sudo mkdir /media/sdc1
sudo mount -a
df -h
```

---

### Post by Foudre on 2007-02-27
hmm ya so, for some stupid reason that killed my xserver, and now i can't get it working again, even dpkg-reconfigure xserver-xorg won't restore it, how do i edit a text file from the command prompt so i can restore the fstab, cause i get a system beep when it says loading file systems and then after the phase of loading stuff it goes to comman prompt login after i log in it flashes the image of kubuntu and freezes, i can still hit ctrl+alt+f1 to do stuff, so, why the hell did that kill my xserver or what ever its doing?

---

### Post by taurus on 2007-02-27
```
sudo nano /etc/fstab
```
<Ctrl>o and <Ctrl>x to save and exit.

---

### Post by Foudre on 2007-02-27
hmm, my fstab doesn't look right at all, not sure why it would but i think kwrite ended up saving the wrong thing over fstab, cause the file mentions mouse this and kde that, and from nano a long line of @ symbols, so i don't know rember off the top of my head what was there, and for some reason the auto back up file the fstab~ is a blank file, so, is there some way to have it search for drives again and write a new fstab or do i have to figure out how to write it myself since i know some drives had some of the options and i don't know what they were

---

### Post by taurus on 2007-02-27
What's the output of this command from a terminal?

```
ls -la /etc/fstab*
```

---

### Post by Foudre on 2007-02-27
rw-r--r-- root root 615 2007-02-27 12:13 /etc/fstab

---

### Post by taurus on 2007-02-27
```
cat /etc/fstab
```

---

### Post by Foudre on 2007-02-27
[$Version]
update_info=kaccel.upd:kde3.3/r1,kded.upd:kde3.0,klippershortcuts.upd:04112002,kwin.upd:kde3.2Xinerama,mouse_cursor_theme.upd:kde3.4.99,socks.upd:Kde3.0/r1

[KDE]
cursorTheme[$d]

[Paths]
Trash=$Home/Desktop/Trash

---

### Post by Foudre on 2007-02-27
the problem here has become a different on then when the thread started, i think maybe a new thread more directed toward the question at hand, might yield more results

---

