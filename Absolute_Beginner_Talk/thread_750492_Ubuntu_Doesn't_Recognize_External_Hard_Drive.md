---
title: "Ubuntu Doesn't Recognize External Hard Drive"
date: 2008-04-09
forum: Absolute Beginner Talk
---

### Post by Amish_Gramish on 2008-04-09
Ubuntu 7.10 won't recognize my external hard drive.  I have gotten it to recognize my PSP, but it works off and on, and now it doesn't work at all.
Both the PSP and the external HDD work on my XP computer, and they are both formatted as Fat32 (PSP uses it natively).

I've read on here something about mounting, but I don't know how to do that.

EDIT:
I saw something else on another thread that says to type in lsusb in the Terminal, and this is what I got:
> Bus 002 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000

I have both the external HDD and the PSP plugged in, but I have three USB ports.  When I unplug both, it says the same thing, but it takes no time to give me feedback.

---

### Post by TeoBigusGeekus on 2008-04-09
What's the output of
```
ls /media
```
when you have them connected?

---

### Post by Amish_Gramish on 2008-04-09
> cdrom cdrom0 sdb1
If it changes anything, cdrom is light green, and cdrom0 and sdb1 are light blue.

---

### Post by lswest on 2008-04-09
can you post the output of ```
sudo fdisk -l
``` when they're both plugged in?

---

### Post by ace007 on 2008-04-09
report the output of the following when the devices are plugged into the USB ports. 

```

sudo fdisk -l

```

this should output a table of devices which are plugged into the computer.  each device is named something like "hda1", "hdb2", "sda1", or "sdb2'.  you should be able to recognize the size and file system used on each device.  that is how you decide which device is which.  if you cant tell, unplug one thing at a time and run the command again.  whichever is missing is that device.  

you probably need to mount the device manually. if the device is "sda1" and you want to mount it to "/media/USBhdd" use:


```

sudo mount /dev/sda1 /media/USBhdd

```  

it should now be available

---

### Post by wolfen69 on 2008-04-09
for a while my psp was hit or miss, depending on if the ubuntu gods were smiling upon me at the moment. but now it mounts flawlessly every time. not sure there is much you can do about it. actually, after i did a psp update it started working correctly. not sure if there is any correlation there, but it's a possibility. 

mounting drives:
This tutorial will show you how to mount NTFS and FAT partitions in ubuntu
(1) How To mount a NTFS partion in ubuntu ?
For mounting NTFS we are going to use one small tool called NTFS-3G this is very powerfull and
simple tool.
The NTFS-3G driver is an open source, freely available NTFS driver for Linux with read and write
support. It provides safe and fast handling of the Windows XP file systems.
You need to edit the sources.list file using the following command
sudo gedit /etc/apt/sources.list
and add the following repositories which is suitable for you
If you are running Ubuntu Dapper enter the following lines save and exit the file
deb [http://givre.cabspace.com/ubuntu/](http://givre.cabspace.com/ubuntu/) dapper main main-all
deb [http://ntfs-3g.sitesweetsite.info/ubuntu/](http://ntfs-3g.sitesweetsite.info/ubuntu/) dapper main main-all
deb [http://flomertens.keo.in/ubuntu/](http://flomertens.keo.in/ubuntu/) dapper main main-all
If you are running Ubuntu Edgy replace dapper with edgy
Go to senaptic package manager and reload the repos and install ntfs-3g
Configuring ntfs-3g
Now you need to use the following command to determine all the available partitions
sudo fdisk -l
Now you need to configure your NTFS partitions in /etc/fstab file before doing any changes in
/etc/fstab file we will take a backup of this file using the following command (Highly Recommended)
sudo cp /etc/fstab /etc/fstab.bak
Now you need to create a directory where do you mount your windows partitions in this example i ma
creating windows directory
sudo mkdir /media/windows
If you want to mount /dev/hda1 is your windows partition you need to enter the following line in
/etc/fstab file
Page 2
/dev/ /media/ ntfs-3g defaults,locale=en_US.utf8 0 0
You need to replace your partition and mount point with your details
Example
/dev/hda3 /media/windows ntfs-3g defaults,locale=en_US.utf8 0 0
save and exit the file
If you want to mount as read only you need to enter the following line in /etc/fstabfile
/dev/hda3 /media/windows ntfs-3g ro,locale=en_US.utf8,uid=1000 0 0
If You want to change your locale option you need to run the following command in a terminal to
know which one is supported by your system.
locale -a
Now if you want these new chnages to take effect there are two options one is you can simply reboot

your machine and the second one is without rebooting you need to run the following commands

To unmount
sudo umount -a partition-name

Mounting Fat Partition
1) Create a folder on the desktop suppose fatdrive (this is just a foldeer name )
2) Open the terminal type the following command
3) sudo -s
4) give the password
5) mount -a /dev/< fat partition to be mounted > <desktop folder name> -t vfat umask 0022
6) fat drive would be mounted

---

### Post by Amish_Gramish on 2008-04-09
When I put in "sudo fdisk -l" I get:  (Both my internal and external HDDs are 80 GB)
> Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xce5973cb

Device      Boot        Start         End        Blocks        Id       System
/dev/sda1   *                 1       9327    74919096       83      Linux
/dev/sda2                9328       9729       3229065       5       Extended
/dev/sda5                9328       9729       3229033+    82      Linux swap / Solaris

I'll try the mounting drive tutorial now.

---

### Post by ace007 on 2008-04-09
He already said that his stuff if FAT not NTFS.  

If you're looking for help in mounting your USB HD or PSP, you need not read any of the first part of the above post, unless you are just looking for knowledge about NTFS, fstab, or ntfs-3g.  I don't believe you will need to edit the sources.list file in order to get ntfs-3g.  I believe the package is available by default in Gutsy, which the OP listed as his distro.  The command:

```

sudo apt-get install ntfs-3g

```


Also, if you are looking to reload fstab with your new settings you only need to run the command:

```

sudo mount -a

```

The command will reload the new fstab.  There is no need to reboot.  

The latter part about FAT mounting is helpful in your case.  But it is convention to mount media to the directory /media.  Also, you do not need the -a flag in the mount command.  The -a flag is for mounting all devices in fstab.  

Finally, just as my opinion, if you're going to respond to a thread with a lengthy instructional that is not yours please cite the author or at least send them to the instructions via a link.

---

### Post by ace007 on 2008-04-09
> **Amish_Gramish said:**
> 

```

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xce5973cb

Device Boot Start End Blocks Id System
/dev/sda1 * 1 9327 74919096 83 Linux
/dev/sda2 9328 9729 3229065 5 Extended
/dev/sda5 9328 9729 3229033+ 82 Linux swap / Solaris

```

From your output, whichever device has Linux installed on it is device "sda", with Linux on the first partition (sda1), followed by an extended partition (sda2) , and finally a swap partition (sda5). this device is whatever HD has Linux on it and it 80 GB.  There has to be additional output from the fdisk command when the other devices are plugged in.


EDIT:

I'm going home for the day, there should be plenty of people around to help you out.  good luck.  I've never dealt with a PSP before, so who knows if there is some quirkiness about it.

---

### Post by Amish_Gramish on 2008-04-09
> **wolfen69 said:**
> for a while my psp was hit or miss, depending on if the ubuntu gods were smiling upon me at the moment. but now it mounts flawlessly every time. not sure there is much you can do about it. actually, after i did a psp update it started working correctly. not sure if there is any correlation there, but it's a possibility. 

Mounting Fat Partition
1) Create a folder on the desktop suppose fatdrive (this is just a foldeer name )
2) Open the terminal type the following command
3) sudo -s
4) give the password
5) mount -a /dev/< fat partition to be mounted > <desktop folder name> -t vfat umask 0022
6) fat drive would be mounted

My PSP is 3.90 M33-3, so it's not the official firmware.

And with the Fat partition tutorial:
#4, I was never asked to input a password
#5 I don't get anything from this, I just get:
> bash: syntax error near unexpected token `<'

---

### Post by wolfen69 on 2008-04-09
one important question. what kind of external drive is it? (brand)

---

### Post by Amish_Gramish on 2008-04-09
> **wolfen69 said:**
> one important question. what kind of external drive is it? (brand)

Hitachi Travelstar
Model: HTS541080G9AT00

I don't really care if I can't get it working on Linux, as long as I can at least get my PSP working.

---

### Post by lackofcreativity on 2008-04-09
Check to see if it's a problem with, say, a loose wire or dead USB hub. If you're dual-booting with Winblows, try it there. If it works, it's an Ubuntu problem. If you're using an external USB hub, try connecting it to a normal port.

---

### Post by Amish_Gramish on 2008-04-09
> **lackofcreativity said:**
> Check to see if it's a problem with, say, a loose wire or dead USB hub. If you're dual-booting with Winblows, try it there. If it works, it's an Ubuntu problem. If you're using an external USB hub, try connecting it to a normal port.

I have accessed both the external HDD and PSP on my Windows XP computer, and I have transferred files from both of them.
I have also connected my PSP and external HDD to all three USB ports.

---

### Post by wolfen69 on 2008-04-09
reboot with external drive attatched and do fdisk -l again and post output here.

---

### Post by Amish_Gramish on 2008-04-09
> **wolfen69 said:**
> reboot with external drive attatched and do fdisk -l again and post output here.

Same thing as before:
> Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xce5973cb

Device Boot Start End Blocks Id System
/dev/sda1 * 1 9327 74919096 83 Linux
/dev/sda2 9328 9729 3229065 5 Extended
/dev/sda5 9328 9729 3229033+ 82 Linux swap / Solaris

Is there a chance that I somehow turned off the USB ports?  (sudo fdisk -l doesn't change no matter if I have the external HDD attached or not)

---

### Post by wolfen69 on 2008-04-09
i'm running out of ideas. try re-setting your bios to default settings. and do another fdisk -l

if ubuntu wont see it after that, someone more knowledgeable will have to jump in.

---

### Post by Amish_Gramish on 2008-04-09
> **wolfen69 said:**
> i'm running out of ideas. try re-setting your bios to default settings. and do another fdisk -l

if ubuntu wont see it after that, someone more knowledgeable will have to jump in.

Sorry, but how do I do that?

---

### Post by wolfen69 on 2008-04-09
when your computer first starts, press delete or F1, F2, or F10. (depending on your pc) you will enter bios. then look for default settings. usually F10 to save settings.

---

### Post by Amish_Gramish on 2008-04-09
Nothing changed.

Is there a way to enable my USB inputs?
It is powering my hard drive, but I just don't know what else it could be.

---

### Post by Amish_Gramish on 2008-04-09
Thanks!!!!
It's working now!

It added both the PSP and external HDD places!
It looks like it was just the BIOS settings.
(I also went to System --> Preferences --> Removable Drives and Media and checked "auto-run programs on new drives and media" and "auto-open files on new drives and media," so that might have done something too.)

---

### Post by aimpau on 2008-04-10
Thanks for this useful thread. I have a PSP too and now, I know what to look for.

Thanks!

---

