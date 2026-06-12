---
title: "wont boot into GUI"
date: 2006-08-19
forum: Absolute Beginner Talk
---

### Post by The Pinny Parlour on 2006-08-19
ARGH   Darn this ubuntu   cursed thing it is.

Everything was nice.  New vid card Automatix nvidia driver install.

I started the machine this morning and went stright to the lowest resolution possible.   Now the thing boots into CLI.

I have tried the sudo dpkg-reconfigure xserver-xorg.  It crashes when I try to enter the bit rate 24.  Says something about overwriting some saved setting.  Why can't this be made a heck of alot easier?  

Can anyone chime in and help please?

---

### Post by tribaal on 2006-08-19
Can't really help you with the xorg specifics, but once you're dropped to CLI try to launch the Xserver manually with *gdm* (if you run ubuntu) or *kdm* if you run kubuntu.

This should take you to the graphical login and hopefully boot into the GUI.

Hope this helps...

- trib'

---

### Post by The Pinny Parlour on 2006-08-19
gdm?   How does that command go again?

I just typed sudo gdm.  Says it's already running.


Gee I hope edgy comes with some better way of doing video modes as the current xserver-xorg is utter crap

---

### Post by scxtt on 2006-08-19
try typing **startx** ...

xorg isn't crap, you're just not accustomed to it...

---

### Post by The Pinny Parlour on 2006-08-19
Thanks for your help.

startx.   didn't do much but make the screen scroll and the only thing worth mentioning is [EE] No devices detected.

Still no GUI.  ](*,)  

I don't want to go back to windows.  Please help.

---

### Post by scxtt on 2006-08-19
it'd probably be helpful if you could post your /etc/X11/xorg.conf (yeah, i know that can be difficult using CLI) -- but we can work through that if you still have a working internet connection ...

---

### Post by ComplexNumber on 2006-08-19
**The Pinny Parlour**
you mention that "I started the machine this morning and went stright to the lowest resolution possible.   Now the thing boots into CLI.".
cany you remember if you did anything 'significant' the day before which may have caused something like this? for example, did you try to update your graphics drivers whilst you were logged into gnome? 
another alternative is that you may be short of hard disk space. type in 'df -c' and post what it says here if you think that may be the case.
also, have you been using 'sudo' to open GUI applications such as gedit or nautilus instead of using gksudo?

> 
didn't do much but make the screen scroll and the only thing worth mentioning is [EE] No devices detected.
i don't quite understand this bit.

---

### Post by JoshHendo on 2006-08-19
I am assuming the screen was turned off when you turned the computer on and it was in the lowest res possible?

I don't know why this happens, but if the monitor is turned off when you reach GDM it will go to a low res. I hope this is fixed in Edgy :)

- Josh

---

### Post by The Pinny Parlour on 2006-08-19
Updated graphics driver yes.

Installed new HDD 320gig so I'm not short of space.

     anyways.  I did the following:

Default Re: Linux guru, please help. "Failed to start the X server"
Quote:
Originally Posted by PandaToledo
"xserver-xorg postinst warning: overwriting possibly-customised configuration file; backup in /etc/X11/xorg.conf.200602071512
This just warns you that it's overwriting your xorg.conf. In other words it's not a problem.

Do this:
sudo nano /etc/X11/xorg.conf

then scroll down the file and get to the Section "Device"
and set the driver to "vesa" like in the following example:
Code:

Driver "vesa"


Press:
CTRL+O to save the file (yes, overwrite it)
CTRL+X to exit

then type:
sudo /etc/init.d/gdm stop (or "kdm stop" if you use Kubuntu)
sudo /etc/init.d/gdm start (or "kdm start" if you use Kubuntu)



This has got me in the GUI    the nvidia driver is not working though.   Will reinstall nvidia driver using automatix and reboot and see what happens

---

### Post by ComplexNumber on 2006-08-19
when you installed the new graphics driver, do you boot into gnome before attempting to do so? or did you try to install it when in failsafe terminal(ie when you login, you get the option in Sessions of booting into gnome or failsafe terminal, which is basically just a terminal and nothing else)? 
i just thought i'd mention that because graphics drivers cannot be installed whilst logged into gnome or kde. either it simply will not work or it will mess something up.

---

### Post by scxtt on 2006-08-19
i install fglrx while in Gnome/KDE ... it doesn't take immediate effect until you restart the X-server ...

---

### Post by The Pinny Parlour on 2006-08-19
I just let automatix do it.   Is there a better/correct way of installing nvdia drivers?  At the moment my device is set to "vesa".  and everything looks abit washed out on the screen.

---

### Post by ComplexNumber on 2006-08-19
> **The Pinny Parlour said:**
> I just let automatix do it.   Is there a better/correct way of installing nvdia drivers?  At the moment my device is set to "vesa".  and everything looks abit washed out on the screen.
i downloaded the rpm's(i use fedora), logged out, logged into failsafe terminal, typed 'rpm -Uvh *' on the commandline in the directory where the drivers are, then rebooted.

---

### Post by The Pinny Parlour on 2006-08-19
I just let automatix do the nvidia driver install.  I just opened xorg.conf with nano:  sudo nano /etc/X11/xorg.conf    to see what changed.  It had made changes.  While I was in there I edited the Hor and Ver Frequency to my monitors exact specifications.  Saved/rebooted.  All appears good now.


Thank you helpers.  I think I will just skip xorg ultra-crap wizard and just edit it via nano in the future.  I hope some smart person can make xorg easier in the future as well.  Hoping edgy will have some REAL (cutting) EDGY features.

---

