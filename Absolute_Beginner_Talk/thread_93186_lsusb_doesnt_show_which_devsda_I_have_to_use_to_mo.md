---
title: "lsusb doesnt show which /dev/sda?? I have to use to mount my harddisk ?"
date: 2005-11-21
forum: Absolute Beginner Talk
---

### Post by patrick295767 on 2005-11-21
I tried gparted and qtparted 
and my letter for my harddisk doesnt show up. 
  
when I do, mount -t vfat /dev/hda4
  
It's there ?? yeap'
So, that would mean that u cannot see all u wish with gparted and qtparted. 
  
Also, I am rather sure that Linux with the regular command line, 
it can tell me where is (which /dev/??) is my external harddrive?
which lsusb -option_stuff should I use 
  
or is there another cmd ?
  
Thank you very much

Pat'

---

### Post by dubz on 2005-11-21
normally for external usb harddrives they run on sd(special devieces) so to mount your usb drive you would type...

mount -t vfat /dev/sda1 <mount point>

-(make sure you are mounting with the correct filesystem)
 
with special devices they start from 1 to how many usb ports you have.

i hope that answered your question.couldnt quite understand you:)

thanks.

---

### Post by patrick295767 on 2005-11-21
[QUOTE=dubz]normally for external usb harddrives they run on sd(special devieces) so to mount your usb drive you would type...

mount -t vfat /dev/sda1 <mount point>

-(make sure you are mounting with the correct filesystem)
 
with special devices they start from 1 to how many usb ports you have.

i hope that answered your question.couldnt quite understand you:)

thanks.[/QUOTE]
   
:-)
Thank you for your reply..
sorry, my english is not sooo good.
  
So, I normally do : mount -t vfat /dev/sda1 <mount point>
  
But, in my case, I dont know what is the <mount point> (sthg like /dev/sda1 or /dev/sdb1 or ...) 
cos I dont know where / how I can get the information of knowing which dev is the One ... 
  
Is there a way to get the information what's is corresponding to my external drive ?
(lsusb ?? gives only that's plugged only but never says : /dev/sda1 or /dev/sd...)
  
I hope you will undertand me better ... now... 
Otherwise, I can take an example to be more accurate ... 
  
Thank you very much again !
  
Pat'

---

### Post by dubz on 2005-11-21
dubz@karova:~$ lsusb
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 003: ID 045e:0009 Microsoft Corp. IntelliMouse
Bus 001 Device 002: ID 09aa:3642 Intersil Corp. Prism2.x 802.11b Adapter
Bus 001 Device 001: ID 0000:0000

thats what i get.
the best way really to find out is guess.
trial and error is your friend in linux.

thanks.

---

### Post by patrick295767 on 2005-11-21
mine for the moment 
Bus 004 Device 005: ID 0f62:1001 Acrox Technologies Co., Ltd 
Bus 004 Device 004: ID 046d:0928 Logitech, Inc. 
Bus 004 Device 003: ID 0556:0001 Asahi Kasei Microsystems Co., Ltd AK5370 I/F A/D Converter
Bus 004 Device 002: ID 04b4:6560 Cypress Semiconductor Corp. CY7C65640 USB-2.0 "TetraHub"
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  


i still have to I plug my hdd external ... to see the result (eating now)...

 thank you again& again !

---

### Post by dubz on 2005-11-21
no problem:)

---

### Post by patrick295767 on 2005-11-22
mine for the moment 
Bus 004 Device 005: ID 0f62:1001 Acrox Technologies Co., Ltd 
Bus 004 Device 004: ID 046d:0928 Logitech, Inc. 
Bus 004 Device 003: ID 0556:0001 Asahi Kasei Microsystems Co., Ltd AK5370 I/F A/D Converter
Bus 004 Device 002: ID 04b4:6560 Cypress Semiconductor Corp. CY7C65640 USB-2.0 "TetraHub"
Bus 004 Device 001: ID 0000:0000 
Bus 003 Device 001: ID 0000:0000 
Bus 002 Device 001: ID 0000:0000 
Bus 001 Device 001: ID 0000:0000 
  
my hdd is visible once plugged ... 
but nothg great changes...
  
Is there a prg to know the list of all the /dev/ linked with USB ?

---

### Post by dubz on 2005-11-22
All i remember right now is

ls /dev/sda*

at console.

---

### Post by patrick295767 on 2005-11-22
[QUOTE=dubz]All i remember right now is

ls /dev/sda*

at console.[/QUOTE]
 
This will give the list.
I also saw that there was a gnome-program to get the info of ur usb
but unfortunately, it's not displayed the corresponding /dev/??  (for instance, /dev/sda1 for my first external harddrive)

---

### Post by dubz on 2005-11-22
The best way is trial and error.Mount and umount diffeerent ones and see what happens.

..

---

### Post by patrick295767 on 2005-11-22
linux is never really easy :-(

---

### Post by patrick295767 on 2005-12-07
From this forum, I learned that : 

Unpluggin then pluggin' the usb device, 
then
type
```
dmesg
```
  
Can indicate better than lsusb where could be your usb device ...

---

### Post by miceagol on 2007-01-11
Wild guess is not a good choice. dmesg tells you the exact position of the usb disk if you look at the last message right after inserting the disk.

---

