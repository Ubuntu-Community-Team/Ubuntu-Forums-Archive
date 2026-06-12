---
title: "USB Sony Micro Vault 1GB"
date: 2006-07-04
forum: Absolute Beginner Talk
---

### Post by joris_xl on 2006-07-04
Hello, 
                started on Ubuntu down here in Burundi, quite nice I thought
                as it's part of the local Kirundi language (+- 'personality')

My USB stick was behaving quite well (as \dev\sda1 on media\usbdisk or something...) till I screwed up something (how ???) 

anyhow, I get " GIVEN UDI IS NOT A MOUNTABLE DEVICE"

and in Windows, it shows as removable disk but when I try to access, I get "INSERT DISK IN DRIVE ..."

anyone any suggestions how to get this thing working again ?

thanks a lot.
Joris 
Bujumbura, Burundi.

---

### Post by ajgreeny on 2006-07-04
Have you inadvertently formatted it in some file system that is not read by either system?  can't imagine what that would be but worth thinking about.  Alternatively check the USB socket on your machine and the stick itself, as it is not impossible for them to get loose and/or dirty and stop good contact with the USB stick.

---

### Post by joris_xl on 2006-07-04
Was formatted as FAT, and expect it still to be... If it was some exotic fs, wouldn't you still see some trace of the 1GB space ?

Windows recognises the drive and "generic usb flash drive usb device" but asks 'insert disk' when accessing.
What's the UDI message in Ubuntu ?  

checked it on 5 different machines (2 Ubuntu, 3 Windows XP) with same results and fiddled a bit with the thing itself, no use... 

 
thanx. 
Joris.

---

### Post by erniewinner on 2006-07-04
hi,

i had problems with my mp3 player last night. something went wrong with the tranfer of files under xandros... i couldn't do anything with it. do you have files on it you want to keep? if you don't use the "disk..." (sorry can't remember the full name.) it's at the top of the screen where all your options are. you will need to put in your password. pick the right drive and click disable drive then you can reformat as fat. that sorted my problem out. (i can't boot ubuntu to check what it's called sorry.)

---

### Post by joris_xl on 2006-07-04
Thanks; just wondering how to select 'the right drive' you refer to, 
as I didn't get it mounted as well.

Sorry can't check in Ubuntu right now, about 200 km away and 'don't install Ubuntu if you have no or slow internet access'... I begin to get the point :)

---

### Post by erniewinner on 2006-07-04
is there anything you want to salvage on the drive? if not a reformat of the drive is about the best way to go?

---

### Post by joris_xl on 2006-07-04
oeps no, nothing.
but in WinXP not accessible so no chance to format,
in Ubuntu no mount so no format 

I'm missing something prbably, but to my limited understanding, I should first get a working partition on it again of 1GB, then format... 

anyhow will try your advice once back on Ubuntu, + possibly with LiveCD and GParted ?

---

### Post by erniewinner on 2006-07-04
anyway the part that helped me out was "system, administartion, disks." "disks manager." just select the right drive. my problem was "input/ output error, the file does not exist" a few files had this problem and i couldn't delete them, so i had to reformat it...
i also had a problem where i was asked to "insert disk" i had 2 identical make usb mmc/sd card drives. one supported a 1gb memory card. but the other one would not... and it asked me to insert a card. is yours a mmc type card you can put in yourself? if so like me you might try to flash the drive with a later firmware... if it exists. :rolleyes:

---

