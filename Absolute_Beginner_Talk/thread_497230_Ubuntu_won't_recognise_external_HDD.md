---
title: "Ubuntu won't recognise external HDD"
date: 2007-07-10
forum: Absolute Beginner Talk
---

### Post by karmakaze11 on 2007-07-10
I've just installed Ubuntu, and it won't reconise my USB external HDD; when I was using the Live CD, it had no trouble noticing it, and put it on my desktop for me - but the installed version doesn't even pick it up in the Places menu, or in the file browser. Can anyone help?

---

### Post by Ek0nomik on 2007-07-10
Can you post the output of these commands (Accessories/Terminal)

```
sudo mount
```

```
sudo fdisk -l
```

```
cat /etc/fstab
```

---

### Post by karmakaze11 on 2007-07-10
sudo mount:
/dev/sda3 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
devhm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.20-15-generic/volatile type tmpfs (rw)
/dev/sda1 on media/sda1 type vfat (rw,utf8,umask=007,gid=46)
/dev/sda2 on media/sda2 type ntfs (rw,nls=utf8,umask=007,gid=46)
/dev/sda0 /media/cdrom0 type iso9660 (ro,noexec,nosuid,nodev,user=acacia)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)

sudo fdisk -1:
This was an invalid command.

cat /etc/fstab:
# /etc/fstab: static file system information.
#
# <file system> <mount point>  <type>  <options>      <dump>  <pass>
proc                    /proc                  proc        defaults          0              0
# /dev/sdal
UUID=e0244a86-fc38-4216-8ebd-705deec8dfla /            ext3          defaults,errors=remount-ro 0     1
# /dev/sdal
UUID=8A68028D68027869 /media/sda2      nfts       defaults,nls=utf8,umask=007,gid=46 0      1
# /dev/sda4
UUID=478a36al-cefd-4a2e-9667-a4e394c9d2d9 none               swap        sw            0               0
/dev/scd0           /media/cdrom0   udf,iso9660 user,noauto       0          0
/dev/fd0             /media/floppy0  auto    rw,user,noauto  0        0

---

### Post by k33bz on 2007-07-10
> **karmakaze11 said:**
> 


sudo fdisk -1:
This was an invalid command.

0

that needs to be
```
sudo fdisk -l
```
lower case L not a one

---

### Post by karmakaze11 on 2007-07-10
Ah ok, sorry about that. The output was:

Disk /dev/sda: 40.0GB, 40020664320 bytes
240 heads, 63 sectors/track, 5169 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes

      Device    Boot     Start     End       Blocks     Id     System
/dev/sda1                      1     715   5405368+   b     W95 FAT32
/dev/sda2     *           716   3651  22196960    7      HPFS/NTFS
/dev/sda3                3652   5130  11181240    83    Linux
/dev/sda4                5131   5169      294840    82    Linux swap / Solaris

---

### Post by Ek0nomik on 2007-07-10
What external hard drive isn't being recognized?

Based off of your mount results, you have a FAT32, EXT3, and NTFS drive mounted.

This is what I am mostly looking at:

```
mount
[B]/dev/sda3 on / type *ext3* (rw,errors=remount-ro)
/dev/sda1 on media/sda1 type *vfat* (rw,utf8,umask=007,gid=46)
/dev/sda2 on media/sda2 type *ntfs* (rw,nls=utf8,umask=007,gid=46)[/B]
```

What file system is the external drive using?  How big is it?

You could also post

```
df -h
```

to look at your drives in a more readable fashion as far as space goes.

---

### Post by bigboy_pdb on 2007-07-10
Plug in your hard drive and turn on the power. Type 'lsusb' in a terminal (Applications -> Accessories -> Terminal). Your external USB drive should show up in the output. This step will only indicate whether or not your computer is recognizing that the device is there, but it will not mount it. If you don't see your drive appearing in the output, try connecting the USB drive to another USB slot. It wouldn't hurt to post the output of the command either.

---

### Post by karmakaze11 on 2007-07-11
lsusb gave the following:
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000

I tried using a USB port at the front of my computer, and one at the back, both gave this output.

df -h gave:
Filesystem Size Used Avail Use% Mounted on
/dev/sda3 11G 2.0G 8.1G 20% /
varrun 252M 108K 252M 1% /var/run
varlock 252m 0 252M 0% /var/lock
procbususb 252M 80K 252M 1% /proc/bus/usb
udev 252M 80K 252M 1% /dev
devshm 252M 0 252M 0% /dev/shm
lrm 252M 33M 219M 14% /lib/modules/2.6.20-15-generic/volatile
/dev/sda1 5.2G 4.3G 952M 82% /media/sda1
/dev/sda2 22G 18G 3.8G 83% /media/sda2
/dev/scd0 649M 649M 0 100% /media/cdrom0

I think my external HDD is fat32, although I'm not 100% sure. EDIT: Oh, and it's 250Gb.

---

### Post by Ek0nomik on 2007-07-11
I have never seen the USB device not get picked up in any of the commands I listed before.  Mostly, fdisk -l, as the others are just showing other information.

Based on your lsusb output, your USB ports aren't being used by anything.  As an example, here is my lsusb output:

```
dove@edelweiss:~$ lsusb
Bus 005 Device 005: ID 1058:0400 Western Digital Technologies, Inc. 
Bus 005 Device 004: ID 1058:0500 Western Digital Technologies, Inc. 
Bus 005 Device 003: ID 1058:0903 Western Digital Technologies, Inc. 
Bus 005 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 004: ID 046d:c024 Logitech, Inc. 
Bus 002 Device 001: ID 0000:0000  
```

I have my Logitech mouse, and two Western Digital hard drives.  (I am not sure why it is showing up with three)

What brand is the hard drive?

---

### Post by karmakaze11 on 2007-07-11
Mine is WD as well.. And when I boot into Windows, XP has no problem recognising it or using the data.. I've tried all the ports on my computer, all 6 gave the same lsusb output.

---

### Post by Ek0nomik on 2007-07-11
> **karmakaze11 said:**
> Mine is WD as well.. And when I boot into Windows, XP has no problem recognising it or using the data.. I've tried all the ports on my computer, all 6 gave the same lsusb output.

You are positive it is a FAT32?  If Windows is recognizing it I imagine it is FAT32 or NTFS.

---

### Post by vwbeamer on 2007-07-11
do share how you solved this?

---

### Post by Inxsible on 2007-07-11
Did you connect your drive and switch it on(if there is a button) before doing the 
```
sudo fdisk -l
```?
 
If yes, try :
 
If you have a dual boot or another Windows machine, plug in the drive to a windows machine and then do the 'Safely Remove Hardware' thingy.
 
Then try to connect it to Ubuntu.

---

### Post by vwbeamer on 2007-07-11
I get this when I input "sudo fdisk -l


Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4781    38403351    7  HPFS/NTFS
/dev/sda2            9586        9729     1156680   82  Linux swap / Solaris
/dev/sda3            4783        9585    38580097+  83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        9729    78148161    c  W95 FAT32 (LBA)

---

### Post by karmakaze11 on 2007-07-11
I found out that random USB disconnections are an unfixed bug in Feisty, especially with mass storage devices. You can try to solve this by disabling USB 2.0 with "sudo modprobe -r ehci_hcd", but this didn't work for me.

I tried safely removing the device from Windows, then booted into Ubuntu for the same information as last time. And yes, it is definitely FAT32.

When I tried lsusb again, my external HDD sounded like it was starting up, but still wasn't recognised in the output.

---

### Post by vwbeamer on 2007-07-11
I rebooted with HDD plugged into USB port and it showed on the desktop. I was able to use it then

---

### Post by Inxsible on 2007-07-11
> **vwbeamer said:**
> I rebooted with HDD plugged into USB port and it showed on the desktop. I was able to use it then
you should use pmount to mount it. pmount is specifically used for external drives. Using pmount will mount your drive under /media and automatically mount it the moment you connect it.

You also do NOT need fstab entries if you use pmount. Post back if you need more info on how to use it.

---

### Post by karmakaze11 on 2007-07-11
How do I use pmount?

Under removable drives and media, I have "mount removable media when inserted".. How is pmount different from this? Thanks for your help..

---

### Post by Inxsible on 2007-07-11
> **karmakaze11 said:**
> How do I use pmount?

Under removable drives and media, I have "mount removable media when inserted".. How is pmount different from this? Thanks for your help..
If you dont already have pmount installed

```
sudo aptitude install pmount
```
then to use it

```
sudo pmount /dev/Xd*? MOUNT_POINT
```where X = s or h
* = a,b,c....
?=1,2,3...
MOUNT_POINT could be a name of your choosing, provided it does not already exist under /media. pmount creates a folder for you and automatically mounts it there each time you connect the drive.

Hope that helps.

---

### Post by karmakaze11 on 2007-07-11
It can't find pmount to install it.. I'm guessing it needs to be connected to the internet for that?

I'm typing this on my parents' laptop because my computer's connection doesn't seem to be working..

I tried using the command anyway, but got the error "sudo: pmount: command not found" so I assume that means pmount isn't installed already.

---

### Post by Inxsible on 2007-07-11
> **karmakaze11 said:**
> It can't find pmount to install it.. I'm guessing it needs to be connected to the internet for that?

I'm typing this on my parents' laptop because my computer's connection doesn't seem to be working..

I tried using the command anyway, but got the error "sudo: pmount: command not found" so I assume that means pmount isn't installed already.

yes you would need the internet to install anything.

---

### Post by karmakaze11 on 2007-07-11
Alright.. Thanks for your help, I'll try to get the internet working now so I can try this out.

---

### Post by bigboy_pdb on 2007-07-13
Has Ubuntu recognized any other USB devices (if you've tried them)? If you haven't tried any other devices you should try plugging some in (such as a printer) and typing the "lsusb" command to see if other USB devices aren't being recognized.

---

