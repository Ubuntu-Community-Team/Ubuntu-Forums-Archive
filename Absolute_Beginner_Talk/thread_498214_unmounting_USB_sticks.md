---
title: "unmounting USB sticks"
date: 2007-07-11
forum: Absolute Beginner Talk
---

### Post by ginestre on 2007-07-11
I have several identical USB sticks that I use quite happily, but there is an anomaly in some behaviour. When I want to take the stick out, in Nautilus I right click, select UNMOUNT VOLUME and wait for data to be written. I wait a few seconds, the busy light on the sticks flash on and off, and then it quietens down. Now here is the anomaly: I do not always get a little yellow system alert box telling me 'It is now safe to unmount the volume' at this point. Sometimes I do, ad sometimes I don't. 

Anyone any ideas as to why?

---

### Post by 5-HT on 2007-07-11
You can always run 'mount' to see if the drive has been unmounted prior to yanking it out.

FWIW: there was a bug a while ago in which the desktop icon for the drive would dissapear after doing a right-click -> unmount before the drive was done syncing up and actually unmounted. Ever since then I just mount/unmount -v via a shell just to be safe.

---

### Post by ginestre on 2007-07-11
Thank you for that. I just ran mount and found, amongst other stuff,

procbususb on /proc/bus/usb type usbfs (rw)

I presume this is the USB stick which isn't in any of my icon-based views? But if so, why do no applications (specifically, Open Office) see it, to open files? Is it mounted or not, I wonder.


Just in case that isn't the USB here is the entire readout from mount

richard@kids:~$ mount
/dev/hda2 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.20-16-generic/volatile type tmpfs (rw)
/dev/hda5 on /home type ext3 (rw)
/dev/hda1 on /media/hda1 type ntfs (rw,nls=utf8,umask=007,gid=46)
/dev/hda4 on /media/hda4 type vfat (rw,utf8,umask=007,gid=46)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)
richard@kids:~$

---

### Post by 5-HT on 2007-07-11
Was that mount output obtained with the drive mounted?
I doubt that procusb is the actual drive and would take a guess that it would be a /dev/xxx device. Perhaps /dev/hda4? If you're not sure what the device is, you can always just navigate to its mount point (/media/hda4 for /dev/hda4) to take a look at the files. Alternatively, plugging in the drive and running 'dmesg' should spit out some information as to what the drive is being recognized as.

cheers,

---

### Post by scxtt on 2007-07-11
```
procbususb on /proc/bus/usb type usbfs (rw)
```that has nothing to do w/ a specific, physically mounted usb stick ... it's more to do w/ giving you the ability to plug them in and be registered as usbfs, like a layer b/t the usb stick and the OS ... it's not that, specific stick ...

---

### Post by ginestre on 2007-07-11
Thanks again.  That was a readout on inserting the USB stick and not finding it recognised.  And going in an icon view to /media only gives me hda1, hda4 - which are my hds, while hda5 is the swapfile space. So maybe it's hda2? That's on the printout. But how to tell? Is it mounted or not, that is the question!
I tried dmesg as you suggested and got pages of

[13003.995389] sdb : status=0, message=00, host=1, driver=00 
[13003.995404] sdb : sense not available. 
[13003.996872] sdb: Write Protect is off
[13003.996889] sdb: Mode Sense: 00 00 00 00
[13003.996892] sdb: assuming drive cache: write through
[13003.998361] sdb : READ CAPACITY failed.
[13003.998365] sdb : status=0, message=00, host=1, driver=00 
[13003.998377] sdb : sense not available. 
[13003.999210] sdb: Write Protect is off
[13003.999228] sdb: Mode Sense: 00 00 00 00
[13003.999232] sdb: assuming drive cache: write through


which looks, frankly, scary.

---

### Post by scxtt on 2007-07-11
it won't be **hd*** anything, since USB sticks use the scsi subsystem (?) and will show up as **s**d* ... looks like it's sdb ... if it doesn't show up for **mount**, 99.9% of the time that means it isn't mounted ...

---

### Post by ginestre on 2007-07-11
Thanks guys: it looks as if if just didn't mount. I pulled it out and it didn't burp at me in any way, and was quite happily readable in the other machine, so it wasn't offended at me....

---

### Post by NuclearPeon on 2007-07-11
I prefer to use the **sudo eject (path) ** on my usb devices. It doesn't give me an "it's safe to remove your drive" message, but it works well.

---

### Post by forsberg on 2007-07-11
I seem to be getting the reverse.

When I am done writing stuff to a USB stick, I click unmount... then there is a message telling me DON'T remove the drive from USB as it is still writing data (even though I have already copied all my files).  After about 30 sec later the "drive" becomes "Flash Disk" and then I have to option to "mount" again, which is my cue to pull out the usb stick.

Is this normal?

---

