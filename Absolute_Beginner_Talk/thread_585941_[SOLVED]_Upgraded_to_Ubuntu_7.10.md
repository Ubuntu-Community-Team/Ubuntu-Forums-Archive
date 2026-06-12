---
title: "[SOLVED] Upgraded to Ubuntu 7.10"
date: 2007-10-21
forum: Absolute Beginner Talk
---

### Post by evolushun on 2007-10-21
I upgraded to Ubuntu 7.10 and for some reason I cannot see my external HDD.  I have NTFS-3G installed but cannot find it and when I could find it before I upgraded, I still couldn't write to it.  Any ideas?

---

### Post by Pumalite on 2007-10-21
Check in /media and see if you have a 'disk' or 'disk-1'

---

### Post by PPAAUULL on 2007-10-21
Have you checked in the media folder on your linux partition?

---

### Post by evolushun on 2007-10-21
No, it only shows cdrom and cdrom0.

---

### Post by PPAAUULL on 2007-10-21
ok then I think you have to mount it in the command terminal.

---

### Post by evolushun on 2007-10-21
OK...I have read a tutorial on this but I am not sure exactly how to do this...can you post a quick how-to on this in lehmans terms?  I am very new to Linux if you couldn't tell.

---

### Post by Pumalite on 2007-10-21
sudo mkdir /media/disk
sudo mount -t ntfs-3g /dev/??? /media/disk
Find out what your external drive is and replace ???

---

### Post by evolushun on 2007-10-21
It says that it cannot mount the drive "EVOLUSHUN" (my external HDD) and offers me the options of Details and Close.

---

### Post by evolushun on 2007-10-21
Is there not a fix for this?

---

### Post by zbot on 2007-10-21
can you post the exact comand/output you get when you try to mount it ?

-Cisco

---

### Post by evolushun on 2007-10-21
I click on mount and it says "Unable to mount the volume "EVOLUSHUN".  I am not sure if I have done everything right with NTFS as I installed it with SYNAPTIC...I am pretty new to all of this and this is basically a brand new install.

---

### Post by cfaulkner on 2007-10-21
sudo tail -f /var/log/messages


plug in the external, catch the messages, should tell you what /dev it is


Control-C after you find the /dev 

sudo mkdir /media/evolushun
sudo mount /dev/??? /media/evolushun

---

### Post by evolushun on 2007-10-21
After typing in "sudo tail -f /var/log/messages", this is what I got - 

Oct 21 23:24:12 evolushun-laptop kernel: [ 6153.820000] scsi3 : SCSI emulation for USB Mass Storage devices
Oct 21 23:24:17 evolushun-laptop kernel: [ 6158.852000] scsi 3:0:0:0: Direct-Access     WD       2500JB External  0107 PQ: 0 ANSI: 0
Oct 21 23:24:17 evolushun-laptop kernel: [ 6158.856000] sd 3:0:0:0: [sda] 488397168 512-byte hardware sectors (250059 MB)
Oct 21 23:24:17 evolushun-laptop kernel: [ 6158.856000] sd 3:0:0:0: [sda] Write Protect is off
Oct 21 23:24:17 evolushun-laptop kernel: [ 6158.856000] sd 3:0:0:0: [sda] 488397168 512-byte hardware sectors (250059 MB)
Oct 21 23:24:17 evolushun-laptop kernel: [ 6158.860000] sd 3:0:0:0: [sda] Write Protect is off
Oct 21 23:24:17 evolushun-laptop kernel: [ 6158.860000]  sda: sda1
Oct 21 23:24:17 evolushun-laptop kernel: [ 6158.868000] sd 3:0:0:0: [sda] Attached SCSI disk
Oct 21 23:24:17 evolushun-laptop kernel: [ 6158.868000] sd 3:0:0:0: Attached scsi generic sg0 type 0
Oct 21 23:25:21 evolushun-laptop kernel: [ 6222.448000] usb 1-5: USB disconnect, address 7
Oct 21 23:25:41 evolushun-laptop kernel: [ 6242.256000] usb 1-5: new high speed USB device using ehci_hcd and address 8
Oct 21 23:25:41 evolushun-laptop kernel: [ 6242.396000] usb 1-5: configuration #1 chosen from 1 choice
Oct 21 23:25:41 evolushun-laptop kernel: [ 6242.396000] scsi4 : SCSI emulation for USB Mass Storage devices
Oct 21 23:25:46 evolushun-laptop kernel: [ 6247.428000] scsi 4:0:0:0: Direct-Access     WD       2500JB External  0107 PQ: 0 ANSI: 0
Oct 21 23:25:46 evolushun-laptop kernel: [ 6247.432000] sd 4:0:0:0: [sda] 488397168 512-byte hardware sectors (250059 MB)
Oct 21 23:25:46 evolushun-laptop kernel: [ 6247.432000] sd 4:0:0:0: [sda] Write Protect is off
Oct 21 23:25:46 evolushun-laptop kernel: [ 6247.436000] sd 4:0:0:0: [sda] 488397168 512-byte hardware sectors (250059 MB)
Oct 21 23:25:46 evolushun-laptop kernel: [ 6247.436000] sd 4:0:0:0: [sda] Write Protect is off
Oct 21 23:25:46 evolushun-laptop kernel: [ 6247.436000]  sda: sda1
Oct 21 23:25:46 evolushun-laptop kernel: [ 6247.444000] sd 4:0:0:0: [sda] Attached SCSI disk
Oct 21 23:25:46 evolushun-laptop kernel: [ 6247.444000] sd 4:0:0:0: Attached scsi generic sg0 type 0

---

### Post by cfaulkner on 2007-10-21
try

sudo mkdir /media/evolushun
sudo mount /dev/sda1 /media/evolushun

---

### Post by evolushun on 2007-10-21
Here is what I got and I will leave the terminal open awaiting your response...

$LogFile indicates unclean shutdown (0, 0)
Failed to mount '/dev/sda1': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the 'Safely Remove Hardware' icon in the Windows
          taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/sda1 /media/evolushun -o force

    Or add the option to the relevant row in the /etc/fstab file:

            /dev/sda1 /media/evolushun ntfs-3g defaults,force 0 0

---

### Post by cfaulkner on 2007-10-21
I would reboot system, and try again...  seems it's already mounted.. check your Places > Computer

Also, in Linux you cannot simply pull the USB cable out.  You must Unmount the Filesystem before unplugging the USB cable.  Or else Windows is gonna freak out ont hat FS when you go back into Windows

---

### Post by evolushun on 2007-10-21
I have rebooted a few times and when I click on Places >Computer, I do see it but when I double click on it, it tells me that it cannot mount the volume.

---

### Post by cfaulkner on 2007-10-21
possibly the partition is in disarray.  you might want to in Windows scandisk it and fix the problems.  What errors is it giving you?

sudo cat /var/log/messages | grep sda

(you'll get a crap load of text on this one prolly)

---

### Post by evolushun on 2007-10-21
First off, would entering anything in this help?

[IMG]http://i97.photobucket.com/albums/l229/evolande/Screenshot-2.png[/IMG]

---

### Post by evolushun on 2007-10-21
Oct 21 21:34:58 evolushun-laptop kernel: [   18.144000] sd 0:0:0:0: [sda] 488397168 512-byte hardware sectors (250059 MB)
Oct 21 21:34:58 evolushun-laptop kernel: [   18.144000] sd 0:0:0:0: [sda] Write Protect is off
Oct 21 21:34:58 evolushun-laptop kernel: [   18.148000] sd 0:0:0:0: [sda] 488397168 512-byte hardware sectors (250059 MB)
Oct 21 21:34:58 evolushun-laptop kernel: [   18.148000] sd 0:0:0:0: [sda] Write Protect is off
Oct 21 21:34:58 evolushun-laptop kernel: [   18.148000]  sda: sda1
Oct 21 21:34:58 evolushun-laptop kernel: [   18.148000] sd 0:0:0:0: [sda] Attached SCSI disk
Oct 21 21:38:43 evolushun-laptop kernel: [  248.528000] sd 1:0:0:0: [sda] 488397168 512-byte hardware sectors (250059 MB)
Oct 21 21:38:43 evolushun-laptop kernel: [  248.528000] sd 1:0:0:0: [sda] Write Protect is off
Oct 21 21:38:43 evolushun-laptop kernel: [  248.532000] sd 1:0:0:0: [sda] 488397168 512-byte hardware sectors (250059 MB)
Oct 21 21:38:43 evolushun-laptop kernel: [  248.532000] sd 1:0:0:0: [sda] Write Protect is off
Oct 21 21:38:43 evolushun-laptop kernel: [  248.532000]  sda: sda1
Oct 21 21:38:43 evolushun-laptop kernel: [  248.540000] sd 1:0:0:0: [sda] Attached SCSI disk
Oct 21 21:42:00 evolushun-laptop kernel: [   18.128000] sd 0:0:0:0: [sda] 488397168 512-byte hardware sectors (250059 MB)
Oct 21 21:42:00 evolushun-laptop kernel: [   18.128000] sd 0:0:0:0: [sda] Write Protect is off
Oct 21 21:42:00 evolushun-laptop kernel: [   18.128000] sd 0:0:0:0: [sda] 488397168 512-byte hardware sectors (250059 MB)
Oct 21 21:42:00 evolushun-laptop kernel: [   18.128000] sd 0:0:0:0: [sda] Write Protect is off
Oct 21 21:42:00 evolushun-laptop kernel: [   18.128000]  sda: sda1
Oct 21 21:42:00 evolushun-laptop kernel: [   18.132000] sd 0:0:0:0: [sda] Attached SCSI disk
Oct 21 22:18:09 evolushun-laptop kernel: [ 2190.640000] sd 1:0:0:0: [sda] 488397168 512-byte hardware sectors (250059 MB)
Oct 21 22:18:09 evolushun-laptop kernel: [ 2190.640000] sd 1:0:0:0: [sda] Write Protect is off
Oct 21 22:18:09 evolushun-laptop kernel: [ 2190.644000] sd 1:0:0:0: [sda] 488397168 512-byte hardware sectors (250059 MB)
Oct 21 22:18:09 evolushun-laptop kernel: [ 2190.644000] sd 1:0:0:0: [sda] Write Protect is off
Oct 21 22:18:09 evolushun-laptop kernel: [ 2190.644000]  sda: sda1
Oct 21 22:18:09 evolushun-laptop kernel: [ 2190.648000] sd 1:0:0:0: [sda] Attached SCSI disk
Oct 21 22:18:43 evolushun-laptop kernel: [ 2225.332000] sd 2:0:0:0: [sda] 488397168 512-byte hardware sectors (250059 MB)
Oct 21 22:18:43 evolushun-laptop kernel: [ 2225.332000] sd 2:0:0:0: [sda] Write Protect is off
Oct 21 22:18:43 evolushun-laptop kernel: [ 2225.336000] sd 2:0:0:0: [sda] 488397168 512-byte hardware sectors (250059 MB)
Oct 21 22:18:43 evolushun-laptop kernel: [ 2225.336000] sd 2:0:0:0: [sda] Write Protect is off
Oct 21 22:18:43 evolushun-laptop kernel: [ 2225.336000]  sda: sda1
Oct 21 22:18:43 evolushun-laptop kernel: [ 2225.340000] sd 2:0:0:0: [sda] Attached SCSI disk
Oct 21 23:24:17 evolushun-laptop kernel: [ 6158.856000] sd 3:0:0:0: [sda] 488397168 512-byte hardware sectors (250059 MB)
Oct 21 23:24:17 evolushun-laptop kernel: [ 6158.856000] sd 3:0:0:0: [sda] Write Protect is off
Oct 21 23:24:17 evolushun-laptop kernel: [ 6158.856000] sd 3:0:0:0: [sda] 488397168 512-byte hardware sectors (250059 MB)
Oct 21 23:24:17 evolushun-laptop kernel: [ 6158.860000] sd 3:0:0:0: [sda] Write Protect is off
Oct 21 23:24:17 evolushun-laptop kernel: [ 6158.860000]  sda: sda1
Oct 21 23:24:17 evolushun-laptop kernel: [ 6158.868000] sd 3:0:0:0: [sda] Attached SCSI disk
Oct 21 23:25:46 evolushun-laptop kernel: [ 6247.432000] sd 4:0:0:0: [sda] 488397168 512-byte hardware sectors (250059 MB)
Oct 21 23:25:46 evolushun-laptop kernel: [ 6247.432000] sd 4:0:0:0: [sda] Write Protect is off
Oct 21 23:25:46 evolushun-laptop kernel: [ 6247.436000] sd 4:0:0:0: [sda] 488397168 512-byte hardware sectors (250059 MB)
Oct 21 23:25:46 evolushun-laptop kernel: [ 6247.436000] sd 4:0:0:0: [sda] Write Protect is off
Oct 21 23:25:46 evolushun-laptop kernel: [ 6247.436000]  sda: sda1
Oct 21 23:25:46 evolushun-laptop kernel: [ 6247.444000] sd 4:0:0:0: [sda] Attached SCSI disk
Oct 21 23:51:46 evolushun-laptop kernel: [   18.168000] sd 0:0:0:0: [sda] 488397168 512-byte hardware sectors (250059 MB)
Oct 21 23:51:46 evolushun-laptop kernel: [   18.196000] sd 0:0:0:0: [sda] Write Protect is off
Oct 21 23:51:46 evolushun-laptop kernel: [   18.196000] sd 0:0:0:0: [sda] 488397168 512-byte hardware sectors (250059 MB)
Oct 21 23:51:46 evolushun-laptop kernel: [   18.196000] sd 0:0:0:0: [sda] Write Protect is off
Oct 21 23:51:46 evolushun-laptop kernel: [   18.196000]  sda: sda1
Oct 21 23:51:46 evolushun-laptop kernel: [   18.196000] sd 0:0:0:0: [sda] Attached SCSI disk

---

### Post by cfaulkner on 2007-10-21
Probably, enter a mount point  (ie  /media/evolushun)

then hit Close

see what gives

Make sure the directory /media/evolushun  exists

---

### Post by evolushun on 2007-10-22
OK...since I pretty much want this hard drive to work in Ubuntu and it seems to have issues with NTFS, how can I format this drive into FAT32 and start over???

---

### Post by cfaulkner on 2007-10-22
Load into a Live WinXP session, BartPE or what not and format.  Or use partition magic. or, just format it to EXT3 and no worries..

---

### Post by evolushun on 2007-10-22
How do I install Partition Magic?

---

### Post by cfaulkner on 2007-10-22
Well, Partition Magic is a commercial program, they might have a trial out there somewhere.  

You could probably 

sudo fdisk /dev/sda

and change the filesystem type in there to Windows95 (FAT32), but about formatting to that, I dunno.

Anyone else have some insight ont his one.. i'm drawing a blank...:)

---

### Post by evolushun on 2007-10-22
I'm just going to roll back to 7.04 since that allowed me to use my drive as-is.

---

### Post by gtdaqua on 2007-10-22
> **evolushun said:**
> I'm just going to roll back to 7.04 since that allowed me to use my drive as-is.

did u try Gnome Partition Editor - it will display all the drives available; u can check what is ur exact "/dev/???" there.

---

### Post by evolushun on 2007-10-22
So, I went back to Feisty...I have not done a thing with NTFS so I do not mess it up.  Where do I start so I can have access to write to it?  It is sitting on my desktop as we speak.

---

### Post by arthur_kalm on 2007-10-22
I'm having the same problem after my Gusty upgrade. At first it worked but now I can no longer mount the Windows partition. This problem was also reported here: [http://ubuntuforums.org/showthread.php?t=575092&highlight=Mount+is+denied+because+NTFS+marked+to+be+in+use.+Choose+one+action%3A]("http://ubuntuforums.org/showthread.php?t=575092&highlight=Mount+is+denied+because+NTFS+marked+to+be+in+use.+Choose+one+action%3A")

---

### Post by evolushun on 2007-10-22
> **arthur_kalm said:**
> I'm having the same problem after my Gusty upgrade. At first it worked but now I can no longer mount the Windows partition. This problem was also reported here: [http://ubuntuforums.org/showthread.php?t=575092&highlight=Mount+is+denied+because+NTFS+marked+to+be+in+use.+Choose+one+action%3A]("http://ubuntuforums.org/showthread.php?t=575092&highlight=Mount+is+denied+because+NTFS+marked+to+be+in+use.+Choose+one+action%3A")

I fixed my problem by hooking up my external back into a Windows PC and properly ejecting it.  Once I did that, Ubuntu Gutsy read it perfectly, with no issues!  Might want to give that a try.

---

### Post by cemptor on 2007-10-22
I have the exact same problem with my upgrade from Fiesty to Gutsy. ntfs-3g was working fine, and it suddenly doesn't. In my case it is an internal hard drive, and I have a Vista partition which is working fine, and shutting down normally. This is definitely a bug with the upgrade as I notice a lot of threads devoted to this

---

