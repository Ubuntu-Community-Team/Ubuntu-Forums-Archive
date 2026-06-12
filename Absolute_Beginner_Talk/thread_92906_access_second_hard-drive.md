---
title: "access second hard-drive"
date: 2005-11-20
forum: Absolute Beginner Talk
---

### Post by duus on 2005-11-20
Hello.  I installed Ubuntu on my parent's old Compaq pesario.  It works just great!  However, the computer has a second hard drive, and I might as well use it....so  I looked at this HowToInstallingANewHarddrive

[https://wiki.ubuntu.com/InstallingANewHardDrive](https://wiki.ubuntu.com/InstallingANewHardDrive)

but on the first step 

$ sudo dmesg|less

i got a lot of errors about my printer (oddly, since it works just fine.)

# lots of lines saying this:
drivers/usb/class/usblp.c: usblp0: error -19 reading printer status
drivers/usb/class/usblp.c: usblp0: error -19 reading printer status
drivers/usb/class/usblp.c: usblp0: error -19 reading printer status
drivers/usb/class/usblp.c: usblp0: error -19 reading printer status

# and then:
drivers/usb/class/usblp.c: usblp0: removed
ibm_acpi: ec object not found
usb 1-1.1: new full speed USB device using uhci_hcd and address 7
drivers/usb/class/usblp.c: usblp0: USB Bidirectional printer dev 7 if 0 alt 0 proto 2 vid 0x03F0 pid 0x7204

But nothing about the harddrive.  Any thoughts?

(More info: the last time i accessed that drive is when it was a Windows machine.  So I'm confident it's still Windows formatted.  When I can access it I plan on reformatting it.)

---

### Post by apjone on 2005-11-20
ok look in /dev and look at what hda / hdb device's there are if it is the slave on ide1 then 

sudo mount /dev/hda1 /mnt
also you can 
sudo vi /etc/fstab 
and press 'i'
input 
/dev/hdb1       /mnt     vfat    defaults        0       0
then press 'esc' ':' 'wq'
this will mount it at boot time

---

### Post by duus on 2005-11-20
thanks for your reply!

does this mean anything to you?

apape@ubuntu:/dev$ sudo mount /dev/hdc /mnt
mount: No medium found

By the way, Device Manager lists both hard drive IDEs as (master), so that could be the issue (although I don't know how to change that.)

---

### Post by apjone on 2005-11-20
try 
sudo mount /dev/hdb0 /mnt 
ort
sudo mount /dev/hdb1 /mnt

---

### Post by aysiu on 2005-11-20
Can you post the output of these two commands? ```
sudo fdisk -l
``` ```
cat /etc/fstab
``` And can you also say whether this is a Windows partition?

---

### Post by duus on 2005-11-20
[QUOTE=apjone]try 
sudo mount /dev/hdb0 /mnt 
ort
sudo mount /dev/hdb1 /mnt[/QUOTE]

it said they don't exist.

---

### Post by duus on 2005-11-20
[QUOTE=aysiu]Can you post the output of these two commands? [/QUOTE]```
sudo fdisk -l
``` 

Disk /dev/hda: 10.0 GB, 10005037056 bytes
255 heads, 63 sectors/track, 1216 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        1162     9333733+  83  Linux
/dev/hda2            1163        1216      433755    5  Extended
/dev/hda5            1163        1216      433723+  82  Linux swap / Solaris


```
cat /etc/fstab
``` 
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

[QUOTE=aysiu]And can you also say whether this is a Windows partition?[/QUOTE]

And it is definitely a windows partition, although there is nothing important on it, so I would be happy reformating it for ubuntu.

I guess that output suggests to me that the extra harddrive is hda2 (whatever "extended" means) and so I thought I would try to mount it.  I thought I had tried before but I guess not--because when I tried it froze my machine.

I also realize that my mount hdc, being the cdrom, seems fairly silly now, too.  Well, I guess this is why it's in "absolute beginner talk" :)

---

### Post by duus on 2005-11-27
hello...any thoughts anyone?  hd2 is the extra harddrive, i guess?  any thoughts on how to make sure?  and maybe format it properly and have it mount?

---

### Post by xmastree on 2005-11-27
Your disks are hd**a** thru hd**d**.

hda is primary master, hdb primary slave, hdc secondary master and hdd secondary slave.
The output of fdisk -l suggests that the system only sees hda, your primary master.
Is the BIOS set up to detect the second disk? Where is it connected?
Your CD appears to be the secondary master (/dev/hdc /media/cdrom0 udf,iso9660 ro,user,noauto 0 0).
If the second hard disk is primary slave it would show up as hdb, but it doesn't...

Check your BIOS.

---

### Post by aysiu on 2005-11-28
I don't see your second hard drive anywhere on the partition table.
As xmastree said, it'd probably be /dev/hdb1
If it were an external hard drive, it'd be /dev/sda1 or /dev/sde1

Are you sure it's plugged in? Even if it's not "mounted" (i.e., accessible for browsing in Ubuntu), it should still show up in the partition table.

---

### Post by patrick295767 on 2005-11-28
maybe try :
qtparted 
 
or gparted 
  
to have better overview which /dev/... has to be mounted:
e.g.:
mount -t vfat /dev/hda6 /mnt/hda6
  
regards

---

### Post by daynah on 2005-11-29
To do this, does there need to be some kind of OS on the hard drive?

---

