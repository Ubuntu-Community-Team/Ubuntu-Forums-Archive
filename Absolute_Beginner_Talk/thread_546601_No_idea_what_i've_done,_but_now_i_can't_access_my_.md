---
title: "No idea what i've done, but now i can't access my NTFS disks :|"
date: 2007-09-09
forum: Absolute Beginner Talk
---

### Post by DAE_JA_VOO on 2007-09-09
They ARE there, but i can't mount them. And when i try to do "sudo mount -a" i get this:

> $LogFile indicates unclean shutdown (0, 0)
Failed to mount '/dev/disk/by-uuid/AEB80E51B80E190B': Operation not supported
Mount is denied because NTFS logfile is unclean. Choose one action:
   Boot Windows and shutdown it cleanly, or if you have a removable
   device then click the 'Safely Remove Hardware' icon in the Windows
   taskbar notification area before disconnecting it.
Or
   Run ntfsfix version 1.13.1 on Linux unless you have Vista.
Or
   Mount the NTFS volume with the 'ro' option in read-only mode.
$LogFile indicates unclean shutdown (0, 0)
Failed to mount '/dev/disk/by-uuid/5E24F4E724F4C2D7': Operation not supported
Mount is denied because NTFS logfile is unclean. Choose one action:
   Boot Windows and shutdown it cleanly, or if you have a removable
   device then click the 'Safely Remove Hardware' icon in the Windows
   taskbar notification area before disconnecting it.
Or
   Run ntfsfix version 1.13.1 on Linux unless you have Vista.
Or
   Mount the NTFS volume with the 'ro' option in read-only mode.
$LogFile indicates unclean shutdown (0, 0)
Failed to mount '/dev/disk/by-uuid/24B04C2CB04C06B0': Operation not supported
Mount is denied because NTFS logfile is unclean. Choose one action:
   Boot Windows and shutdown it cleanly, or if you have a removable
   device then click the 'Safely Remove Hardware' icon in the Windows
   taskbar notification area before disconnecting it.
Or
   Run ntfsfix version 1.13.1 on Linux unless you have Vista.
Or
   Mount the NTFS volume with the 'ro' option in read-only mode.


I've been struggling to get the disks mounted in such a way that i can write to them, and now i can't mount them at all :|

Any help would be appreciated :D

---

### Post by Sef on 2007-09-09
Try [GParted]("http://gparted.sourceforge.net").   I have problems booting up and I have used it to fix that.

---

### Post by DAE_JA_VOO on 2007-09-09
Okay, well, i downloaded gparted, and once it was finished scanning my disks, it gave me this view:

[IMG]http://i29.photobucket.com/albums/c267/DAE_JA_VOO/more2/gparted2.png[/IMG]



There's no "mount" or anything like that, what should i do?

---

### Post by DAE_JA_VOO on 2007-09-09
Anyone?

---

### Post by Gone fishing on 2007-09-09
it looks like the ntfs partition is unclean. can you boot into windows and tell it to check the disks on next boot and then reboot into XP and let chkdsk do its stuff? If Windows will not boot, start up on the XP startup disk and then run chkdsk from the console and fix the problems?

I seem to remember that you can force a mount but I'd try and fix the ntfs partition.

---

### Post by dwhitney67 on 2007-09-09
I dunno about your system, but all I have to do is select **Applications -> System Tools -> NTFS Configuration Tool** to setup my NTFS external drive.  Now, each and everytime I connect my external drive, and then power it on, Ubuntu auto-mounts it and displays the folder in a UI window.

If you do not have that tool, then go [here]("http://www.ubuntugeek.com/widows-ntfs-partitions-readwrite-support-made-easy-in-ubuntu-feisty.html") (and pass this info on to the next newbie).  There is no need to muck with your /etc/fstab!

---

