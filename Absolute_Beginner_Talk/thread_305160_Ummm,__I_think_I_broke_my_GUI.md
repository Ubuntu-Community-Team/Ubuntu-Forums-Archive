---
title: "Ummm,  I think I broke my GUI"
date: 2006-11-22
forum: Absolute Beginner Talk
---

### Post by BlocknBleed on 2006-11-22
I can't load the desktop. In my neverending quest to not leave well enough alone I managed to try to change my graphic driver to somehting that would accommodate googleearth and in the process I killed my GUI. I tryed changing from nv to nvidia driver by modifying the /etc/X11/xorg.conf file and now it says x server wont run and something about gdm. 

I'm in over my head here, can someone tell me why when I reverse what I changed it won't go back to normal?

graphic card: nVidia GeForce4 Ti4200

Is there a way to restore or last know good like in windows?

---

### Post by LLRNR on 2006-11-22
Ok this will rewrite your xorg.conf, so there's a slight possibility that you'd have to do some tweaking again once you're done... but hopefully it will give you your GUI back. You will run through a series of questions... just answer as correct as you can.
```
sudo dpkg-reconfigure xserver-xorg
```

Good luck!

LLRNR

---

### Post by BlocknBleed on 2006-11-22
thanks I'll give it a try

---

### Post by PartisanEntity on 2006-11-23
Did you backup your xorg.conf file before changing anything? If yes you can restore the backed up copy without having to reconfigure xserver-xorg (someone correct me if I am wrong, I am a newb).

---

### Post by Bachstelze on 2006-11-23
Just changing 'nv' to 'nvidia' won't install the drivers for you ;) If you tell your X server to use 'nvidia' drivers but they are not installed, no wonder it can't run ;)

---

### Post by steve.horsley on 2006-11-23
the command **sudo nano /etc/X11/xorg.conf** will allow you to edit the file and change "nvidia" back to "nv".

Alternatively, 
**sudo apt-get install nvidia-glx**
should install the missing nvidia driver that you told it to use.

---

### Post by Bachstelze on 2006-11-23
Not exactly, *nvidia-glx* will only install the runtime libraries. The actual driver (the kernel module) is in *linux-restricted-modules-$(uname -r)*, so it's needed as well.

---

### Post by steve.horsley on 2006-11-23
It actially lists 11 dependencies. I believe they will be pulled in as part of the install process. I know I have installed the nVidia drivers before by only installing that one package.

---

### Post by Bachstelze on 2006-11-23
I thought that too but if you go [here](http://packages.ubuntu.com/edgy/x11/nvidia-glx), you'll see nvidia-glx depends only on linux-restricted-modules-common, which won't install the actual module either. Maybe you had your linux-restricted-modules -$(uname -r) already installed somehow.

---

### Post by steve.horsley on 2006-11-24
Sorry, I don't understand. I looked that the link ([http://packages.ubuntu.com/edgy/x11/nvidia-glx)](http://packages.ubuntu.com/edgy/x11/nvidia-glx)), and it shows 11 red balls, which I take to be 11 dependencies. The tenth in the list is nvidia-kernel-1.0.8776.

---

### Post by Bachstelze on 2006-11-24
My mistake, you're right, I didn't notice the virtual package...

---

