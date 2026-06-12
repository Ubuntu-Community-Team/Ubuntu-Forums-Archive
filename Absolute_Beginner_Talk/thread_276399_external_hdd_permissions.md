---
title: "external hdd permissions"
date: 2006-10-12
forum: Absolute Beginner Talk
---

### Post by nagates on 2006-10-12
hey, i have usb external hardrive and i want to copy some media files to it but i cant because its read only and linux wont let me change them the graphical way and i figure i will have to do it the sudo way, BUT HOW?

---

### Post by John.Michael.Kane on 2006-10-12
Is the external drive ntfs formated?

---

### Post by nagates on 2006-10-12
> **SD-Plissken said:**
> Is the external drive ntfs formated?Yes

---

### Post by John.Michael.Kane on 2006-10-12
Heres what i was able to find. From the looks of it theres does not seem to an easy way to change permissions,however. These threads talk about the issue,and may offer some help.

[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

[http://ubuntuforums.org/showthread.php?t=161855&highlight=change+external+hdd+permissions](http://ubuntuforums.org/showthread.php?t=161855&highlight=change+external+hdd+permissions)

[http://ubuntuforums.org/showthread.php?t=201068&highlight=change+external+hdd+permissions](http://ubuntuforums.org/showthread.php?t=201068&highlight=change+external+hdd+permissions)

---

### Post by givré on 2006-10-13
If you want read/write support, try that :
[http://ubuntuforums.org/showthread.php?t=217009](http://ubuntuforums.org/showthread.php?t=217009)

---

### Post by nagates on 2006-10-13
> **givré said:**
> If you want read/write support, try that :
[http://ubuntuforums.org/showthread.php?t=217009](http://ubuntuforums.org/showthread.php?t=217009)Hey i tired you guide but im still having some troubles, i think ive might of screwed up how things mount so if you would be willing to help me out that would be great, maybe you can pm me so i could reply easier that would be great.

error: mount point /media/usbdisk is already in /etc/fstab

error: could not execute pmount


I get this kinda error when i click on it in the Computer folder

---

### Post by givré on 2006-10-13
External device should not be set in /etc/fstab, which is for static device.
Remove it from /etc/fstab and retry.

---

### Post by nagates on 2006-10-16
> **givré said:**
> External device should not be set in /etc/fstab, which is for static device.
Remove it from /etc/fstab and retry.

alright i think i correctly removed it. **_but now i get thi_**s

failed to mount '/dev/sda1': operation not supported

mount is denied because the ntfs journal file is unclean. choices are:

 a) shutdown windows properly.

 b) click the 'safely remove hardware' icon in the windows taskbar

    notification area before disconnecting the device.

 c) use 'eject' from windows explorer to safely remove the device.

 d) if you ran chkdsk previously then boot windows again which will

    automatically initialize the journal.

 e) run 'ntfsfix' on linux which will reset the ntfs journal.

 f) mount the volume read-only by using the 'ro' mount option.

error: could not execute pmount

---

### Post by givré on 2006-10-16
nagates, simply do what he want you to do.

---

### Post by nagates on 2006-10-16
> **givré said:**
> nagates, simply do what he want you to do. well i have a giant 320gb external hdd that i started using while i still had a windows os and no i would like to be able read and write to it, If i could move all my files to my desktop and reformat the hdd drive i would(but i dont have enough space)  and the files on there are very hard to replace.

---

### Post by givré on 2006-10-16
Of course you can, but you'll have to find a windows box to clean up the ntfs journal. This is something that we can't do currently in linux. there is no equivalent to chkdsk yet. So just :
- find a windows box
- plug your HD
- Unmount it safely with the eject button of explorer, or whatever.
- unplug the HD
And that's should be ok.

EDIT : and don't forget to use the eject button before unplugging your drive the following time.

---

### Post by nagates on 2006-10-16
> **givré said:**
> Of course you can, but you'll have to find a windows box to clean up the ntfs journal. This is something that we can't do currently in linux. there is no equivalent to chkdsk yet. So just :
- find a windows box
- plug your HD
- Unmount it safely with the eject button of explorer, or whatever.
- unplug the HD
And that's should be ok.

EDIT : and don't forget to use the eject button before unplugging your drive the following time.Holly Crap that did it!!!

---

