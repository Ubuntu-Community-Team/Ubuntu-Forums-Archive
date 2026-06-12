---
title: "Can not mount external HDD with ubuntu 7.10"
date: 2008-02-08
forum: Absolute Beginner Talk
---

### Post by copperco2 on 2008-02-08
I have recently installed ubuntu 7.10 and all the required security updates.
the file system is identified as NTFS and earlier i was it was FAT32 under windows...

the problem now is that , i have taken the back up of all my mails, totaling upto 3GB of disk space on external HDD which now i can not mount as it is identified as FAT32....
as it was under windows...
can anybody help me with that..
It was working fine with windows....

I have installed ubuntu over windows so i seem to have lost about 5gb of disk space that too will be required to gain back...

i am a novice when it comes to technology, pl. help.

---

### Post by taurus on 2008-02-08
Can you post the outputs of these commands from a terminal?

Applications -> Accessories -> Terminal
```
sudo fdisk -l
cat /etc/fstab
df -h
```

---

### Post by copperco2 on 2008-02-08
ajay-mani@Ajay-Mani:~$ sudo fdisk -l

Disk /dev/sda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x3a593a58

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4679    37584036   83  Linux
/dev/sda2            4680        4864     1486012+   5  Extended
/dev/sda5            4680        4864     1485981   82  Linux swap / Solaris

ajay-mani@Ajay-Mani:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=c8cd68ad-3b51-4315-8ff8-33345683d0a0 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=4caee33e-e86b-419a-8786-695e9ca2d176 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0

ajay-mani@Ajay-Mani:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=c8cd68ad-3b51-4315-8ff8-33345683d0a0 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=4caee33e-e86b-419a-8786-695e9ca2d176 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0


I have done it according to your guidance. thanks.

---

### Post by taurus on 2008-02-08
Is your external harddrive plugged in and on because I don't see it on the list at all?  What's the output of this command from a terminal then?

```
dmesg | tail
```

p.s.  You just posted the output of the second command twice.

---

### Post by rzrgenesys187 on 2008-02-08
Do you get any errors when the drive is plugged in?  Also have you tried going into Places >> Computer.  Is there an icon there?  One last question was the drive connected when you ran the terminal commands above?

---

### Post by copperco2 on 2008-02-09
jay-mani@Ajay-Mani:~$ sudo fdisk -l

Disk /dev/sda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x3a593a58

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4679    37584036   83  Linux
/dev/sda2            4680        4864     1486012+   5  Extended
/dev/sda5            4680        4864     1485981   82  Linux swap / Solaris

Disk /dev/sdb: 80.0 GB, 80026361344 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x727ae075

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        9729    78148161    7  HPFS/NTFS

ajay-mani@Ajay-Mani:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=c8cd68ad-3b51-4315-8ff8-33345683d0a0 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=4caee33e-e86b-419a-8786-695e9ca2d176 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0


ajay-mani@Ajay-Mani:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=c8cd68ad-3b51-4315-8ff8-33345683d0a0 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=4caee33e-e86b-419a-8786-695e9ca2d176 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
ajay-mani@Ajay-Mani:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              36G  2.1G   32G   7% /
varrun                248M   92K  248M   1% /var/run
varlock               248M     0  248M   0% /var/lock
udev                  248M   84K  248M   1% /dev
devshm                248M     0  248M   0% /dev/shm
lrm                   248M   34M  214M  14% /lib/modules/2.6.22-14-generic/volatile


the above result is after i plug in the external HDD

ajay-mani@Ajay-Mani:~$ dmesg | tail
[ 5865.612000] sd 3:0:0:0: [sdb] Write Protect is off
[ 5865.612000] sd 3:0:0:0: [sdb] Mode Sense: 03 00 00 00
[ 5865.612000] sd 3:0:0:0: [sdb] Assuming drive cache: write through
[ 5865.612000] sd 3:0:0:0: [sdb] 156301487 512-byte hardware sectors (80026 MB)
[ 5865.616000] sd 3:0:0:0: [sdb] Write Protect is off
[ 5865.616000] sd 3:0:0:0: [sdb] Mode Sense: 03 00 00 00
[ 5865.616000] sd 3:0:0:0: [sdb] Assuming drive cache: write through
[ 5865.616000]  sdb: sdb1
[ 5865.640000] sd 3:0:0:0: [sdb] Attached SCSI disk
[ 5865.640000] sd 3:0:0:0: Attached scsi generic sg2 type 0

thanks.

---

### Post by taurus on 2008-02-09
```
sudo apt-get update
sudo apt-get install ntfs-3g
sudo mkdir /media/sdb1
sudo mount -t ntfs-3g /dev/sdb1 /media/sdb1
ls -la /media/sdb1
```

---

### Post by copperco2 on 2008-02-09
> **rzrgenesys187 said:**
> Do you get any errors when the drive is plugged in?  Also have you tried going into Places >> Computer.  Is there an icon there?  One last question was the drive connected when you ran the terminal commands above?

yes, there is an icon. It recognises the external HDD.
The recent result pasted for the reference are after i have connected the external HDD.
. 
there is an error message that says "Cannot mount volume. Unable to mount the volume 'Manaj'."
Details $logfile indicates unclean shutdown (0,0) failed to mount '/dev/sdb1': operation not supported mount is denied because NTFS is marked to be in use. choose one action: choice 1: if you have windows then disconnect the external devices by clicking on the 'safely remove hardware' icon in the windows taskbar then shutdown windows cleanly. choice 2: if you dont have windows then you can use the force option for your own responsibility. for example type on the command line: mount -t ntfs-3g/dev/sdb1/media/manaj -o force Or add the option to the relevent row in the /etc/fstab file: /dev/sdb1 /meia/Manaj ntfs, force 0 0"

---

### Post by taurus on 2008-02-09
Looks like you just probably unplugged that drive while you are in windows instead of safely eject it.  Therefore, connect it back to a windows machine and safely and cleanly eject the drive.  Then, you shouldn't have problem mounting it again in Ubuntu.

Otherwise, you have to use the force option to mount it.

---

### Post by copperco2 on 2008-02-09
> **taurus said:**
> ```
sudo apt-get update
sudo apt-get install ntfs-3g
sudo mkdir /media/sdb1
sudo mount -t ntfs-3g /dev/sdb1 /media/sdb1
ls -la /media/sdb1
```

i tried these and i was greeted by the message that said
"ajay-mani@Ajay-Mani:~$ sudo mkdir /media/sdb1
ajay-mani@Ajay-Mani:~$ sudo mount -t ntfs-3g /dev/sdb1 /media/sdb1
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
ajay-mani@Ajay-Mani:~$ ls -la /media/sdb1
total 8
drwxr-xr-x 2 root root 4096 2008-02-09 10:54 .
drwxr-xr-x 4 root root 4096 2008-02-09 10:54 .."
after that i again tried the force mount command-
"ajay-mani@Ajay-Mani:~$ sudo mount -t ntfs-3g /dev/sdb1 /media/sdb1 -o force
$LogFile indicates unclean shutdown (0, 0)
WARNING: Forced mount, reset $LogFile."

now along with the icon, when i right click on the icon the list shows an unmount option which was not visible earlier.. but what do i do for the warning?

**WARNING: Forced mount, reset $LogFile.**

and do i have to do it everytime i have to use the external HDD?!

thanks for the help.

---

### Post by copperco2 on 2008-02-09
> **taurus said:**
> 

Otherwise, you have to use the force option to mount it.

Now if i have to disconnect it as i do not wish it to be connected to my laptop then how do i do it. do i have to again force it?. 
i tried doing right click and select unmount. it did not help. the error messge is -
"Cannot unmount the volume 'Manaj' " and the detail given is 'cannot open /media/.hal-mtab"

---

### Post by copperco2 on 2008-02-09
thanks for the help.
the problem has been solved.

i just restarted the laptop with the external hard disk plugged in ... thats all.

thanks a ton for your help. again.

---

