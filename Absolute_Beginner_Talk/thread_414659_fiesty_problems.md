---
title: "fiesty problems"
date: 2007-04-20
forum: Absolute Beginner Talk
---

### Post by championboxes on 2007-04-20
I installed ubuntu 7.04 via the alternate i386 cd... my problem is that whenever the login screen should come up there is a black screen... i can type in my username and password and i will hear the startup music...  my question is there a way i can install drivers using the terminal Ctrl-Alt-F1... I have a alienware m9700 laptop... AMD-Turion ML-44, 2GB RAM, dual 256MB NVIDIA 7900 GS's...

Thanks,
Championboxes...

---

### Post by kinalus on 2007-04-20
Hi,
this command should install the nvidia drivers for you:
# sudo apt-get install nvidia-glx
then you need to enable the drivers by doing this:
# sudo nvidia-glx-config enable
good luck

---

### Post by championboxes on 2007-04-21
I tried that just a min ago... it looked like it installed but it is still doing the same thing but now i cant get into the terminal...

---

### Post by Outrunner on 2007-04-21
After typing your username and password do you get a command prompt(like user-user-desktop:)? If so try typing startx , that is assuming that you have x server installed.

---

### Post by peebly on 2007-04-21
would it not be nvidia-glx-new as nvidia-glx is the old driver.

---

### Post by annda on 2007-04-21
you can't use ALT+F1 etc.? try booting into recovery mode and see what your
/etc/X11/xorg.conf
file looks like. does it have the 'nvidia' driver, or still 'nv'? if it's still nv, change it.

---

### Post by championboxes on 2007-04-22
Ok... i installed nvidia-glx and the login screen still never came up and i cant go into the terminal by pressing Ctrl-Alt-F1

i went into the recovery mode thing and looked at /etc/X11/xorg.conf and it said "nvidia"

i also tried installing nvidia-glx-new wihich it installed but still where the login screen should be there is a black screen... with this driver installed i can hear the little drum sound where you need to logon but its just a black screen... 

i can do Ctrl-Alt-F1 and i think i goes into the terminal but the screen is black so i really cant tell what im doing...

whenever i installed the nvidia-glx-new driver it said that it made a backup of my /etc/X11/xorg.conf file...

how would i go back to that?

---

### Post by championboxes on 2007-04-23
i got fiesty to work...

i found it here===>   [http://ubuntuforums.org/showthread.php?t=233340&page=2&highlight=m9700](http://ubuntuforums.org/showthread.php?t=233340&page=2&highlight=m9700)



Press Ctrl + Alt + F1 to get to the console

Download NVIDIA drivers:
For 32-bit:
Code:

#] wget [http://us.download.nvidia.com/XFree86/Linux-x86/1.0-9755/NVIDIA-Linux-x86-1.0-9755-pkg1.run](http://us.download.nvidia.com/XFree86/Linux-x86/1.0-9755/NVIDIA-Linux-x86-1.0-9755-pkg1.run)

For 64-bit:
Code:

#] wget [ftp://download.nvidia.com/XFree86/Linux-ia64/1.0-5336/NVIDIA-Linux-ia64-1.0-5336-pkg1.run](ftp://download.nvidia.com/XFree86/Linux-ia64/1.0-5336/NVIDIA-Linux-ia64-1.0-5336-pkg1.run)

Type the following
Code:

#] sudo apt-get install build-essential
#] sudo /etc/init.d/gdm stop
#] sudo killall gdm
#] sudo sh NVIDIA-Linux-x86-1.0-9755-pkg1.run

Run though the NVIDIA wizard and it will compile and install a driver for your system. Ensure that it compiles and that it modifies the X config for you.

Last step:
Code:

#] sudo /etc/init.d/gdm restart

---

### Post by dyssident on 2007-05-26
the above solution worked for me. unfortunately, although X is now running, the gnome desktop never loads after login. any suggestions on where to start figuring out how to get gnome to load would be appreciated.

---

