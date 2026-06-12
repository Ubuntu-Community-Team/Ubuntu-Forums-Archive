---
title: "USB Mass Storage help... :("
date: 2007-08-15
forum: Absolute Beginner Talk
---

### Post by nothing4me on 2007-08-15
Subject: Sony DSC-N2 Camera (In Mass Storage Mode via USB)
Clues:[LIST=1]
[*]No messages pop up when USB is in.
[*]Does not appear in "Computer".
[*]Does not appear on the "Desktop".[/LIST]What should I do?
(If you need some command outputs, let me know.)

---

### Post by nothing4me on 2007-08-15
Quick bumpie. :)

---

### Post by overdrank on 2007-08-15
> **nothing4me said:**
> Subject: Sony DSC-N2 Camera (In Mass Storage Mode via USB)
Clues:[LIST=1]
[*]No messages pop up when USB is in.
[*]Does not appear in "Computer".
[*]Does not appear on the "Desktop".[/LIST]What should I do?
(If you need some command outputs, let me know.)

Which version of ubuntu are you using, Feisty 7.04, Edgy 6.10?

---

### Post by milosz.galazka on 2007-08-15
Turn it on (?), connect to computer and cut and paste result of commands:
**tail /var/log/messages** and **lsusb**

Quite interesting link: [http://ubuntuforums.org/showthread.php?t=292951](http://ubuntuforums.org/showthread.php?t=292951)

---

### Post by nothing4me on 2007-08-15
Fiesty 7.04. :)

---

### Post by nothing4me on 2007-08-15
Bump... :(

---

### Post by nothing4me on 2007-08-15
> **milosz.galazka said:**
> Turn it on (?), connect to computer and cut and paste result of commands:
**tail /var/log/messages** and **lsusb**

Quite interesting link: [http://ubuntuforums.org/showthread.php?t=292951](http://ubuntuforums.org/showthread.php?t=292951)The first command of "tail" said:
> user@laptop:~$ tail /var/log/messages
Aug 15 19:41:25 laptop kernel: [10957.008000] usb 5-1: configuration #1 chosen from 1 choice
Aug 15 19:42:20 laptop kernel: [11012.144000] usb 5-1: USB disconnect, address 30
Aug 15 19:42:23 laptop kernel: [11014.400000] usb 5-1: new high speed USB device using ehci_hcd and address 31
Aug 15 19:42:23 laptop kernel: [11014.532000] usb 5-1: configuration #1 chosen from 1 choice
Aug 15 19:43:00 laptop kernel: [11051.412000] usb 5-1: USB disconnect, address 31
Aug 15 19:43:01 laptop kernel: [11053.164000] usb 5-1: new high speed USB device using ehci_hcd and address 32
Aug 15 19:43:02 laptop kernel: [11053.296000] usb 5-1: configuration #1 chosen from 1 choice
Aug 15 19:43:10 laptop kernel: [11062.028000] usb 5-1: USB disconnect, address 32
Aug 15 19:43:25 laptop kernel: [11076.664000] usb 5-1: new high speed USB device using ehci_hcd and address 33
Aug 15 19:43:25 laptop kernel: [11076.800000] usb 5-1: configuration #1 chosen from 2 choices
The second command of "lsusb" said:
> user@laptop:~$ lsusb
Bus 005 Device 033: ID 054c:0010 Sony Corp. DSC-S30/S70/S75/F505V/F505/FD92 Cybershot/Mavica Digital Camera
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  


---

### Post by overdrank on 2007-08-15
Hi maybe this thread may help
[http://ubuntuforums.org/showthread.php?t=401879&highlight=Sony+Corp.+DSC-S30%2FS70%2FS75%2FF505V%2FF505%2FFD92](http://ubuntuforums.org/showthread.php?t=401879&highlight=Sony+Corp.+DSC-S30%2FS70%2FS75%2FF505V%2FF505%2FFD92)

---

### Post by milosz.galazka on 2007-08-15
You can install **gphoto2**

Look at the documentation. Simple usage is here at [http://www.gphoto.org/doc/manual/using-gphoto2.html](http://www.gphoto.org/doc/manual/using-gphoto2.html)

Reference at [http://www.gphoto.org/doc/manual/ref-gphoto2-cli.html](http://www.gphoto.org/doc/manual/ref-gphoto2-cli.html)

Supported devices: [http://www.gphoto.org/proj/libgphoto2/support.php](http://www.gphoto.org/proj/libgphoto2/support.php)

---

### Post by nothing4me on 2007-08-15
I don't need the photos. I need some files placed on there from a Windows OS.

---

### Post by milosz.galazka on 2007-08-15
[http://www.gphoto.org/doc/manual/using-gphoto2.html](http://www.gphoto.org/doc/manual/using-gphoto2.html)
alice@host:~$ gphoto2 --get-all-files

---

### Post by nothing4me on 2007-08-15
By the way, when I put the camera on "PTP" or "Pictobridge" mode, Ubuntu detects it, but launches a picture manager software.

I don't want to use that method, I need to get the files from the Camera.

---

### Post by nothing4me on 2007-08-15
> **milosz.galazka said:**
> [http://www.gphoto.org/doc/manual/using-gphoto2.html](http://www.gphoto.org/doc/manual/using-gphoto2.html)
alice@host:~$ gphoto2 --get-all-filesHow would I put files into it too?

---

### Post by nothing4me on 2007-08-15
Bumpie. :)

---

### Post by nothing4me on 2007-08-15
Argh!!! :((((
Bump!!!

---

### Post by meierfra on 2007-08-15
Post the output of

```
sudo fdisk -l
```

---

### Post by creedog on 2007-08-15
ok, try disconnecting the drive and doing the following

```
df -k
```

then reconnect the drive... wait a few seconds and do the command again. Hopefully you will have an additional line of output which should be the mounting of your camera. 

When I connected mine I get the following additional line

```
/dev/sdd1               120992     54256     66736  45% /media/disk-1

```

This tells me that the device /dev/sdd1 is now mounted on /media/disk-1. Navigate to this directory in your gui file manager and you should see your files.

---

### Post by nothing4me on 2007-08-15
> **meierfra said:**
> Post the output of

```
sudo fdisk -l
```

Here you go:
> user@laptop:~$ sudo fdisk -l
Password:

Disk /dev/sda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4659    37423386   83  Linux
/dev/sda2            4660        4864     1646662+   5  Extended
/dev/sda5            4660        4864     1646631   82  Linux swap / Solaris


---

### Post by nothing4me on 2007-08-15
> **creedog said:**
> ok, try disconnecting the drive and doing the following

```
df -k
```then reconnect the drive... wait a few seconds and do the command again. Hopefully you will have an additional line of output which should be the mounting of your camera. 

When I connected mine I get the following additional line

```
/dev/sdd1               120992     54256     66736  45% /media/disk-1

```This tells me that the device /dev/sdd1 is now mounted on /media/disk-1. Navigate to this directory in your gui file manager and you should see your files.Nothing changed when I removed the USB and put it back in. The numbers didn't move around.

---

### Post by nothing4me on 2007-08-15
Bump! :D

*Going to sleep.*

---

### Post by meierfra on 2007-08-15
Connected the camera in the various modes and each time run the commands  "df -k" and "sudo fdisk -l".  If you detect any changes, post the output.

---

