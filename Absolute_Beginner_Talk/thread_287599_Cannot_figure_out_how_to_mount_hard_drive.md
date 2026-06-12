---
title: "Cannot figure out how to mount hard drive"
date: 2006-10-29
forum: Absolute Beginner Talk
---

### Post by vince vega on 2006-10-29
I recently installed Ubuntu, its my first linux experience. I have two hard drives connected to my pc. I have Ubuntu installed on my 160gb (master) drive. My 100gb (slave) drive, houses all of my music/videos. After formatting the master and installing linux, i cannot figure out how to access my slave drive, with all my music. Any help would be greatly appreciated.

---

### Post by taurus on 2006-10-29
Okay, I assume your second harddrive is called /dev/hdb1 and it's a fat32/vfat format.  Open a terminal (Applications -> Accessories -> Terminal) and do

```
gksudo gedit /etc/fstab
```
Now, add the following line to the end of it and save it.

```
/dev/hdb1   /media/share   vfat   defaults,umask=0000   0   0
```
Then, create a mount point for it and mount it with

```
sudo mkdir /media/share
sudo mount -a
```
Your music should now be in /media/share...

---

### Post by phelixnyc on 2006-10-29
What if your using ntfs? I'am having isues mounting my sata drive I was able to load my other drive that is ntfs formatted. I'am using Edgy and am using Ntfs-3g.  Work well for one but not my sata

---

### Post by taurus on 2006-10-29
> **phelixnyc said:**
> What if your using ntfs? I'am having isues mounting my sata drive I was able to load my other drive that is ntfs formatted. I'am using Edgy and am using Ntfs-3g.  Work well for one but not my sata

```

/dev/sda1   /media/share   ntfs   defaults,umask=0222   0   0

```

---

### Post by vince vega on 2006-10-29
Tarus, I tried adding: 

/dev/hdb1   /media/share   vfat   defaults,umask=0000   0   0

When i try to mount, I get this error.

wrong fs type, bad option, bad superblock on /dev/hdb1,
       missing codepage or other error

I also tried the NTFS code, and it did not work. Im Lost.

Heres a copy of fstab:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=a10f3808-b654-424d-b2e5-326f63dac6c5 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=b2ffa735-9bc2-45e5-8249-081396e3abc2 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/hdb1   /media/share   vfat   defaults,umask=0000   0   0

---

### Post by mahy on 2006-10-29
So what kind of filesystem your disk is?

remove the entry from fstab and try it separately

sudo mount -t your_filesystem /dev/something /media/share

1.) you can use some nice grafical apps to check what the name of your disk is
2.) make sure the directory /media/share exists
3.) does your drive work elsewhere?

---

### Post by vince vega on 2006-10-29
Its a NTFS file system. I was previously running windows. Windows was never installed on the drive. It is used strictly for storage.

Media/Share..does exist.

What graphical apps, do you recommend? I have no idea what drive to mount. This is my 1st day using Linux. I'm clueless. Thanks.

---

### Post by Chinkostu on 2006-10-29
[http://www.linuxforum.com/linux_tutorials/1/1.php](http://www.linuxforum.com/linux_tutorials/1/1.php)

i did something along the lines of that to mount HDB1 on my install.

---

### Post by phelixnyc on 2006-10-29
Thank you taurus for the reply. I did as you said and I still cant get that sata to be displayed on my desktop.  "Storage device manager states" it is mounted but no icon on desktop. When I enter command "/dev/sda1   /media/share   ntfs   defaults,umask=0222   0   0" in termanal it says "permission denied". Not sure where to go from here.

---

### Post by mahy on 2006-10-29
> **vince vega said:**
> Its a NTFS file system. I was previously running windows. Windows was never installed on the drive. It is used strictly for storage.

Media/Share..does exist.

What graphical apps, do you recommend? I have no idea what drive to mount. This is my 1st day using Linux. I'm clueless. Thanks.

Try looking around in the Gnome menu (you do have Gnome, don't you? Is your desktop brown? If yes, you have Gnome ;) ). I don't have, can't be more specific. Try finding something like "Partition Manager" or similar name. It should list all your disks. Just don't commit any changes in there!!

---

### Post by mahy on 2006-10-29
> **phelixnyc said:**
> Thank you taurus for the reply. I did as you said and I still cant get that sata to be displayed on my desktop.  "Storage device manager states" it is mounted but no icon on desktop. When I enter command "/dev/sda1   /media/share   ntfs   defaults,umask=0222   0   0" in termanal it says "permission denied". Not sure where to go from here.

you have to put 'sudo' in front of that command:

sudo *command*

---

### Post by taurus on 2006-10-29
> **phelixnyc said:**
> Thank you taurus for the reply. I did as you said and I still cant get that sata to be displayed on my desktop.  "Storage device manager states" it is mounted but no icon on desktop. When I enter command "/dev/sda1   /media/share   ntfs   defaults,umask=0222   0   0" in termanal it says "permission denied". Not sure where to go from here.
If you want to test it out from a command first, try

```
sudo mount -t ntfs /dev/sda1 /media/share
(assuming that your NTFS is on /dev/sda1 and you have a mount point of /media/share
```

---

### Post by phelixnyc on 2006-10-29
Mahy thank you. I did not commit as you said and did as taurus said and I still can not mount the drive.  My hdb is mounted using nfts-3g but as I stated early I cant mount my sata drive

---

### Post by taurus on 2006-10-29
What's the output of this command then?

```
sudo fdisk -l
```

---

### Post by phelixnyc on 2006-10-29
Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       30400   244187968+   7  HPFS/NTFS

---

### Post by taurus on 2006-10-29
So, exactly what is the error message after you run these two commands from a prompt?

```

sudo mkdir /media/share
sudo mount -t ntfs /dev/sda1 /media/share

```

---

### Post by phelixnyc on 2006-10-29
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1           11983       14593    20972857+  83  Linux
/dev/hda2           11722       11982     2096482+  82  Linux swap / Solaris
/dev/hda3               1       11721    94148901   83  Linux

Partition table entries are not in disk order

Disk /dev/hdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1       14592   117210208+   7  HPFS/NTFS

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       30400   244187968+   7  HPFS/NTFS

---

### Post by phelixnyc on 2006-10-29
Taurus this the error
phelix@phelix-desktop:~$ sudo mkdir /media/share
mkdir: cannot create directory `/media/share': File exists
phelix@phelix-desktop:~$ sudo mount -t ntfs /dev/sda1 /media/share
mount: /dev/sda1 already mounted or /media/share busy
mount: according to mtab, /dev/sda1 is already mounted on /media/share
phelix@phelix-desktop:~$

---

### Post by taurus on 2006-10-29
> **phelixnyc said:**
> Taurus this the error
phelix@phelix-desktop:~$ sudo mkdir /media/share
mkdir: cannot create directory `/media/share': File exists
phelix@phelix-desktop:~$ sudo mount -t ntfs /dev/sda1 /media/share
mount: /dev/sda1 already mounted or /media/share busy
mount: according to mtab, /dev/sda1 is already mounted on /media/share
phelix@phelix-desktop:~$
Hey, your NTFS is in /media/share now!!!  What does it look when you run this command?

```
df -h
```
Do you see /dev/sda1 in /media/share?

---

### Post by phelixnyc on 2006-10-29
phelix@phelix-desktop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/hda1              20G  2.5G   17G  14% /
varrun                506M  108K  506M   1% /var/run
varlock               506M     0  506M   0% /var/lock
procbususb             10M  116K  9.9M   2% /proc/bus/usb
udev                   10M  116K  9.9M   2% /dev
devshm                506M     0  506M   0% /dev/shm
lrm                   506M   18M  489M   4% /lib/modules/2.6.17-10-generic/volatile
/dev/hda3              89G  157M   84G   1% /home
/dev/hdb1             112G   38G   75G  34% /media/hdb1
/dev/sda1             233G   48G  186G  21% /media/share

---

### Post by bodhi.zazen on 2006-10-29
phelixnyc:

I wrote a how-to on fstab that may help: [How to fstab](http://ubuntuforums.org/showthread.php?t=283131)

At any rate try:
```
sudo umount /media/share
sudo mount -t ntfs-3g /dev/sda1 /media/share
ls /medis/share
```

and for fsatab:> /dev/sda1 /media/share ntfs-3g users,auto,gid=100,umask=007

Now```
sudo umount /media/share
mount /media/share
```_Note_: No sudo in that last mount.

---

### Post by taurus on 2006-10-29
Do you see the last line of that output?  Your /dev/sda1 is in /media/share right now.  ;) 

So, if you want to mount it upon boot with read permission for everybody, add this line to your /etc/fstab (gksudo gedit /etc/fstab).

```

/dev/sda1   /media/share   ntfs   defaults,umask=0222   0   0

```
Now, unmount it and mount it again with

```
sudo umount /media/share
sudo mount -a
```

---

### Post by phelixnyc on 2006-10-29
Taurus this the message I get
phelix@phelix-desktop:~$ sudo umount /media/share
Password:
phelix@phelix-desktop:~$ sudo umount /media/share
umount: /media/share: not mounted
phelix@phelix-desktop:~$ sudo mount -a
mount: /dev/sda1 already mounted or /media/share busy
phelix@phelix-desktop:~$

---

### Post by phelixnyc on 2006-10-29
Bodhi I tried the command a got this message
phelix@phelix-desktop:~$ sudo umount /media/share
Password:
umount: /media/share: not mounted
phelix@phelix-desktop:~$ sudo umount /media/share
umount: /media/share: not mounted
phelix@phelix-desktop:~$ sudo mount -t ntfs-3g /dev/sda1 /media/share
Error opening partition device: Device or resource busy
Failed to startup volume: Device or resource busy
Failed to mount '/dev/sda1': Device or resource busy
Mount is denied because the NTFS volume is already exclusively opened.
The volume may be already mounted, or another software may use it which
could be identified for example by the help of the 'fuser' command.
phelix@phelix-desktop:~$ ls /medis/share
ls: /medis/share: No such file or directory
phelix@phelix-desktop:~$ fuser
No process specification given

---

### Post by taurus on 2006-10-29
> **phelixnyc said:**
> Taurus this the message I get
phelix@phelix-desktop:~$ sudo umount /media/share
Password:
phelix@phelix-desktop:~$ sudo umount /media/share
umount: /media/share: not mounted
phelix@phelix-desktop:~$ sudo mount -a
mount: /dev/sda1 already mounted or /media/share busy
phelix@phelix-desktop:~$
Why don't you reboot your machine and see if /dev/sda1 still shows up with "df -h" command!  If not, then edit /etc/fstab and add that line to the bottom of it, as describe above.  Then run "sudo mount -a" at the prompt and see what happens...

---

### Post by phelixnyc on 2006-10-29
It still is in "df-h". When I run sudo mount -a nothing happens.

---

### Post by phelixnyc on 2006-10-29
Could it have something to do with Fuse?

---

### Post by bodhi.zazen on 2006-10-29
> **phelixnyc said:**
> Could it have something to do with Fuse?

It looks like the partition is already mounted.

What happens when you type:```
ls /media/share
```Note: you had a "typo" in your earlier post:> phelix@phelix-desktop:~$ ls /medis/share
ls: /[color=red]medis[/color]/share: No such file or directory

---

### Post by phelixnyc on 2006-10-29
Nothing when I use "ls /media/share" I boot and I still have no access to drive(and no icon on desktoop like my 2nd drive).

---

### Post by taurus on 2006-10-29
If your /dev/sda1 is not mounted after you boot, from "df -h" command, then add that line to your /etc/fstab and mount it with the "sudo mount -a" this time...

---

### Post by phelixnyc on 2006-10-30
I figured it out some what> I have three drives in my pc and I must have mounted my two extra ones wrong because I "dh-h" it and get thisphelix@phelix-desktop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/hda1              20G  2.3G   17G  13% /
varrun                506M  100K  506M   1% /var/run
varlock               506M     0  506M   0% /var/lock
procbususb             10M  116K  9.9M   2% /proc/bus/usb
udev                   10M  116K  9.9M   2% /dev
devshm                506M     0  506M   0% /dev/shm
lrm                   506M   18M  489M   4% /lib/modules/2.6.17-10-generic/volatile
/dev/hda3              89G  138M   84G   1% /home
/dev/sda1             112G   38G   75G  34% /media/share
/dev/hdb1             112G   38G   75G  34% /media/share


I also get the two same mounted points on my desktop after boot.

---

