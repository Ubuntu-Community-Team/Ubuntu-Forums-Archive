---
title: "2nd hard drive not available"
date: 2007-04-29
forum: Absolute Beginner Talk
---

### Post by McDusty on 2007-04-29
hi,

just installed Ubuntu last night and i've had my problems, but I have my wireless card working and Opera installed so things are looking up!

But my 2nd hard drrive is nowehre to be seen. I have one drive with a ntfs winxp partition and the ubuntu one. i can see this ntfs one and access it. I also have a 2nd fat32 drive which is the large one i use to store music, pictures, video, work, etc etc. But this is absent.

Now on my first boot into Ubuntu it perform drive checks claiming such a check hadnt been done in 49 thousand days or something ridiculous. Anyway, this got right to the end then it said an error which i think related to continuous space, but cant be sure ... it reset the computer a few secs later and booted straight in ... without the drive showing and without performing this check again.

The drive is still fine and accessible from within windows. Im a little unsure where to start to investigate this since im not even sure what the error was.

Any idea's on where to start? What test to run?

Cheers
Ash

---

### Post by taurus on 2007-04-29
Can you post the output of these two commands from a terminal?

Applications -> Accessories -> Terminal
```
cat /etc/fstab
sudo fdisk -l
```

---

### Post by AtrejuT on 2007-04-29
could you open up a terminal and post the output of
```

sudo fdisk -l

```

this will help us get some information to help you...

EDIT: (damn, I was second...)

---

### Post by McDusty on 2007-04-29
Hi guys,

Sorry for the delayed response ... An ubuntu update killed my hard work getting the ndiswrapper to work with my usb wpn111. Still not resolved, so im back in windows right now :(

Anyway, I ran the fdisk command. Heres the output: 

ash@Rusty:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda2
UUID=bdc968a0-0fbd-48dd-adf3-d4ba6801c649 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=42e03570-60bc-41da-b43a-cbf439e0b619 none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdb        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

---

### Post by McDusty on 2007-05-01
Hi,

just a bump really ...

It doesn't look like my 2nd 120 gig drive is even on this list to me. since i think it just shows the  ntfs windows partition of the my first drive and the ubuntu partition of my first drive.

my 2nd drive is a slave to my 1st. Could this be an issue in Linux? Should I try putting my 2nd drive as the Secondary Master?

---

### Post by taurus on 2007-05-01
Can you post the output of this command from a terminal?

```
sudo fdisk -l
```

---

### Post by McDusty on 2007-05-02
Cheers,

I did ... its ...

ash@Rusty:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
# /dev/hda2
UUID=bdc968a0-0fbd-48dd-adf3-d4ba6801c649 / ext3 defaults,errors=remount-ro 0 1
# /dev/hda5
UUID=42e03570-60bc-41da-b43a-cbf439e0b619 none swap sw 0 0
/dev/hdd /media/cdrom0 udf,iso9660 user,noauto 0 0
/dev/hdb /media/cdrom1 udf,iso9660 user,noauto 0 0
/dev/fd0 /media/floppy0 auto rw,user,noauto 0 0

---

### Post by taurus on 2007-05-02
How about

```
sudo fdisk -l
```

---

### Post by McDusty on 2007-05-02
ash@Rusty:~$ sudo fdisk -l
Password:

Disk /dev/hda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        3204    25736098+   7  HPFS/NTFS
/dev/hda2            3205        4789    12731512+  83  Linux
/dev/hda3            4790        4865      610470    5  Extended
/dev/hda5            4790        4865      610438+  82  Linux swap / Solaris

Disk /dev/hdc: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1   *           1       14593   117218241    c  W95 FAT32 (LBA)
ash@Rusty:~$

---

### Post by taurus on 2007-05-02
Edit /etc/fstab

```
gksudo gedit /etc/fstab
```
and add this line to the end of it to mount your /dev/hdc1.

```
/dev/hdc1   /media/hdc1   vfat    iocharset=utf8,umask=000    0    0
```
Save the change.  Then, create a new mount point and mount it.

```
sudo mkdir /media/hdc1
sudo mount -a
df -h
```

---

### Post by McDusty on 2007-05-02
Sorry taurus

Got confused. So there it is, the hdc1 partition. So, any idea's why can't I see it?

Thanks
Ash

---

### Post by McDusty on 2007-05-02
Cheers,

only just seen your post ... will try it now :)

---

### Post by McDusty on 2007-05-02
Hi again.

It seemed to do its stuff, but the drive didnt appear. I restarted the comp but still no joy and my on/off erratic wireles in Ubuntu decided to stop working again. So back in windows right now to post this.

fstab now reads:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda2
UUID=531d03a5-e002-496c-a89f-d729f9f69f98 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=a611f37d-ffab-4be8-bc39-492af7cff160 none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdb        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/hdc1   /media/hdc1   vfat    iocharset=utf8,umask=000    0    0


and fdisk -l: 

ash@Rusty:~$ sudo fdisk -l

Disk /dev/hda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        3204    25736098+   7  HPFS/NTFS
/dev/hda2            3205        4789    12731512+  83  Linux
/dev/hda3            4790        4865      610470    5  Extended
/dev/hda5            4790        4865      610438+  82  Linux swap / Solaris

Disk /dev/hdc: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1   *           1       14593   117218241    c  W95 FAT32 (LBA)



Ill try booting into Ubuntu again and hitting alt+f4 to see if I can spot any errors as it boot.

---

### Post by taurus on 2007-05-02
After it finishes booting, post the output of this command from a terminal?

```
df -h
```

---

### Post by banditv1 on 2007-05-02
I had trouble mounting a vfat partition as well I ended up having to change the drive format to ext3. My drive was vfat32. Since you are able to access the ntsf drive you may want to consider converting the fat partition to ntsf. CAUTION Be sure to back up all data before you do this. 

Good Luck!

---

### Post by McDusty on 2007-05-02
:)

The output was ...

ash@Rusty:~$ df -h
Filesystem            Size Used Avail Use% Mounted on
/dev/hda2              12G  2.2G  9.3G  19% /
varrun                252M  108K  252M   1% /var/run
varlock               252M     0  252M   0% /var/lock
procbususb            252M  112K  252M   1% /proc/bus/usb
udev                  252M  112K  252M   1% /dev
devshm                252M     0  252M   0% /dev/shm
lrm                   252M   33M  219M  14% /lib/modules/2.6.20-15-generic/volatile
/dev/hdc1             112G   32K  112G   1% /media/hdc1


... so I looked in /media and indeed there it is, hdc1 ... and all  my files are there and accessible!

Is there anyway to get this to appear as a drive? Though its not really a problem to access it this way.

Also, there was some messages on boot about this, is there a log kept of boot output? It said something about ISO not being optimum for fat32 or something along those lines. Could be usefull to help me solve my wireless issue if i can see a boot log ... since theres always stuff being dumped about ndiswarpper.

Thanks guys (or girls)
Ash

---

### Post by McDusty on 2007-05-02
Found a thread about turning on boot logging. Should have searched before asking. Ill give that a try.

---

