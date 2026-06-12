---
title: "webcam help"
date: 2007-03-02
forum: Absolute Beginner Talk
---

### Post by nonewmsgs on 2007-03-02
ok, so since my last webcam was not supported well, i hopped over to ebay and bought some cams with the 4-5 star rating from [http://mxhaard.free.fr/spca5xx.html](http://mxhaard.free.fr/spca5xx.html)
good news:
they use the same driver, sortof?
spca5xx and the one new one says spca5xx/LE

at the bottom it says that means it is possible to use both, but advises against the le unless you know what you're doing, and that means i havent tried the le, because i have fear.   i already have the spca5xx one installed, but i get no love from any program trying to use my cam.

under lsusb it says:
Bus 004 Device 004: ID 04fc:5330 Sunplus Technology Co., Ltd 

but all the programs keep saying "could not connect to video device (/dev/video0).  please check connection.

---

### Post by invalid on 2007-03-02
Is the driver module installed correctly, and activated?
Try```
lsmod | grep spca
```and see if it is actually in use.
If not, try```
sudo modprobe spca5xx
```

---

### Post by nonewmsgs on 2007-03-02
william@william-desktop:~$ lsmod | grep spca
spca5xx               635984  0 
videodev                9728  3 spca5xx,cx8800,cx88xx
usbcore               130304  7 snd_usb_audio,snd_usb_lib,usbhid,spca5xx,ehci_hcd,uhci_hcd
william@william-desktop:~$ sudo modprobe spca5xx
Password:
william@william-desktop:~$ (and nothing happend)

---

### Post by invalid on 2007-03-03
I can only suggest trying a program I know worked with a spca5xx device I used a while back, camstream, just to see what happens. Perhaps it is actually located on /dev/video1 or another node.

---

### Post by nonewmsgs on 2007-03-04
after gnome stopped working and i did the whole resetting xconfig it saw i :D  thank you for your ideas, they were much appriciated and knowing someone out there cared too gives a lot of moral support.

---

