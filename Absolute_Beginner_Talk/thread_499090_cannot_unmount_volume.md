---
title: "cannot unmount volume"
date: 2007-07-12
forum: Absolute Beginner Talk
---

### Post by oliviacond on 2007-07-12
every time i eject/unmount an USB disk (drive/mp3 player), an error message "Cannot unmount volume" with details "Cannot remove directory" will appears, and the "Writing Data to Disk" will appear forever.

this happens after i update to the latest kernel.

---

### Post by aquavitae on 2007-07-12
What happens if you open a terminal and type the command:
umount -v /media/disk
Assuming your usb disk if mounted to /media/disk.

---

### Post by Inxsible on 2007-07-12
> **oliviacond said:**
> every time i eject/unmount an USB disk (drive/mp3 player), an error message "Cannot unmount volume" with details "Cannot remove directory" will appears, and the "Writing Data to Disk" will appear forever.

this happens after i update to the latest kernel.

you should use pmount to mount your external drives. pmount has never failed me.

---

### Post by oliviacond on 2007-07-14
> **aquavitae said:**
> What happens if you open a terminal and type the command:
umount -v /media/disk
Assuming your usb disk if mounted to /media/disk.

nothing happens, just "/dev/sdb1 is unmounted"

---

### Post by nilsja on 2007-08-20
i have the same problem. when i use the contextmenu on the desktop i get the same error like oliviacond. but with
sudo umount -v /media/CORSAIR

the unmount works fine. ("/dev/sdb1 umounted") 

how can i fix the more user friendly variant on the desktop?

edit:
i'm running ubuntu feisty.

---

### Post by jspangler on 2007-09-09
> **aquavitae said:**
> What happens if you open a terminal and type the command:
umount -v /media/disk
Assuming your usb disk if mounted to /media/disk.

I have this problem, and it says:

umount: /media/lacie is not in the fstab (and you are not root)

Also, when I try to do graphical umount, it says "can't eject disk" and reloads the drive.

---

### Post by aquavitae on 2007-09-10
I've never done this before, so I'm not sure how to fix your problem, but a bit of googling has found this: the program that handles mounting/unmounting in gnome is gnome-mount, and its configuration is stored in gconf.  For it to work properly (I think) you must not have an entry in /etc/fstab
So the questions, are you using gnome? (i.e. Ubuntu, not kubuntu or xubuntu)
Can you post the output of ```
cat /etc/fstab
```
Try this (replace /dev/sda1 for the device you're trying to unmount), and post the output:```
gnome-mount -v -u -d /dev/sda1
```
Also, remember you can unmount anything using```
sudo umount *<device>*
```where *<device>* is either the device name (e.g. /dev/sda1) or the mount point (e.g. /media/disk)

---

### Post by jspangler on 2007-09-10
Actually, I discovered it's a known HAL bug in Ubuntu 7.04. I fixed it with this command:

```
sudo mv /usr/share/hal/fdi/policy/10osvendor/10-storage-policy.fdi /usr/share/hal/fdi/policy/10osvendor/10-storage-policy.fdi.backup

```

and now unmounting works like a charm.

---

### Post by liviubero on 2007-09-11
Wow, jspangler, you also saved me with that line...
I have a Maxtor external usb hard disk drive which is in ntfs formated and at first it all went ok, I installed ntfs-config and could write and read the hard. But then it just started not working anymore. Could not eject the drive, I was always getting a popup window saying something like "Cannot eject drive, data needs to be written on it... please try latter", but I wasn't writing anything on it, just plugged it in and then wanted to eject it, through the gnome interface.
And then I renamed the file you pointed at and poof! it worked.
That file has by me the following content (using Feisty):

> <!-- -*- SGML -*- -->
&#8722;
    <deviceinfo version="0.2">
&#8722;
    <!--
 Always eject USB storage devices to properly power them off 
-->
&#8722;
    <device>
&#8722;
    <match key="info.category" string="storage">
&#8722;
    <match key="storage.bus" string="usb">
<merge key="storage.requires_eject" type="bool">true</merge>
</match>
&#8722;
    <match key="storage.bus" string="ieee1394">
<merge key="storage.requires_eject" type="bool">true</merge>
</match>
</match>
</device>
</deviceinfo>
Could you please make it clear what's that? What's in there and why does the ejecting now works? Sorry, am a newbie and trying to understand things.
I only know the the file command gives me this information:
10-storage-policy.fdi.backupLIVIU: XML 1.0 document text

---

### Post by jspangler on 2007-09-11
I really don't know what's in that file, quite honestly. I picked it up in another post :) However, I think the problem is that a USB HDD can't take an eject command, while this file requires that an eject command be sent to the drive. We remove this requirement, and it only allows unmount.

---

### Post by liviubero on 2007-09-11
Hmmm.. But a few days before it worked... I had no problem ejecting the drive. Just right clicked it and then eject.

---

### Post by oliviacond on 2007-09-25
> **aquavitae said:**
> I've never done this before, so I'm not sure how to fix your problem, but a bit of googling has found this: the program that handles mounting/unmounting in gnome is gnome-mount, and its configuration is stored in gconf.  For it to work properly (I think) you must not have an entry in /etc/fstab
So the questions, are you using gnome? (i.e. Ubuntu, not kubuntu or xubuntu)
Can you post the output of ```
cat /etc/fstab
```
Try this (replace /dev/sda1 for the device you're trying to unmount), and post the output:```
gnome-mount -v -u -d /dev/sda1
```
Also, remember you can unmount anything using```
sudo umount *<device>*
```where *<device>* is either the device name (e.g. /dev/sda1) or the mount point (e.g. /media/disk)

```
cat /etc/fstab
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=c87eed1c-546e-431b-b788-c74a04224883 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=296331b0-f597-42c5-9924-6d65e613be0b none            swap    sw              0       0
/dev/cdrom       /media/cdrom0   udf,iso9660 user,noauto     0       0


```
gnome-mount -v -u -d /dev/sda1
```
gnome-mount 0.5

---

### Post by BeeDee on 2007-10-05
> **jspangler said:**
> Actually, I discovered it's a known HAL bug in Ubuntu 7.04. I fixed it with this command:

```
sudo mv /usr/share/hal/fdi/policy/10osvendor/10-storage-policy.fdi /usr/share/hal/fdi/policy/10osvendor/10-storage-policy.fdi.backup

```

and now unmounting works like a charm.

Thanks, jspangler, it works for me too for my USB devices (I had no problem with CD's).  I notice that the option in the right-click pop-up menu has now changed from Eject to Unmount, which makes more sense too.

---

### Post by Vic! on 2007-11-25
I have the same problem and i tried the one line that jspangler posted and i still get the cannot unmount volume error  any help will be greatly appreciated 

thanx!!

---

### Post by rabbit20 on 2008-05-01
Same problem when i do that i get an error that the file doesn't exist   with that one liner....here is what i have...when i plug the drives in they came up fine, on the unmount one of the usb drives had no problem, the second one that has 2 partitions has the issue. is had disk-1 and disk-2   2 leaves but one doesnt, when i plugged it back in i got a new disk-1...so there are two disk-1s on the desktop....HELP!!!!

---

### Post by tlhogan on 2008-05-21
Well I see it has been a couple of weeks and I am not sure if anyone has come up with a solution but here is what worked for me when I started receiving the un-mount error after the most recent kernel update.

Go to the /media directory and remove the file ".hal-mtab" and ".hal-mtab-lock" and then reboot.  After I did that I stopped seeing the un-mount errors.  Not sure what is in a zero byte file that could cause the grief but there it is.

---

### Post by SonicSteve on 2008-05-26
> **tlhogan said:**
> Well I see it has been a couple of weeks and I am not sure if anyone has come up with a solution but here is what worked for me when I started receiving the un-mount error after the most recent kernel update.

Go to the /media directory and remove the file ".hal-mtab" and ".hal-mtab-lock" and then reboot.  After I did that I stopped seeing the un-mount errors.  Not sure what is in a zero byte file that could cause the grief but there it is.

Awesome, this bug has been bitting me for far too long. I see it if a umount fails and I have to unplug the device. 
FYI, this fix worked without even rebooting.

In the .hal-mtab file it contained what looked like stale mount information from a usb drive that had been plugged in some time ago. The .hal-mtab-lock file was empty. I'm guessing that when a usb drive is plugged in the connection info is stored in these files and when they are umounted they are supposed to be cleared.

---

