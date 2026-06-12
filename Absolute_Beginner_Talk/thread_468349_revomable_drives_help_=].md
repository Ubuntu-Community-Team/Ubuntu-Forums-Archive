---
title: "revomable drives help =]"
date: 2007-06-08
forum: Absolute Beginner Talk
---

### Post by mark. on 2007-06-08
i started using linux yesterday, but when i start up is says cannot access 'HAL' service (or launch hal service, i forgot.) is this any bad, and can how can i fix it?

also, my mobiblu 1500i will not connect with the computer. it is supposed to show up as a removable disk drive, but i plug it in and it charges but does not show up on the computer. also when i launch 'removable drives and media' (in a self-attempt to fix it) it shows a error message 

'the "hald" service is required but not currently running. enable this service and re-run this application, or contact your system administrator.'

help anyone? thanks in advance :D

---

### Post by mark. on 2007-06-08
help anyone? i cannot use my usb thumb drives and mp3 player =[

---

### Post by shamushand on 2007-06-08
I hope I'm wrong, but those devices sound like they aren't Linux compatible.

---

### Post by mark. on 2007-06-09
really? its just a removable disk drive.. 
but i cant even get the manager to start as-is. help anyone?

---

### Post by Inxsible on 2007-06-09
You can use your external drives with Linux.
Connect the drive to the computer and run this command in the terminal. Applications --> Accessories --> Terminal
```
sudo fdisk -l
``` -l is lowercase L

---

### Post by mark. on 2007-06-09
umm i did that, and i think it recognized the drive. however i don't know where to access the files on the drive- is it in removable disks/media?

---

### Post by Inxsible on 2007-06-09
Could you post the output here?

---

### Post by mark. on 2007-06-09
:~$ sudo fdisk -l
Password:

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9202    73915033+   7  HPFS/NTFS
/dev/sda2            9203       19269    80863177+  83  Linux
/dev/sda3           19270       19457     1510110    5  Extended
/dev/sda5           19270       19457     1510078+  82  Linux swap / Solaris

Disk /dev/sdb: 519 MB, 519438336 bytes
34 heads, 53 sectors/track, 563 cylinders
Units = cylinders of 1802 * 512 = 922624 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1         563      507236+   b  W95 FAT32

im guessing that FAT32 has something to do with this.. is there any way i can fix this?

---

### Post by Inxsible on 2007-06-09
I am assuming its the 512 mb sdb drive. It has a boot flag on it, do you have an installation of Windows on it?

if you dont already have pmount installed, you can install it by ```
sudo aptitude install pmount
```
you can mount it by using the following command
```
sudo pmount /dev/sdb1 usbdisk
```
you can replace usbdisk with any name you want. Make sure that the name you choose is NOT already a folder under /media, because pmount creates the folder too.

---

### Post by mark. on 2007-06-09
ok i got everything, but when i enter my folder for the media, it says 

You do not have the permissions necessary to view the contents of "+mobiblu".

(mobiblu being the name of the folder :/) is there a terminal command to fix this?

---

### Post by Inxsible on 2007-06-09
Assuming your username is mark and your group is mark too
```
sudo chown -R mark:mark /media/mobiblu
```

---

### Post by mark. on 2007-06-09
well im not sure of my group ect.. i cant even access my users/groups menu :/

my computer name is as l--desktop and my user is mark, but i dont really know what my group is.

and is says i need to enable 'hald' service, how can i do that.

---

### Post by mark. on 2007-06-18
ok im in users group 'root', but when i enter that into terminal nothing happens.
i tried running 'Removable drives and Media' from the menu bar but i need to enable 'HAL' (or 'hald'). 

how do i enable this? 
help please ive been trying to do this for weeks now and im getting frustrated =[

---

