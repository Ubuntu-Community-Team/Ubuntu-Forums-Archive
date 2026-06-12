---
title: "Need help with DVD player"
date: 2006-03-29
forum: Absolute Beginner Talk
---

### Post by wolfee on 2006-03-29
My p4 should handle it but movies skip like a 400 mhz Is there a hardware conflict?
I'm using mplayer. Also Totem or mplayer play mpg,avi,and dvds really dark. i cant adjust the brightness. I set it but nothing happens

---

### Post by LanceM on 2006-03-29
Check out your dma setting:

[https://wiki.ubuntu.com/DMA](https://wiki.ubuntu.com/DMA)

---

### Post by wolfee on 2006-03-29
I got this

lou@c-67-163-247-106:~$    sudo hdparm /dev/hdc

/dev/hdc:
 IO_support   =  0 (default 16-bit)
 unmaskirq    =  0 (off)
 using_dma    =  1 (on)
 keepsettings =  0 (off)
 readonly     =  0 (off)
 readahead    = 256 (on)
 HDIO_GETGEO failed: Invalid argument
lou@c-67-163-247-106:~$   sudo hdparm -d1 /dev/hdc

/dev/hdc:
 setting using_dma to 1 (on)
 using_dma    =  1 (on)
lou@c-67-163-247-106:~$    4.
bash: 4.: command not found
lou@c-67-163-247-106:~$
lou@c-67-163-247-106:~$       sudo gedit /etc/hdparm.conf
sudo: gedit: command not found
lou@c-67-163-247-106:~$
lou@c-67-163-247-106:~$

---

### Post by moffa on 2006-03-29
what about your drivers for the video card?  Try typing "fglrxinfo" in a console, if you see Mesa, you don't have your drivers installed

---

### Post by wolfee on 2006-03-29
[QUOTE=moffa]what about your drivers for the video card?  Try typing "fglrxinfo" in a console, if you see Mesa, you don't have your drivers installed[/QUOTE]
lou@c-67-163-247-106:~$ fglrxinfo
bash: fglrxinfo: command not found
lou@c-67-163-247-106:~$ sudo fglrxinfo
Password:
sudo: fglrxinfo: command not found
lou@c-67-163-247-106:~$ fglrxinfo
bash: fglrxinfo: command not found
lou@c-67-163-247-106:~$ sudo hdparm /dev/hdc

/dev/hdc:
 IO_support   =  0 (default 16-bit)
 unmaskirq    =  0 (off)
 using_dma    =  0 (off)
 keepsettings =  0 (off)
 readonly     =  0 (off)
 readahead    = 256 (on)
 HDIO_GETGEO failed: Invalid argument
lou@c-67-163-247-106:~$

](*,)

---

### Post by taurus on 2006-03-29
What video card do you have?  Maybe you just need to install a driver for it...

---

### Post by TylerH on 2006-03-29
pretty sure you can use Automatix to enable DMA as well.... seemed to do the trick for me

---

### Post by wolfee on 2006-03-29
I looked everywher this computer was given to me it's a sony viao pcv-7732
I found something on a forum
8xAGP GeForce 4 Ti 4200 Verto 64mb 
but not sure if this is it

---

### Post by wolfee on 2006-03-29
[QUOTE=TylerH]pretty sure you can use Automatix to enable DMA as well.... seemed to do the trick for me[/QUOTE]
 That worked great!!! Now I need to figure out how to make screen brighter from software since monitor is up all the way and movie are still dark. Will dma on from automatix work with most machines amd laptops?[-( =D>

---

