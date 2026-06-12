---
title: "USB drives not coming up"
date: 2007-01-31
forum: Absolute Beginner Talk
---

### Post by JNowka on 2007-01-31
I have been trying for a few hours now to get my usb drives to be recognized under edgy.  I was able to do it just fine at first, and then the next thing I know it refuses to mount them.  The computer recognizes the usb drives but just doesn't mount them.  There are no broken packages and I have not uninstalled anything.  But I did install some files seeing that it was a fresh install.  I remember a while back there was a solution where you had to go and edit some file, but I cant remember which file it is.

Thank you in advance.

---

### Post by riven0 on 2007-01-31
How about your /etc/fstab file? Did you trying adding an entry in there? Otherwise, run the command **sudo fdisk -l** and see if your usb is listed there.

---

### Post by taurus on 2007-01-31
What's the output of this command from a terminal?

Applications -> Accessories -> Terminal
```
sudo fdisk -l
```

---

### Post by JNowka on 2007-01-31
riven0:
No I have not tried adding anything to my fstab.  On my other computer it works just fine so I think there is just a small config file that has a problem. 


taurus:
I am sorry but I am using kubuntu 6.10 on my laptop. as for fdisk -l:

> Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               2       19457   156280320    f  W95 Ext'd (LBA)
/dev/sdb5               2       19457   156280288+   7  HPFS/NTFS


Problem is I also cant get my flash drive to work either.  I was able to get these drives to mount earlier on the same computer.

---

### Post by taurus on 2007-01-31
```
sudo mount -t ntfs /dev/sdb5 /media/usbdrive -o nls=utf8,umask=0222
df -h
```
And don't forget to unmount it first before you unplug it.

```
sudo umount /dev/sdb5
```

---

### Post by dcstar on 2007-01-31
> **JNowka said:**
> I have been trying for a few hours now to get my usb drives to be recognized under edgy.  I was able to do it just fine at first, and then the next thing I know it refuses to mount them.  The computer recognizes the usb drives but just doesn't mount them.  There are no broken packages and I have not uninstalled anything.  But I did install some files seeing that it was a fresh install.  I remember a while back there was a solution where you had to go and edit some file, but I cant remember which file it is.

Thank you in advance.

Check if **gnome-volume-manager** is running, if not then System-Preferences-Removable Storage will kick it off.

If you find that - after a boot - that USB auto-mounting is unreliable, and you have auto-logon enabled, then do the following:

[LIST=1]
[*]Disable auto-logon
[*]Enable logon after a period (say 5 seconds)
[/LIST]

There is a timing bug where the Gnome desktop launches before other processes have completed loading, and this can cause gnome-volume-manager (and many other things!) not to function correctly after boot because Gnome starts too quickly.

On my own Edgy system USB auto-mounts were problematic (as well as hddtemp reporting in Gkrellm) until I found this particular solution, now they seem rock-solid.

---

