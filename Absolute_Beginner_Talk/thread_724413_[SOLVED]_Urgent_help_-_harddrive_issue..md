---
title: "[SOLVED] Urgent help - harddrive issue."
date: 2008-03-14
forum: Absolute Beginner Talk
---

### Post by lover_of_sc on 2008-03-14
All, 

I tried to explain my problem in a previous tread, but I problebly came out as being absolutely hopeless,.. So I try again.

I have a problem with one of my partitions (sdb1), it's a NTFS partition and I need the information stored on that drive. here is the printout from fstab:

--------------
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=ea889b08-6025-4ee8-ac7c-6bf88f0fcda6 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=ecde84c1-26d9-415b-a529-8745c4fba59f /home           ext3    defaults        0       2
# /dev/sdb1
UUID=6694794B94791EAD /media/sdb1     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sdb5
UUID=5aaa7a8c-7560-4afc-bab2-bdfd80055cf0 /media/sdb5     ext3    defaults        0       2
# /dev/sda6
UUID=3aa0bea0-64d4-4a1e-8e3c-5a0b8aed5d39 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0

-------------

Here is the printout from fdisk:


----------------

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf5966b27

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1824    14651248+  83  Linux
/dev/sda2            1825       19457   141637072+   5  Extended
/dev/sda5            2073       19457   139645012+  83  Linux
/dev/sda6            1825        2071     1983964+  82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1de2c90e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       17108   137419073    7  HPFS/NTFS
/dev/sdb2           17109       19214    16916445    5  Extended
/dev/sdb5           17109       19214    16916413+  83  Linux
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf5966b27

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1824    14651248+  83  Linux
/dev/sda2            1825       19457   141637072+   5  Extended
/dev/sda5            2073       19457   139645012+  83  Linux
/dev/sda6            1825        2071     1983964+  82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1de2c90e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       17108   137419073    7  HPFS/NTFS
/dev/sdb2           17109       19214    16916445    5  Extended
/dev/sdb5           17109       19214    16916413+  83  Linux

-----------------

I can find the drive but i can not see any files in it, I have tried gparted and an error message states that it can not read the information? There is no mount point on it as well.

plz help poor me, I have all my photos stored on that drive. :-(

regards
anders

---

### Post by taurus on 2008-03-14
What happens when you run this command from a terminal?

```
sudo mount -t ntfs /dev/sdb1 /media/sdb1 -o umask=0222
```

---

### Post by lover_of_sc on 2008-03-14
This is what i get mate, thx.

$LogFile indicates unclean shutdown (0, 0)
Failed to mount '/dev/sdb1': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the 'Safely Remove Hardware' icon in the Windows
          taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/sdb1 /media/sdb1 -o force

    Or add the option to the relevant row in the /etc/fstab file:

            /dev/sdb1 /media/sdb1 ntfs-3g defaults,force 0 0

---

### Post by Oldsoldier2003 on 2008-03-14
> **lover_of_sc said:**
> This is what i get mate, thx.

$LogFile indicates unclean shutdown (0, 0)
Failed to mount '/dev/sdb1': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the 'Safely Remove Hardware' icon in the Windows
          taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/sdb1 /media/sdb1 -o force

    Or add the option to the relevant row in the /etc/fstab file:

            /dev/sdb1 /media/sdb1 ntfs-3g defaults,force 0 0

boot into windows and do a clean shutdown, wouldn't hurt to do a chkdisk and defrag while you're there.  Or alternatively you could force the mount, but its better to reset the dirty bit from within winders in my opinion.

---

### Post by taurus on 2008-03-14
Do you still have windows on your machine?  You need to boot it up and shut it down cleanly, means no hibernation.  

Otherwise, you can use the force option to mount it so you can copy whatever you need off it for now.

```
sudo mount -t ntfs-3g /dev/sdb1 /media/sdb1 -o force
ls -la /media/sdb1
```

---

### Post by lover_of_sc on 2008-03-14
I removed my previous windows vista, so I did the force mount command and it worked!!! :) Thanks guys!!!!

I am moving all of my files to my sda drive at the moment. What is the easiest way of changing the entire sdb to EXT3?

---

### Post by taurus on 2008-03-14
1.  Unmount it.

```
sudo umount /media/sdb1
```

2.  Use gparted, System -> Administration (and if you don't have it, install it), and format it to ext3.

3.  Edit /etc/fstab and change the entry for /dev/sdb1 to

```
/dev/sdb1   /media/sdb1   ext3   defaults   0   1
```

4.  Reboot.

---

### Post by lover_of_sc on 2008-03-14
brilliant, thanks again! 

I have merged the entire sdb into one partition with EXT format, not sure if its mounted properly?

Think I may have to do another force mount?


Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xf5966b27

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    29302559    14651248+  83  Linux
/dev/sda2        29302560   312576704   141637072+   5  Extended
/dev/sda5        33286680   312576704   139645012+  83  Linux
/dev/sda6        29302686    33270614     1983964+  82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x1de2c90e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63   312576704   156288321   83  Linux
anders@anders-laptop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=ea889b08-6025-4ee8-ac7c-6bf88f0fcda6 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=ecde84c1-26d9-415b-a529-8745c4fba59f /home           ext3    defaults        0       2
# /dev/sdb1
UUID=6694794B94791EAD /media/sdb1     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sdb5
UUID=5aaa7a8c-7560-4afc-bab2-bdfd80055cf0 /media/sdb5     ext3    defaults        0       2
# /dev/sda6
UUID=3aa0bea0-64d4-4a1e-8e3c-5a0b8aed5d39 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0

---

### Post by taurus on 2008-03-14
Edit /etc/fstab

```
gksudo gedit /etc/fstab
```
and remove these lines since you don't have /dev/sdb5 and your new /dev/sdb1 is ext3 now instead of ntfs.

```

# /dev/sdb1
UUID=6694794B94791EAD /media/sdb1 ntfs defaults,umask=007,gid=46 0 1
# /dev/sdb5
UUID=5aaa7a8c-7560-4afc-bab2-bdfd80055cf0 /media/sdb5 ext3 defaults 0 2

```
Then, add this line to the end of it.

```
/dev/sdb1   /media/sdb1   ext3   defaults   0   1
```
Save it and close down gedit window.  Now, either reboot or just mount it with

```
sudo mount -a
```
At this point, you want to be able to write to /media/sdb1 without using sudo so you need to change the ownership of /media/sdb1 from root to your login name, _assuming_ your login name is **lover**.

```
sudo chown -R **lover**:**lover** /media/sdb1
ls -la /media
```

---

### Post by lover_of_sc on 2008-03-14
Thanks a lot mate, sorry to ruin your Friday evening! :-)

sdb1 appears to be ok now, although I still get an error message on sda1?

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
**UUID=ea889b08-6025-4ee8-ac7c-6bf88f0fcda6 /               ext3    defaults,errors=remount-ro 0       1**
# /dev/sda5
UUID=ecde84c1-26d9-415b-a529-8745c4fba59f /home           ext3    defaults        0       2
/dev/sdb1   /media/sdb1   ext3   defaults   0   1
# /dev/sda6
UUID=3aa0bea0-64d4-4a1e-8e3c-5a0b8aed5d39 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0

My external hard drive also get an error message as soon as I plug it in - I assume those issues are linked?

Once again, many thanks! I can write to sdb1 now :-)

---

### Post by taurus on 2008-03-14
What kind of error message do you get with /dev/sda1, root partition?  Does it complain about wrong UUID?

---

### Post by lover_of_sc on 2008-03-14
The hard drive appears to be ok, but as soon as i plug in my external usb (NTFS) hard drive - then a big error message appears:

Can not mount the volume DATA and under details:

$Logfile indicates unclean shutdown (0, 0). Failed to mount /dev/sdc1 NTFS is marked as being in use

Does that help mate?

---

### Post by taurus on 2008-03-14
You need to plug that external harddrive to a windows machine again.  Then, unmount it safely instead of just unplug if when you are finished using it.  There should be an icon next to the clock in the lower right corner.  Use that to unmount your external drive in windows.

---

### Post by lover_of_sc on 2008-03-14
Hmm must be something else that's wrong. Because it worked perfectly fine before i started my attempt in getting the other partitions to work properly? I have also tried to plug it into a windows computer as you said - but I get the same message...

Any other ideas? Considering reinstalling ubuntu from scratch again?

---

### Post by taurus on 2008-03-14
Is there anything on that external drive?  Why don't you run a checkscan and defrag on that drive from windows.  See if that fixes the problem.

---

### Post by notbitmonk on 2008-03-14
I don't think that you need to reinstall Ubuntu.  You may need to do what was previously suggested and force mount.  Also, if you haven't done chown, check chmod -R 777 /media/sdb1.  I had similar troubles and chmod fixed it for me.  Notice that what this does is give permission to any user to read and write to the disk.  Also, I don't think that the bit in fstab about error is not really an error (check bodhi.zazen [post on fstab]("http://ubuntuforums.org/showthread.php?t=283131")).  This is my fstab file:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=cd66c0e6-1b0a-4546-bfc3-b0cc4bac047a /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda1
UUID=76417f6a-fe1c-46e9-b23c-de6919cd745a /media/hda1     ext3    defaults        0       2
# /dev/sda1
UUID=c819aaf3-59bc-4733-8c5f-0b68ee377b89 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0

```
So far, my computer works OK.

---

### Post by lover_of_sc on 2008-03-14
Oh, it finally works! :-) The scandisc and defreag helped it up and running. Thanks a lot for your patients and skills. It's very appreciated. :-)

---

