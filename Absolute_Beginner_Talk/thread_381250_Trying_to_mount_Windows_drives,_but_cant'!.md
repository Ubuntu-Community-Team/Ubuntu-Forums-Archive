---
title: "Trying to mount Windows drives, but cant'??!"
date: 2007-03-10
forum: Absolute Beginner Talk
---

### Post by cynon83 on 2007-03-10
Hi,
  I'm not exactly new to linux, but I'm fairly new, and I've been running into some odd problems trying to mount and access my windoze XP drives with Ubuntu 6,06.  There are really some odd things going on, and I could use a hand :)

The system is Windoze XP and Ubuntu 6.06

Here is what my fstab looks like:
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda3       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda7       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd5       /mnt/win_BU1    vfat    iocharset=utf8,umask=000        0       0
/dev/hdd6       /mnt/win_BU2    vfat    iocharset=utf8,umask=000        0       0

Please note the following, because it's really odd.
I can access /mnt/win_BU2 (as either a user or root -- and I'll get into that user vrs. root thing in a minute), but I cannot access /mnt/win_BU1.

They are both fat32 drives.  There is data on both.  And calling up the Disks manager shows that I have the correct device name /dev/hddX.  So, hdd5 mounts with no errors, but doing an ls on it shows no files, and hdd6 mounts with no errors and doing an ls on that, shows all the data on the disk.  And yes, there is data on hdd5.  Hitting the browse button in the Disks manager shows data on hdd6 but not on hdd5.  This is really, really strange.
Oh, here is the directory read out in /mnt 
drwxrwxrwx  2 root root 4096 2007-03-10 14:59 win_BU1
drwxrwxrwx  9 root root 4096 1969-12-31 19:00 win_BU2


Moving on.

Used to be, when I clicked on Places->Computer, I could see most of the NTFS drives on the system.  Not that I could actually click on them without getting an error, but they were there.  hdd6 wasn't though -- I could only get to that by navigating to /mnt/win_BU2.  Now, after I added the /mnt/hdd5 line in my fstab (and rebooted of course, there's been lots of that), those drives no longer show up.  Does anyone have any idea why?

Also, does anyone have any idea how I could have all my widoze drives listed and accessable by a standard user?  I made a link  in my user directory to the /mnt/win_BU2 and that gets me to that drive easily enough.  Even as a non root user, but then, I had to chmod the /mnt/win_BU2 to all 777 to make that happen.

And as for the NTFS stuff?  I'm resigned to the fact that linux won't write to it, but I know I should be able to read it, and because Ubuntu (which, BTW, I really like, for the most part) uses this sudo thing, it's really screwing me up.

How do I make all these drives accessble in the file browser, and how do I get them to mount correctly?  I haven't even tried the NTFS drives because I can't get the second FAT32 drive to work.  I did the other one months ago, but I've only just started getting my Ubuntu in shape for every day use recently.

Anyway, that'll do for a start.  Help from you gurus (or anyone else that knows what they're doing) would be most welcome.

Thanks!

---

### Post by wj32 on 2007-03-10
Instead of mounting in /mnt, mount in /media. I think GNOME, KDE and friends prefer /media. For NTFS, you can write to NTFS using ntfs-3g.

*sudo mkdir /media/win_BU1 /media/win_BU2*

---

### Post by cynon83 on 2007-03-10
Forgive me, but that doesn't seem to make sense.  the /mnt directory is there for a reason, and besides, I can't see what difference it would make?  Surely mounting is a standard Linux function, right??

---

### Post by astrolabio on 2007-03-10
Your problem is very odd.

But you can write ntfs. 

sudo apt-get install ntfs-3g

then you have to use ntfs-3g instead ntfs in your fstab file.

To make your partition writable to all users i usually use something like that. But you should consult the manual because i don't remember well i do i get to that line :)

/dev/hda5 /media/D ntfs-3g users,user,atime,auto,rw,nodev,noexec,nosuid,umask=007,gid=46,locale=en_US.utf8 0 0

Beside may i ask how big are those partitions?

---

### Post by cynon83 on 2007-03-10
The FAT23 partitions are around 160GB (or so) each.
And yes, the problem is quite odd.  is there anyway, other than command line tools, that one can add drives to the fstab?

---

### Post by wj32 on 2007-03-10
Yes, but GNOME and friends only look in /media for mounted stuff.

---

### Post by cynon83 on 2007-03-10
> **wj32 said:**
> Yes, but GNOME and friends only look in /media for mounted stuff.

Okay.  However, that doesn't explain why I can't get hdd5 to mount and access it even from the command line.  It really is very very strange.

---

### Post by cynon83 on 2007-03-11
> **astrolabio said:**
> Your problem is very odd.

But you can write ntfs. 

sudo apt-get install ntfs-3g

then you have to use ntfs-3g instead ntfs in your fstab file.

To make your partition writable to all users i usually use something like that. But you should consult the manual because i don't remember well i do i get to that line :)

/dev/hda5 /media/D ntfs-3g users,user,atime,auto,rw,nodev,noexec,nosuid,umask=007,gid=46,locale=en_US.utf8 0 0

Beside may i ask how big are those partitions?

My problem is that I'm an idiot.  The partition isn't fat 32, it's NTFS.  I was sure when I added that last data disk, I specifically formatted the thing into 2 FAT32 drives, but no, I didn't.  

So, now I'm off to try this ntfs-3g thing, in hopes that that will work.

Thanks again for all the help.

---

