---
title: "User access outside of /home"
date: 2006-03-17
forum: Absolute Beginner Talk
---

### Post by triviadave on 2006-03-17
Hi all,  I have just installed Ubuntu on a computer I intend to use as a sort of media centre in my living room (eventually installing Myth TV on it).  I have two hard disks, a 20 Gb and a 40 Gb.  I have installed ubuntu on the 20 Gb disk with the intention of using that to contain the entire installation and /home, and then to use the 40 Gb disk as a media store, which can be accessed ,and written to, by all users.  At the moment, the 40 Gb disk can only be written to as root, and always logging in as root is obviously not an option.

Does anyone have any ideas about the best way to set up such a system?  Just to complicate matters further, the 40 Gb disk, is formatted as FAT 32, so that other computers (running Windows) can also read the drive.

Thanks for any help you can offer.

---

### Post by triviadave on 2006-03-17
Sorry, I forgot to mention, I have already tried chown to reassign the permissions for the drive away from root, and also logging in as root, and graphically adding write access for users from the "permissions" tab in the "properties" option after right clicking on the drive, and also a folder created within the drive.  Neither of these worked, the chown output said the operation could not be performed, and the graphical method added a tick momentarily, only for it to disappear within a second.

---

### Post by Swab on 2006-03-17
edit your fstab by sudo gedit /etc/fstab


find the line that relates to your fat32 drive... and make it look like the following.. substituting /dev/hda1 for your partition....

/dev/hda1       /whereyouwantotmount  vfat    iocharset=utf8,umask=000   0       0

then reboot and all users should have access..

---

### Post by taurus on 2006-03-17
[QUOTE=Swab]
/dev/hda1       /whereyouwantotmount  vfat    iocharset=utf8,umask=000   0       0
[/QUOTE]
I think there should be 4 0s after umask, umask=0000...

---

### Post by pbaehr on 2006-03-17
Also, just so you know, if you're using Samba to share the second drive with the Windows machines you don't need it to be formatted as fat32. I prefer to use ext3 as it requires less maintanance. Windows machines can't tell the difference when they're connecting through Samba. They will still be able to read or write to it fine.

---

### Post by triviadave on 2006-03-17
Thanks very much everyone, it works now :) (I used three zeroes in the end and it seems fine, but time will tell).

I didn't realise that about Samba, I'm tempted to change the drive before I fill it up with stuff.

---

### Post by pbaehr on 2006-03-17
If it's empty you may as well, I guess. As far as I know there are only advantages to using ext3 over fat32. Then there's ReiserFS, too. I know a lot of people back that.

I just like to keep my drives native to the system that they reside in. It's not necessary for Linux, but it just feels right.

Edit: By the way, if you do change it to ext3 or something similar the fstab entry will be different...mine is:
```
/dev/hdb1    /mnt/hdb1    ext3    defaults    0    0
```

You don't need all that umask stuff if you're not using fat32...at least in my experience.

---

