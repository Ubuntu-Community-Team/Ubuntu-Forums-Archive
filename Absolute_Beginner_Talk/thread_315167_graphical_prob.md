---
title: "graphical prob"
date: 2006-12-08
forum: Absolute Beginner Talk
---

### Post by spliffy on 2006-12-08
right hello all,
my system is a:
3700 amd
an8 sli
x800gto
gig dual chan ram

my problem is when i goto install ubuntu i get the error message saying,
failed to start the x server (your graphical interface)it is likely that it  is not set up correctly.

as u no im a new and no very little bout linux can u plz tell me how to get set it up plz thanks

---

### Post by taurus on 2006-12-08
Why don't you use the alternate CD to install it on your machine.  It comes with everything that the LiveCD has so there shouldn't be a difference except it uses text base installer so no need to boot into Live first before you can install it.

[http://www.gtlib.gatech.edu/pub/ubuntu-releases/edgy/](http://www.gtlib.gatech.edu/pub/ubuntu-releases/edgy/)

---

### Post by spliffy on 2006-12-10
i have installed it to my hdd but when i try to log in the first time i still get the same massage plz plz help

---

### Post by bulldog on 2006-12-10
Try to reconfigure the X-server,type in your console after log in```
sudo dpkg-reconfigure -phigh  xserver-xorg
```

---

### Post by spliffy on 2006-12-11
i dont  get to login it gos straight to that message

---

### Post by taurus on 2006-12-11
Boot into recovery mode from GRUB menu and at the prompt, reconfigure your X again...

```
dpkg-reconfigure -phigh xserver-org
```

---

### Post by spliffy on 2006-12-15
i did an gotinto the setup, i put the folling:

-autodetects video hardware <yes>
-Xserver driver defaults to "ati", 
-identifier for video card: ATI Technologies, Inc. Rage XL
-video card's bus identifier: PCI:1:0:0
amount of memory (in kB) for video card:<blank>
-use kernel framebuffer device interface? <yes>
-autodetect keyboard layout <yes>
-select keyboard layout: "gb"
-select XKB rule to use: "xorg"
-select keyboard model: "pc105"
-select keyboard variant: (blank)
-select keyboard options: (blank)
-describe your mouse: "ImPS/2"
-emulate 3 button mouse <yes>
-select Xorg modules to be loaded by default: bitmap, ddc, dri, extmod, freetype, glx, int10,. type1, vbe
-write default files section to config file: <yes>
-attempt monitor autodetection: <yes>
-identifier for monitor: "Generic Monitor"
-select video modes you would like to use: (1024x768, 800x600, and 640x480 were enabled by default) i only tryed 1024x768 and 640x480
-choose method for selecting monitor characteristics: Medium (1024x786 at 60Hz)
-desired color depth in bits: tryed 24 an 16
-"sudo reboot"

and i still get this bloody message wot do i have to change??or do or sumthing

---

### Post by Bachstelze on 2006-12-15
Use the "vesa" driver instead of "ati", then you can install proper ATi drivers to get 3D accel if you want.

---

### Post by spliffy on 2006-12-16
the vesa driver seems to work with most ppl but not me, i think its time for a defeat,an time to go bk to windows.](*,) :confused:

---

### Post by drphilngood on 2006-12-16
Try this:
```
sudo apt-get install xorg-driver-fglrx
sudo aticonfig --initial
sudo aticonfig --overlay-type-Xv
```

See here for more info:
[http://www.ubuntuforums.org/showthread.php?t=190133]("http://www.ubuntuforums.org/showthread.php?t=190133")

---

### Post by spliffy on 2006-12-18
WOW it worked im in ubuntu,now the only prob i have is i carnt renember wot my user name an p/w is lol thanks

---

### Post by taurus on 2006-12-18
Boot into recovery mode from GRUB menu and at the prompt, look in /etc/passwd to see what's your login name is (usually near the end of it)...

```
cat /etc/passwd
```
Assuming it's called spliffy, give spliffy a new password with

```
passwd spliffy
```
Reboot and try to login with spliffy and the new password.

```
shutdown -r now
```

---

### Post by spliffy on 2006-12-18
when i try an look in /etc/passwd it says permission denied.

if i do cat /etc/passwd it come up with lots of stuff but i carnt seem to see anything that might b my user or pw
soryy to b such a *******.:mrgreen:

---

### Post by taurus on 2006-12-18
What are the last few lines in /etc/passwd say?

```
tail  /etc/passwd
```
Otherwise, what is the output of this command then?

```
ls -la /home
```

---

### Post by spliffy on 2006-12-18
tail  /etc/passwd =
dhcp:100:101::/nonexistent:/bin/false
syslog:x:101:102::/home/syslog:/bin/false
klog:x:102:103::home/klog:/bin/false
messagebus:x:103:107::/var/run/dbus:/bin/false
avahi:x:104:108:Avahi mDNS daemon ,,,:/var/run/avahi-daemon:bin/false
cupsys:x:105:109::/home/cupsys:/bin/false
haldaemon:x:106:110:hardware abstraction layer,,,:/var/run/hal:/bin/false
hplip/:107:7:HPLIP system user , , , :/var/run/hplip:/bin/false
gdm:x:108:113:Gnome Display Manager:/var/lib/gdm:/bin/false
oem:x:29999:29999:OEM configuration (temporary user) , , ,:/home/oem:/bin/bash

ls -la /home =
drwxr-xr-x 3 root root 4096 Dec 12 16:45
drwxr-xr-x 22 root root 4096 Dec 18 14:39
drwxr-xr-x 2 oem oem 4096 Dec 12 16:45

Have i done sumthing wrong when installing coz it dont look like the username or pass inthere? thanks taurus you have been a grate help

---

### Post by spliffy on 2006-12-18
lol the smilles ant me

---

