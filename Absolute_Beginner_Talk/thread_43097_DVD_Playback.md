---
title: "DVD Playback"
date: 2005-06-20
forum: Absolute Beginner Talk
---

### Post by vampiro on 2005-06-20
linux newbie alert

I have tried Playing dvds back on xine and the sound is fine but the video is all jumpy im running ubuntu on a HP Pavilion N5461 laptop. any way i can fix this???

also is there a way to get read and right access on a usb hard drive???

laymans terms plz 

Cheers

---

### Post by wellery on 2005-06-20
You'll have to enable dma on you drive.

To check you can do "hdparm /dev/hdd" where /dev/hdd is the location of the dvd drive .
if not then do "sudo vim /etc/hdparm.conf" and append the following  

/dev/hdd {
dma = on
}

where /dev/hdd is the location of the dvd drive. 

this will ensure it is enabled at boot. 


To enable dma now do:

hdparm -d 1 /dev/hdd

You should be able to find out you dvd location by typing "sudo mount" when a dvd is in the drive and is mounted.

---

### Post by chz on 2005-06-21
=======================
$ hdparm -d 1 /dev/hda

/dev/hda:
 setting using_dma to 1 (on)
 HDIO_SET_DMA failed: Permission denied
 using_dma    =  0 (off)

$
=======================

whats wrong here..??

EDIT: nevermind...forgot to put "sudo".....DOH

---

### Post by vampiro on 2005-06-21
i get  this when i run 

root@ubuntu:/home/vampiro # hdparm -d 1 /dev/hda3

/dev/hda3:
 setting using_dma to 1 (on)
 HDIO_SET_DMA failed: Invalid argument
 using_dma    =  1 (on)

and thats with out editing the conf file and it still be jumpy

---

### Post by mercur on 2005-06-22
I had the same problem... and I tried 
root@testa:/home/sartori # hdparm -d 1 /dev/hdc

/dev/hdc:
 setting using_dma to 1 (on)
 using_dma    =  1 (on)
root@testa:/home/sartori #

and it works using Xine!!!!
But I still have some doubts! Can I set this on the system's intialization? 
thanks!

---

### Post by vampiro on 2005-06-22
i have just about to get it not to jump by altering the video driver to use in dxr3.

the jumpiness has gone down a bit but it is still there and annying the hell out of me. any other video file like .avi, .mpeg .mpg play fine  :???:

---

