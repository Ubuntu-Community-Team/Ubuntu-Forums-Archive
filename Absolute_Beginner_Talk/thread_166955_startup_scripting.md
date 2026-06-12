---
title: "startup scripting"
date: 2006-04-27
forum: Absolute Beginner Talk
---

### Post by underdog5004 on 2006-04-27
Wow, after at least 2 hours of googling and searching this forum, I can't figure out how to write a startup script (is it just a plaintext document?) or how to implement one. I want my system (Breezy Badger 5.10) to mount my NTFS partition automatically. I've already specified the mount point as /media/Windows, and after another command line (something from the help file) the drive shortcut is displayed on the desktop, but it disappears when I reboot. I've tried putting the command into the 
System->Preferences->Sessions->Startup Programs...but it doesn't work. Frankly, I'm at a loss for what I should do next.

---

### Post by mostwanted on 2006-04-27
Why write a script for mounting partitions when there is already one being run for the same task?

[http://ubuntuguide.org/#automountntfs](http://ubuntuguide.org/#automountntfs)

---

### Post by bswilson on 2006-04-27
> I want my system (Breezy Badger 5.10) to mount my NTFS partition automatically. I've already specified the mount point as /media/Windows, and after another command line (something from the help file) the drive shortcut is displayed on the desktop, but it disappears when I reboot. I've tried putting the command into the
System->Preferences->Sessions->Startup Programs...but it doesn't work. Frankly, I'm at a loss for what I should do next.

You have the right idea, but you need to edit the /etc/fstab file to ensure that your NTFS partition is mounted when you boot the system up.

Let's look at the /etc/fstab file from **_my_** Ubuntu 5.10 installation, and I'll show you what you need to do:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
```

The term *fstab* means **file system table**.  It tells your computer what mount points should be used when the system is turned on.  So all you really need to do is add an entry that will connect your NTFS partition to the system.  

Step 1. Back up /etc/fstab (it's only prudent)

```
sudo cp /etc/fstab /etc/fstab.backup
```

Step 2. Edit /etc/fstab with the appropriate information

```
sudo vi /etc/fstab
```
or
```
gksudo gedit /etc/fstab
```

Then add this information at the bottom.  I used a mount point name of /dev/ hdd because that's the next available one.  You can make it up, honestly.

```
/dev/hdd     /media/Windows     ntfs,noauto     0     0
```

The part that says ntfs,noauto just means that the filesystem type is NTFS, and that it must be explicitly mounted (refer to the man page for mount).  Just save your document and reboot, you should be all set.

---

### Post by underdog5004 on 2006-04-27
Ok, I'll try this when I get home. Thanks for helping me out...I'm totally n00bish when it comes to linux.

---

### Post by tburns on 2006-04-27
[QUOTE=underdog5004]Wow, after at least 2 hours of googling and searching this forum, I can't figure out how to write a startup script (is it just a plaintext document?) or how to implement one. I want my system (Breezy Badger 5.10) [/QUOTE]


It is a plain text document with some bash (generally) and it goes in your /etc/init.d directory. Keywords to search for are init.d, rc.d, and runlevel. That should get in the general area of startup/shutdown scripting.

---

### Post by underdog5004 on 2006-04-28
Ok, I got home, and played around with the fstab (after backing it up)...but I still don't get an icon on the desktop like I do when I mount it through the command line...Oh, and do I have to start off the script with a special character string?

---

### Post by tburns on 2006-05-04
have you tried creating an shortcut to your mount point?

---

