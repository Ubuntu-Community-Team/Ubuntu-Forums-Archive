---
title: "Help mounting SATA disk"
date: 2007-03-30
forum: Absolute Beginner Talk
---

### Post by Keldair on 2007-03-30
Hello all, I am new to Linux and am working on getting my system up and running.

Install worked fine, I am just attempting to mount my SATA harddrive.

I read around some posts and I think I figured out my issue is with my fstab.

Here is my information I have seen others ask for.

fdisk:
```

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       60801   488384001    b  W95 FAT32

Disk /dev/hda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        4864    39070048+   7  HPFS/NTFS

Disk /dev/hdb: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        4664    37463548+  83  Linux
/dev/hdb2            4665        4865     1614532+   5  Extended
/dev/hdb5            4665        4865     1614501   82  Linux swap / Solaris

```

and fstab:
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hdb1
UUID=d6eb59d9-af71-449a-a55f-7a0104204e5b /               ext3    defaults,errors=remount-ro 0       1
# /dev/hdb5
UUID=df72df6d-ad54-437f-8f9c-d383077fb80b none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0

```

I saw some information on adding something to the fdisk but I am not quite sure what .  Any help mounting my drive?

---

### Post by Scunizi on 2007-03-30
Here's my fstab with a mix of SATA drives and IDE.  I can read a NTFS partition but haven't set it up to write, and probably won't at this point.  You also need to creat a mount point for it in /media.  With the label on your drive sda1 all you have to do from the terminal is type "sudo mkdir /media/sda1".  Now for your system to relook at /etc/fstab and /media and give you access.... well I know there is an easier way but I don't know it.  I just reboot and VIOLA!  It's there.

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sdb3       /               reiserfs notail          0       1
/dev/sda1       /media/sda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
/dev/sdb1       /media/sdb1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
/dev/sdb5       /media/sdb5     vfat    defaults,utf8,umask=007,gid=46 0       1
/dev/sdb6       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/hda1	/media/hda1	vfat	user,auto,fmask=0111,dmask=0000
```

---

### Post by Keldair on 2007-03-30
Ok Scunizi, I tried your suggestion and got no reply from the terminal.  Good so far, so I rebooted.

No change to fstab and still unable to mount the drive.  Any other suggestions?

---

### Post by nike984 on 2007-03-30
there isn't any comment about SATA disk in your fstab file, 
neither the hda2 extended partition.

---

### Post by Keldair on 2007-03-30
Ok how do I get the information into fstab?

---

### Post by Scunizi on 2007-03-30
To add the information to fstab, from the terminal type "sudo gedit /etc/fstab".  Gedit is a text editor and will open fstab showing you what's inside.  Take a look at my posted fstab.  My sdb5 is the line you want to add changing sdb5 referances to sda1.  As for your hdb2 extended partition that is mearly an extended partiton referance for your hdb5 swap partition.  You can tell they are the same by the beginning and ending blocks.

---

### Post by alien21010 on 2007-03-30
You need to edit your /etc/fstab file.  You can use vim or any other text editor to edit the file.  So you would do, sudo vim /etc/fstab.  It's a good idea to make a backup copy first, in case you make some changes that you do not want (sudo cp /etc/fstab /etc/fstab.bak or something like that).

Add the following line to your /etc/fstab.

/dev/sda1       /media/windows (or wherever you want to mount it)     vfat    defaults,utf8,umask=007,gid=46 0       1

After you add this to /etc/fstab, you can remount everything by typing:  sudo mount -a instead of rebooting.

Hope this helps.

BTW, /etc/fstab determines what to mount on boot.  If you only want to mount it temporarily, once in a while you could use sudo mount -t vfat -o uid=1000 /dev/sda1 /media/windows

---

### Post by Keldair on 2007-03-30
Ok I tried Alien's advice and no go.  I tried the temporary mount that Alien suggested and that does not work either.  Same error, posted below
```

mount: mount point /media/windows does not exist

```

This is my new fstab:
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hdb1
UUID=d6eb59d9-af71-449a-a55f-7a0104204e5b /               ext3    defaults,errors=remount-ro 0       1
# /dev/hdb5
UUID=df72df6d-ad54-437f-8f9c-d383077fb80b none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0
/dev/sda1       /media/windows  vfat defaults,utf8,umask=007,gid=46 0 1

```

Thank you for your patience so far, I hope we can get this worked out.

---

### Post by Scunizi on 2007-03-31
The reason being you tried to mount it to /media/windows.  You haven't created a directory in /media called windows.  I think you did create one called sda1 though.  Try the same command again and substitute sda1 for windows, and initiate the "sudo mount -a" command from the terminal.

---

### Post by SentientFluid on 2007-03-31
What Scunizi says sounds right.  In your fstab, where you have "/dev/sda1    /media/windows", you're telling the operating system to mount the first partition on your SATA drive to the "windows" folder inside "media".  If that "windows" folder doesn't exist, then it's not going to moutn anything.

Type this into Terminal, pressing RETURN after each line:

```
sudo mkdir /media/windows
sudo mount -a
```

In case you didn't know, the "vfat" in your fstab is telling it to mount it as FAT32.  If your SATA drive is formatted as something else (NTFS, for example), then you're most likely going to have some problems.

---

### Post by Scunizi on 2007-03-31
What SentientFluid and I said are both correct.  SentientFluid, I had Keldair create a sda1 directory in /media in one of my earlier posts so your method or mine will work the same.

---

### Post by Keldair on 2007-03-31
Solved!

SentientFluid and Scunizi thank you much!  I now have a working folder in my media folder called windows that shows all the files in the drive.  

Thank you for your patience.

---

### Post by SentientFluid on 2007-03-31
> **Scunizi said:**
> What SentientFluid and I said are both correct.  SentientFluid, I had Keldair create a sda1 directory in /media in one of my earlier posts so your method or mine will work the same.

I see.. I must have missed that, sorry.  :)

---

