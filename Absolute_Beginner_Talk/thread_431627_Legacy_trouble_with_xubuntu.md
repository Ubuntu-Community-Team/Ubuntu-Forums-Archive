---
title: "Legacy trouble with xubuntu"
date: 2007-05-03
forum: Absolute Beginner Talk
---

### Post by duffman.c.d on 2007-05-03
Hi,
I'm new to linux and I'm having troubles with the nvidia drivers.
I have installed xubuntu 6.10 then immediately updated to Feisty.

I have a nVidia TNT and have tried installing the nvidia-glx-legacy drivers via synaptic and then activating first by typing " sudo nvidia-glx-config enable" then via restricted drivers manager.
The first time seemed to work until I restarted (I tested by running blender) at which point X.org wouldn't start.

It came up with an error message and then a longer one. Is there any way to save these?
I found an old org.conf and restored it and tried again (with drivers manager) to the same result.

How do I get the nVidia drivers working?:confused: 

Thanks in advance,
Duffman

---

### Post by hencke on 2007-05-03
> **duffman.c.d said:**
> Hi,
I'm new to linux and I'm having troubles with the nvidia drivers.
I have installed xubuntu 6.10 then immediately updated to Feisty.

I have a nVidia TNT and have tried installing the nvidia-glx-legacy drivers via synaptic and then activating first by typing " sudo nvidia-glx-config enable" then via restricted drivers manager.
The first time seemed to work until I restarted (I tested by running blender) at which point X.org wouldn't start.

It came up with an error message and then a longer one. Is there any way to save these?
I found an old org.conf and restored it and tried again (with drivers manager) to the same result.

How do I get the nVidia drivers working?:confused: 

Thanks in advance,
Duffman

I think installing those drivers should be done either through synaptic or with the restricted drivers manager. Trying both might get it messed up. It is very nice that synaptic tells you to "sudo nvidia-glx-config enable" but it doesn't tell you to restart your xserver. Did you do this? To do this you should logout and select "Restart xserver". If x fails at this point restart into safe mode and type:

cd /etc/X11
ls

You will find a backup of your xorg.conf with a date after it. Type:

sudo cp xorg.conf.yymmddtttt xorg.conf

to recover your working xorg.conf.

Type

startx

to start the xserver or

shutdown -h now

to shutdown.

Duffman, please go to synaptic and check that you have only the legacy driver installed and that your xorg.conf has

Driver "nvidia" 
in 
Section "Device"

If not, then make sure you only have the legacy driver installed and then type

sudo nvidia-glx-config enable

once again and this time restart your xserver and see what happens.

If you have restarted your computer (or xserver) and your xorg.conf uses "nvidia" then you have are using the proprietary driver provided by nVidia, but this does not mean that all 3D applications will work. Please try running an (several) application(s) you have problems with in the terminal and post the output (the common error in the outputs).

Anybody wondering which nvidia driver they should use with their specific card can see:

[http://ubuntuforums.org/showthread.php?t=416563](http://ubuntuforums.org/showthread.php?t=416563)

---

### Post by duffman.c.d on 2007-05-04
Perhaps I didn't explain properly the first time,:oops: 
I installed nvidia-glx-legacy (BTW yes thats the only one installed), then I tried to enable it with "nvidia-glx-settings enable" that seemed to work until I restarted, when Xorg didn't start. So, I copied over the old xorg.conf and tried again with restricted drivers manager-to the same result: A blue screen with "X was not able to start... do you want to view [output? (I think)]"

My graphics card works fine in Windows and I would like to try some 3D under linux.

Once again preemptively, thanks for the help.

Duffman

---

### Post by hencke on 2007-05-16
I'm not sure if I can help, but if you'd like to post your xorg.conf, I might find out what's wrong with it... The Device, Monitor, Screen, ServerLayout, Module sections should be more than enough. Preferrebly from the working and non-working one. Also If you could post the relevant lines from the "output" with EE or WW in the front of them, it might help. I'll try and reply sooner next time...

---

