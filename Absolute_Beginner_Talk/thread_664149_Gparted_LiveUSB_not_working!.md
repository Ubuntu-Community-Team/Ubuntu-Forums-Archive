---
title: "Gparted LiveUSB not working!"
date: 2008-01-10
forum: Absolute Beginner Talk
---

### Post by 449 on 2008-01-10
Why isn't this working?

```
erik@erik-desktop:~$ cd D
Desktop/   Documents/ 
erik@erik-desktop:~$ cd Desktop/
erik@erik-desktop:~/Desktop$ cd ..
erik@erik-desktop:~$ ls
3 10 to Yuma[2007]DvDrip[Eng]-FXG
Atonement.2007.DvDRip.Eng-FxM
Azureus
check_gmail.sh
Circle Takes the Square
Circle Takes The Square - As The Roots Undo
C O D E~
conditions.sh
Desktop
Documents
Files
Futurama season 1-5 (complete) + extras
Futurama - Season 2
gtk-2.0
hddmonit.sh
He.Was.A.Quiet.Man.2007.DVDRip.XviD-VoMiT
Incomplete
Maybe
Music
nautilus-debug-log.txt
Next[2007]DvDrip.AC3[Eng]-aXXo
Orchid- Dance Tonight! Revolution Tomorrow!
orchid - takk!_soundsampler -- Jamendo - MP3 VBR 192k - 2007.04.23 [www.jamendo.com]
Pictures
pogodynka.sh
Public
Punch_Drunk_Love.avi
Saetia - Discography - MP3
Se7en(1995DvDrip).avi
Shared
Torrent DLs
Torrent Downloads
ventrilo
Videos
erik@erik-desktop:~$ cd ..
erik@erik-desktop:/home$ ls
erik
erik@erik-desktop:/home$ cd ..
erik@erik-desktop:/$ cd ..
erik@erik-desktop:/$ ls
bin    dev       GPL.txt  initrd.img  media  root  sys  var
boot   etc       home     lib         mnt    sbin  tmp  vmlinuz
cdrom  EULA.txt  initrd   lost+found  proc   srv   usr
erik@erik-desktop:/$ cd m
media/ mnt/   
erik@erik-desktop:/$ cd media/
erik@erik-desktop:/media$ ls
cdrom  cdrom0  cdrom1  disk  USB20FD
erik@erik-desktop:/media$ cd USB20FD/
erik@erik-desktop:/media/USB20FD$ ls
gparted-livecd-0.3.4-11.iso  set_usb.sh
erik@erik-desktop:/media/USB20FD$ sudo sh set_usb.sh 

[: 16: /tmp/gparted: unexpected operator























$

 ----------------------------------------------------------------------
$                This script is to be run to copy files from GParted-livecd ISO file to usb stick. Run this script from the directory where you downloaded the GParted-livecd ISO file. I assume you have a usb stick formatted as FAT (or FAT32), with at least 55 MO free. You are now going to be asked the path where your usb stick is mounted.
-----------------------------------------------------------------------$

set_usb.sh: 27: function: not found
-en 
y
$        -So, let's look for any gparted-livecd ISO file in the current directory.
erik@erik-desktop:/media/USB20FD$ 



```

---

### Post by 449 on 2008-01-10
I don't see what I'm doing wrong...

---

### Post by 449 on 2008-01-10
anyone??

---

### Post by Sef on 2008-01-11
Please don't bump unless more than 24 hours have passed.   Most threads do get answered within a day, but not always right away.  Infractions can be given for bumping too often.

---

