---
title: "Help with LiveCD file recovery!  Quick response needed!"
date: 2007-04-13
forum: Absolute Beginner Talk
---

### Post by thedesign3r on 2007-04-13
Hello, I was wondering if I could obtain some assistance with using the LiveCD as a recovery tool for a crashed Windows machine.  My friends laptop won't boot into XP anymore, so I was planning to use the LiveCD along with an external USB drive to pull his data off and reformat.  I found, however, that I wasn't able to access his files through Ubuntu, which I think may be due to the fact that his windows account was password protected.  If this is the case, aside from getting the password from him, what do I need to do on the LiveCD to permit access to the windows file system?  Any help would be greatly appreciated, thanks!

---

### Post by mac.ryan on 2007-04-13
If it was just the user to have a password, you probably won't need to use it. Just [mount the windows partition into ubuntu]("http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Windows_with_Dapper_Desktop"), and then copy all the files you need into a new partition.

---

### Post by confused57 on 2007-04-13
Here's how to mount a Window's partition, using the live cd:
[http://users.bigpond.net.au/hermanzone/p10.htm](http://users.bigpond.net.au/hermanzone/p10.htm)

---

### Post by Seisen on 2007-04-13
You can also try using Knoppix, it has came in handy many time for me.

```
http://www.knoppix.org/
```

---

### Post by n3tfury on 2007-04-13
Knoppix would be a good alternative live cd

---

### Post by n3tfury on 2007-04-13
> **Seisen said:**
> You can also try using Knoppix, it has came in handy many time for me.

```
http://www.knoppix.org/
```

darn you.

---

### Post by thedesign3r on 2007-04-14
Ok, so I managed to get it mounted, after much trial and error.  But I can't seem to get the data transferred off it to the external USB hard drive I have hooked up!  it says I don't have permission to write to the external drive.  Is there a command that I need to run in the terminal in order to allow me to get these files off?  I'm so close, thanks for all of your help!

---

### Post by confused57 on 2007-04-14
> **thedesign3r said:**
> Ok, so I managed to get it mounted, after much trial and error.  But I can't seem to get the data transferred off it to the external USB hard drive I have hooked up!  it says I don't have permission to write to the external drive.  Is there a command that I need to run in the terminal in order to allow me to get these files off?  I'm so close, thanks for all of your help!

There's probably a GUI way of changing permissions...possibly something like "gksudo nautilus" in the terminal, then navigate to the directory where your external hd is mounted, right-clicking, then changing the permissions.

From a terminal, you might try:
```
sudo mount
```
to determine the mountpoint of your external drive
to unmount:
```
sudo umount /media/external
```
substitute your mountpoint for "/media/external"
then to remount with permissions:
```
sudo mkdir /media/external
sudo mount /dev/sda1 /media/external -t vfat -o umask=000
```

I've never tried any of this, so I don't know if it'll work or not.

Added: I assume your external drive is FAT32, if it's NTFS, then you won't be able to write to it.  If the above works, make sure to unmount your external drive after you've finished copying files

---

### Post by thedesign3r on 2007-04-14
are all NTFS formatted drives unwritable in ubuntu?  that would be my problem...maybe ill give knoppix a try...

---

### Post by mac.ryan on 2007-04-14
> **thedesign3r said:**
> are all NTFS formatted drives unwritable in ubuntu?  that would be my problem...maybe ill give knoppix a try...

Parts of the NTFS filesystem are "industrial secret" by Microsoft, for this reason drivers have been back-engineered, and this made them less stable than the EXT2/3, Reiser, FAT, etc... For "safety reasons" ubuntu chose to only allow reading from NTFS.

You can however under any GNU/Linux distro install the support for writing on them. It is called **ntfs-3g**. Under ubuntu I used [this how-to]("http://ubuntuforums.org/showthread.php?t=217009") months ago, but then I totally converted to EXT3, so I am unaware it if is still up-to date.

---

### Post by lamalex on 2007-04-14
use the new knoppix, it has ntfs read-write built in to it.

---

