---
title: "[SOLVED] Xserver help"
date: 2007-12-11
forum: Absolute Beginner Talk
---

### Post by Quicksilver21 on 2007-12-11
im a newb to linux and i got the newest nvidia driver installed and everything but when i get towards the end it says:
   "unable to perform the runtime configuration check for library 'libGL.so.1'"
then it continues installing and assumes success. Everything works fine until i reboot. After that it goes back to the old xserver config and makes me run in low graphics mode. 
   anyone know how to enable the nvidia xserver and make it the default one?

---

### Post by bodhi.zazen on 2007-12-11
If you installed the nvidia driver you should be able to run :

```
gksu nvidia-settings
```

Set up your monitor and save your settings.

---

### Post by Quicksilver21 on 2007-12-11
i type that and then it brings up the nvidia control panel and it says:

 You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server.

---

### Post by oeolycus on 2007-12-11
so the commands would be

```
sudo nvidia-xconfig
```

and then ctrl+alt+backspace to reset X.

(I hope I'm right--am I right?)

---

### Post by Quicksilver21 on 2007-12-11
that doesnt help, btw when i try to save my xserver config it says "Unable to remove old X config backup file '/etc/X11/xorg.conf.backup'."

---

### Post by bodhi.zazen on 2007-12-11
It sounds like the nvidia driver is not properly installed.

1. What video card do you have ?

2. How did you install the nvidia driver ?

3. It might be helpful if you were to post the actual error message / terminal output. 

FYI: You can cut-and-paste from the terminal to here.

---

### Post by Quicksilver21 on 2007-12-12
It sounds like the nvidia driver is not properly installed.

1. What video card do you have ?

2. How did you install the nvidia driver ?

3. It might be helpful if you were to post the actual error message / terminal output. 
---------------------------------------------------------------------------------------------------------------------------

1. I have an nvidia 7600gt

2. i pressed CTRL+ALT+F1
    then i typed sudo /etc/init.d/gdm stop
    then i typed sudo sh /home/username/"the name of the newest nvidia driver"
    then after i install it i type sudo /etc/init.d/gdm start

3.when I go to Applications-->System Tools-->NVIDIA X Server Settings it gives me this error “You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server.

---

### Post by bodhi.zazen on 2007-12-12
OK, I have the same card ...

1. When you re-start GDM, do you get the nvidia splash screen ?

2. Did you ever install the open-source drivers ? You may need to remove nvidia-glx and re-install the nvidia driver.

3. What happens when you ;```
modprobe nvidia
``` ??

---

### Post by Quicksilver21 on 2007-12-12
yes i get the splash screen but once i restart the computer i dont have it.

and i went here and downloaded the driver:
 [http://www.nvidia.com/object/linux_display_amd64_100.14.19.html](http://www.nvidia.com/object/linux_display_amd64_100.14.19.html)

when i put in that command nothing happens

---

### Post by bodhi.zazen on 2007-12-12
My guess is you are having a conflict with the open source driver.

Try removing nvidia-glx and re-installing the nvidia driver. If you have nvidia-glx new installed, there is a bug, and it does not remove itself properly, causing exactly your problem.

[https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.22/+bug/106217](https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.22/+bug/106217)

---

### Post by Quicksilver21 on 2007-12-13
okay so i gave up on fixing it and did a re-install and i havnt installed anything, i enabled the default driver that came with ubuntu and i updated everything and i was wondering if you could tell me how to install the right way?

---

### Post by bodhi.zazen on 2007-12-13
what driver are you using then ? What driver is listed in /etc/X11/xorg.conf ?

I assume it is the open source, or "nv" driver ?

Also search with synaptic and see if the nvidia-glx and / or nvidia-glx-new driver(s) are installed.

If it is, you will need to remove the opensource or "restricted" driver, aka nvidia-glx.

Then install the nvidia driver as you did.

If you have the nvidia-glx-new driver installed, you will need to remove that and follow the link I gave you to the bug report for a fix.

If neither the nvidia-glx or nvidia-glx-new driver is installed, skip all that and just go ahead and install the nvidia driver as you did before (I assume you installed the kernel headers and build-essential).

---

### Post by Quicksilver21 on 2007-12-13
alright thank you for all the help it works now :)

p.s. linux rocks

---

