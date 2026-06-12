---
title: "All my music is on an NTFS drive"
date: 2008-04-21
forum: Absolute Beginner Talk
---

### Post by Jimmy9pints on 2008-04-21
Hi, because I came over from Windows, all of my music is on an NTFS drive. 

What's the best way to deal with this?

Currently I mount the drive every time I log into Ubuntu - which is a bit of a pain.

Is there another way?

---

### Post by jakupl on 2008-04-21
move it to the ubuntu partition ;) just kidding :)

---

### Post by kpkeerthi on 2008-04-21
If you have a spare disk, copy the music over. Reformat your NTFS drive to ext3 and transfer back the files. I recommende this. :)
or 
You can have your NTFS drive mounted automatically at boot time. If you want to do this, let me know. I can help.

---

### Post by adouglasmhor on 2008-04-21
kpkeerthi can you let me know how to do this please, I am in the same boat as OP.

---

### Post by Victormd on 2008-04-21
The fastest and easiest way would be to automatically mount your NTFS drive (I thought this was default...) but if you're not going to be dual booting, then convert your entire drive to ext3. You can do this with gparted but will take a bit of resizing your partitions, moving files, resizing again, moving some more files until all your files are on a ext3 Partition...

---

### Post by kpkeerthi on 2008-04-21
Before you do this, unmount your NTFS partition if you have mounted it manually.

1. Get the name of your NTFS partition
```
sudo fdisk -l
```
* I assume /dev/sda2 as the NTFS partition
	
2. Make folder where your NTFS partition will be mounted
```
sudo mkdir /media/Windows
```

3. Edit	FSTAB to mount the partition at boot
```
gksudo gedit /etc/fstab
```

4. Add this line to the end of the file
```
/dev/sda2 /media/Windows ntfs-3g defaults 0 0
```
Save and Exit.

5. Test it
```
sudo mount -a
```

If all goes well, you should see a desktop shortcut to the partition and should auto-mount next time you reboot. 

Post back errors, if any.

---

### Post by Jimmy9pints on 2008-04-21
My NTFS was /dev/hdb1

Followed your instructions and everything went smoothly. 

Thank you!

---

### Post by adouglasmhor on 2008-04-21
Will try this as soon as I have time at home thank you.

---

### Post by markusX on 2008-04-25
thanks for the guide. worked like a charm. ^^

---

### Post by andrewabc on 2008-04-25
Oddly I noticed this with a fresh install of Hardy.
It automounted all partitions with hardy alphas.

thanks for the tip.

EDIT:
Hmm, editing fstab is not working for me. I input correct uuid and dev/sda2 and other stuff but it does not see them. gives errors that it does not exist, wehn they clearly do.

EDIT:
I think I got it working. Yep got it working with a simple
> /dev/sda2 /media/ACER ntfs-3g defaults 0 0
/dev/sda3 /media/disk ntfs-3g defaults 0 0
Although oddly the disk partition used to be called PQSERVICE on my old hardy install.
It is even labeled PQSERVICE in /dev/disk/by-label
oh well.

---

### Post by gaffurabi on 2008-04-26
i did it like this:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda7
UUID=5ade7ef2-d6fd-4af6-a878-17cb61dcef69 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda6
UUID=98f7ac4b-3b47-4b55-94bc-185e978c6145 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/sdb5 /media/Windows ntfs-3g defaults 0 0
/dev/sdb6 /media/Windows ntfs-3g defaults 0 0
/dev/sdb1 /media/Windows ntfs-3g defaults 0 0
/dev/sda1 /media/Windows ntfs-3g defaults 0 0
/dev/sda5 /media/Windows ntfs-3g defaults 0 0
```

and now it only mounts sdb5 :(

---

### Post by kpkeerthi on 2008-04-28
gaffurabi,
You cannot mount all your partitions to the same mount points.
First create separate mountpoints for the partitions
```

sudo mkdir /media/sdb5 
sudo mkdir /media/sdb6 
sudo mkdir /media/sdb1 
sudo mkdir /media/sda1 
sudo mkdir /media/sda5 

```
Then change the lines in FSTAB as below. 
```

/dev/sdb5 /media/sdb5 ntfs-3g defaults 0 0
/dev/sdb6 /media/sdb6 ntfs-3g defaults 0 0
/dev/sdb1 /media/sdb1 ntfs-3g defaults 0 0
/dev/sda1 /media/sda1 ntfs-3g defaults 0 0
/dev/sda5 /media/sda5 ntfs-3g defaults 0 0

```

* Instead of /media/sdb5, you may want to assign a more meaninful name for the partitions depending on the partition's use. /media/Music, /media/Pictures, /media/Data etc.

---

### Post by spawnywhippet on 2008-04-28
I am unable to access any data on my external NTFS USB drive. I use this on many Windows machines and it cannot be changed to ext3. I'm using Ubuntu 8.04 Hardy Heron.
Would gratefully appreciate assistance...

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x50bc9e52

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       10199    81923436    7  HPFS/NTFS
/dev/sdb2           10200       14593    35294805    7  HPFS/NTFS

andy@ubuntu-laptop:~$ sudo mkdir /media/software
andy@ubuntu-laptop:~$ sudo mkdir /media/burn
andy@ubuntu-laptop:~$ gksudo gedit /etc/fstab

I added this to fstab:

/dev/sdb1 /media/software ntfs-3g defaults 0 0
/dev/sdb2 /media/burn ntfs-3g defaults 0 0

andy@ubuntu-laptop:~$ sudo mount -a
$LogFile indicates unclean shutdown (0, 0)
Failed to mount '/dev/sdb1': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the 'Safely Remove Hardware' icon in the Windows
          taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/sdb1 /media/software -o force

    Or add the option to the relevant row in the /etc/fstab file:

            /dev/sdb1 /media/software ntfs-3g force 0 0
$LogFile indicates unclean shutdown (0, 0)
Failed to mount '/dev/sdb2': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the 'Safely Remove Hardware' icon in the Windows
          taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/sdb2 /media/burn -o force

    Or add the option to the relevant row in the /etc/fstab file:

            /dev/sdb2 /media/burn ntfs-3g force 0 0
andy@ubuntu-laptop:~$ mount -t ntfs-3g /dev/sdb1 /media/software -o force
mount: only root can do that

---

### Post by kpkeerthi on 2008-04-28
Do not attempt to force mount the NTFS partions as it may render it unusable. If you have access to a windows machine, boot into it, plugin the USB drive and then simple use "Safely remove hardware" from the system tray. Then retry with Ubuntu. 
To mount the partition manually use this command
```
**[COLOR="Red"]sudo [/COLOR]**mount -t ntfs-3g /dev/sdb1 /media/software
```

To force mount the partition
```
**[COLOR="Red"]sudo[/COLOR]** mount -t ntfs-3g /dev/sdb1 /media/software -o force
```
But again, be warned that force mounting NTFS may render the partition unusable.

---

### Post by spawnywhippet on 2008-04-28
Excellent, thanks for that, works perfectly. Do I need to repeat this with each re-boot, or make new entries in fstab?

---

### Post by kpkeerthi on 2008-04-28
Yeah. Add these lines to your fstab
```

/dev/sdb1 /media/software ntfs-3g defaults 0 0
/dev/sdb2 /media/burn ntfs-3g defaults 0 0

``` to have them automounted at boot up.

**PS:** Make sure that you always do "Safely Remove Hardware" on these partitions whenever you access them from Windows and you should be good.

---

