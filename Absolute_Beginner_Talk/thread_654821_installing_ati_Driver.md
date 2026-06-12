---
title: "installing ati Driver"
date: 2007-12-31
forum: Absolute Beginner Talk
---

### Post by frenchsquared on 2007-12-31
Hello again

ok Im back

I did have to reinstall

under applications I have Catalyst
so some progress
but it inst doing anything
still using generic driver and screen resolution is to low

so now what

---

### Post by frenchsquared on 2007-12-31
gordon@Gateway:~$ sudo aticonfig --initial
Uninitialised file found, configuring.
Using /etc/X11/xorg.conf
Saved back-up to /etc/X11/xorg.conf.original-0
gordon@Gateway:~$ sudo aticonfig --overlay-type=Xv
Warning: Option 'VideoOverlay' doesn't affect running session.
Warning: Option 'OpenGLOverlay' doesn't affect running session.
Using /etc/X11/xorg.conf
Saved back-up to /etc/X11/xorg.conf.fglrx-0
gordon@Gateway:~$

---

### Post by frenchsquared on 2007-12-31
its using driver "fglrx"

that is different but not correct

---

### Post by Afkpuz on 2007-12-31
Did you try installing the ati restricted driver?  

System>Administration>Restricted Driver Manager

---

### Post by frenchsquared on 2007-12-31
gordon@Gateway:~$ gksu gedit /etc/default/linux-restricted-modules-common
gordon@Gateway:~$ sudo rm /usr/src/fglrx-kernel*.deb
rm: cannot remove `/usr/src/fglrx-kernel*.deb': No such file or directory
gordon@Gateway:~$ sudo dpkg -i xorg-driver-fglrx_8.443.1-1*.deb fglrx-kernel-source_8.443.1-1*.deb fglrx-amdcccle_8.443.1-1*.deb
dpkg: error processing xorg-driver-fglrx_8.443.1-1*.deb (--install):
 cannot access archive: No such file or directory
dpkg: error processing fglrx-kernel-source_8.443.1-1*.deb (--install):
 cannot access archive: No such file or directory
dpkg: error processing fglrx-amdcccle_8.443.1-1*.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 xorg-driver-fglrx_8.443.1-1*.deb
 fglrx-kernel-source_8.443.1-1*.deb
 fglrx-amdcccle_8.443.1-1*.deb
gordon@Gateway:~$ 


it isnt listed in the restriced drivers only my wireless card is

---

### Post by Don1500 on 2007-12-31
Well, Finally I have the ATI card installed right. After reading all the disclaimers and trying 15 different "guaranteed" methods of flawless installation, I used [[COLOR="Red"]Envy (linked)[/COLOR]]("http://www.albertomilone.com/nvidia_scripts1.html"). It loaded easy, even after I goofed up and stopped it half way through.

Please try this, it may save you hours of frustration.

---

### Post by frenchsquared on 2007-12-31
I installed envy but it doesnt seem to do anything
how do i use it

---

### Post by frenchsquared on 2007-12-31
Envy wasnt installed correctly
Its doing something so I let you know if it works

Thanks

---

### Post by Don1500 on 2007-12-31
Check under Applications=> System Tools There should be a new program for you, called Envy
Install the missing dependencies (automatic, just click yes)
Then select your option. (Install ATI driver)

---

### Post by skaldicpoet9 on 2007-12-31
Hey man :)

I have the same thing going on but I think that the driver may be installed on your comp.
Try typing in aticonfig in the console and it should bring up a list off commands for the ATI driver (if it is installed). I know I am a noob too but it seemed to work for me (however I can't figure out how to use the command line to change the resolution but it is there nonetheless).

---

### Post by frenchsquared on 2007-12-31
Envy **WORKED**

YAH it only took three installes of  ubuntu but envy fixed

I  just didnt have envy installed completly

Thanks all

---

