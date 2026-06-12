---
title: "Trying to get isight camera working on Intel iMac"
date: 2011-09-01
forum: Apple Hardware Users
---

### Post by rmcellig on 2011-09-01
So far, I have the required file from my Mac OS 10.5 installation sitting on my Ubuntu desktop. So far so good. Then I went into a terminal window to install the terminal tools. How do I launch the tools so that I can continue? This is what I get in the terminal window. See attached.

Thanks!

Randy

---

### Post by dfacto on 2011-09-07
sudo dpkg-reconfigure isight-firmware-tools

---

### Post by rmcellig on 2011-09-07
This is what happened after the patch. Is there anything else I need to do aside from restarting and trying the camera in Cheese?

home@home-iMac:~$ sudo dpkg-reconfigure isight-firmware-tools
[sudo] password for home: 
home@home-iMac:~$ sudo dpkg-reconfigure isight-firmware-tools
** Message: Found firmware signature at offset 0x20D8.
** Message: Firmware extracted successfully in /lib/firmware/isight.fw
** Message: Firmware version 2.37.92 (0x02.0x25.0x5C)
** Message: Apply patch 0 : Fix device descriptor
** Message: Apply patch 1 : Fix interface assocation descriptor
** Message: Apply patch 2 : Fix video interface collection
** Message: Apply patch 3 : Fix video streaming device qualifier
** Message: Apply patch 4 : Fix video control interface descriptor
** Message: Apply patch 5 : Fix video streaming interface descriptor
** Message: Firmware patched successfully
home@home-iMac:~$

---

### Post by dfacto on 2011-09-08
Ummm....use it?

---

### Post by rmcellig on 2011-09-08
I tried with Cheese but it doesn't see the camera.

---

### Post by dfacto on 2011-09-08
> **rmcellig said:**
> I tried with Cheese but it doesn't see the camera.

```

sudo modprobe -r uvcvideo
sudo modprobe uvcvideo
dmesg|tail -10

```

Paste output back here.

---

### Post by rmcellig on 2011-09-08
home@home-iMac:~$ sudo modprobe -r uvcvideo
[sudo] password for home: 
Sorry, try again.
[sudo] password for home: 
home@home-iMac:~$ clear
home@home-iMac:~$ sudo modprobe -r uvcvideo
home@home-iMac:~$ sudo modprobe uvcvideo
home@home-iMac:~$ dmesg|tail -10
[   30.956018] eth0: no IPv6 routers present
[   36.446351] hfs: write access to a journaled filesystem is not supported, use the force option at your own risk, mounting read-only.
[   37.504612] hfs: write access to a journaled filesystem is not supported, use the force option at your own risk, mounting read-only.
[   37.573346] hfs: write access to a journaled filesystem is not supported, use the force option at your own risk, mounting read-only.
[   37.867800] hfs: write access to a journaled filesystem is not supported, use the force option at your own risk, mounting read-only.
[   38.889616] EXT4-fs (sda4): re-mounted. Opts: errors=remount-ro,commit=0
[13105.525753] exe (2998): /proc/2998/oom_adj is deprecated, please use /proc/2998/oom_score_adj instead.
[32944.700711] Linux video capture interface: v2.00
[32944.726639] usbcore: registered new interface driver uvcvideo
[32944.726642] USB Video Class driver (v1.0.0)
home@home-iMac:~$

---

### Post by dfacto on 2011-09-08
Hmmm not sure why its not working.  I can tell you that the driver is not picking up the firmware that you dumped though.  I'm guessing you don't have a FaceTime camera?  Is this an older Mac?

---

### Post by rmcellig on 2011-09-08
It's an iMac (24 inch) from 2006 with the built in isight camera.

---

### Post by dfacto on 2011-09-08
Sorry, I'm not familiar with older cameras.  My only experience is with the newer ones and even this experience is limited.

---

### Post by shmibs on 2011-09-08
yeah, isight is really finicky. i had problems getting isight-firmware-tools to function on my late 2007 macbook as well. the instructions here ([ https://help.ubuntu.com/community/MactelSupportTeam/AppleiSight?action=show&redirect=AppleiSight]("https://help.ubuntu.com/community/MactelSupportTeam/AppleiSight?action=show&redirect=AppleiSight") ) 'should' do the trick. also, remember that, when reinstalling isight-firmware-tools to try again, you have to purge it first or the dialogue asking where to find the firmware will not reappear.
like i said, this 'should' work, but it didn't for me until i installed xubuntu on top of my ubuntu 10.10 install and booted it once or twice. i have no idea what was going on there:P

---

### Post by dfacto on 2011-09-08
Correction: you don't need to purge, "dpkg-reconfigure -phigh" should be equivalent to any purge, reinstall.

---

### Post by rmcellig on 2011-09-08
Thanks for the info. I will keep trying. So there are people out there with iMacs that actually have the camera working properly?

---

