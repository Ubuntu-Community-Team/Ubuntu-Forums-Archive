---
title: "Making an added hard drive writeable"
date: 2006-03-01
forum: Absolute Beginner Talk
---

### Post by B7may on 2006-03-01
I posted a thread the other day asking why my USB drive is only readable.  I found out that it was because the file system was NTFS.

So I need to reformat it.  

In order to do this, I added another IDE harddrive to my computer so I could copy the files from the USB drive before I format it.  Everything seems to be working fine.  I can see the drive, add files and folders.  However, when I make the new hard drive sharing and change smb.conf to look like:

[60GB_Drive]
path = /home/calvarymanagua/Drive_1
available = yes
browseable = yes
public = yes
writable = yes

(I also had at one time the additional lines of)
create mask = 0777
directory mask = 0777
force user = nobody
force group = no group

When I try to make this drive sharable (so I can use it on another computer that has Windows XP) it makes it read only from the Linux machine and my windows machine.  How can I prevent this from happening?  And how can I change this?

Thanks
Brian

---

### Post by nihilocrat on 2006-03-01
How is the extra IDE drive formatted? NTFS or FAT32, I presume?

Make sure the /etc/fstab entry for the drive is correct. I presume it should look something like this:

/dev/hdb1  /home/calvarymanagua/Drive_1   vfat   defaults,user     0  0

---

### Post by LordBug on 2006-03-01
Check the permissions on the mountpoint, /home/calvarymanagua/Drive_1 in your case.  Modify to 777 and you should be good.

---

### Post by tadashi on 2006-03-01
I made my FAT32 drive fstab like the following:

/dev/hda5  /media/shared  vfat  iocharset=utf8,umask=000  0 0

This basically give who ever logs in rw access to my shared data drive (shared between windows and linux).

---

### Post by B7may on 2006-03-01
I formated it with Fat32

I changed my Fstab to say the following:

/dev/hdb1 /home/calvarymanagua/Drive_1 vfat defaults,user 0 0

I then rebooted the computer.  The drive mounts to the correct directory, however it is read only.

I then went into terminal and typed the following:

sudo chmod 777 /home/calvarymanagua/Drive_1

It does not give me an error, but it also does not change the drive to writeable.  It stays read only?

So then I unmounted the drive (I had to do this through menus because I do not know how to do it in terminals - System - Drives ...)
I could then change the Drive to writeable through chmod

I tried to remount it using the menus - System - Drives... it changes it to read only again and I cannot change it using Chmod???

Brian

---

### Post by B7may on 2006-03-01
Also, how do I "reboot" fstab, without rebooting the computer?

---

### Post by tadashi on 2006-03-02
Add umask=000 to the options section in the fstab.

---

### Post by B7may on 2006-03-02
That fixed the problem
Thanks

---

### Post by Little_Tiger on 2006-03-02
Ok, I'm a "newbie"...I have the same problem.
First I couldn't see open it..but now I can open the external USB harddrive.
But now I want to write on it...
and just clicking the permissions isn't helping (right click  the harddrive icon check write permission)...

I can't reformat it to Fat32, (because it's a 200 GB harddrive with too much stuff on it)....so can I get this to work. so it's NTFS

and explain it to me step by step..newbie here...

thanks
-=LT=-=

---

### Post by tadashi on 2006-03-04
Linux does not play very well with NTFS.  At most you can look.  Do do not want to write to it because it may corrupt your drive.  THe only way is to copy all that data to your windows partition, format it, then copy it back.

---

