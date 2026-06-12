---
title: "Can't set resolution.."
date: 2008-01-22
forum: Absolute Beginner Talk
---

### Post by makko on 2008-01-22
Hi,

My resolution is set to 1024x780 but the icons,windows,title bars,text in webpages is too big. It's the same resolution as on my windows xp but everything is bigger. It give me a pain in my head when I have to use ubuntu now..No matter what I change the res to it stays the same but sometimes when I boot it goes into safe graphics mode or something like that..

Do I need to install drivers for my graphics card or something?

I am using a dell inspiron 6000 with the INTEL MEDIA ACCELERATOR 900 GRAPHICS and 15.4 INCH WXGA LCD PANEL..

I've read about editing the XORG.CONF file but how exactly do I do that?

Thanks..

---

### Post by S15_88 on 2008-01-22
go to the terminal and type: sudo nautilus
navigate to: /etc/X11/xorg.conf

open that up and go down to the resolution section and add your preffered settings, not sure if this will fix your problem or not.

keep in mind editing your xorg.conf can be tricky sometimes make sure u have a back up that you can revert to.

Thanks, Alain

---

### Post by JoshuaRL on 2008-01-22
Another way is to type in the terminal:

```

sudo gedit /etc/X11/xorg.conf

```

It will open it in Gedit (short for Gnome Edit).  You would want to scroll down to the Device "Screen"  And make sure your desired resolution is there in that section.  Just read through it carefully, it should make sense.  If not, you can post it here and we'll help.

---

### Post by spiderbatdad on 2008-01-22
nautilus is a folder browser. I do not believe you can edit anything from nautilus, instead you would need to:```
gksu gedit /etc/X11/xorg.conf
``` or use a terminal text editor. Please excuse if I am mistaken.

---

### Post by kyle.p on 2008-01-22
If I am not mistaken, sudo nautilus would allow makko to navigate to the xorg.conf file in a browser instead of having to use the terminal. Basically, it gives him sudo permission as he is navigating through a browser (so could edit xorg.conf by just double clicking and editing it in a text editor) rather than using terminal to navigate via text commands and then "sudo gedit..."

Both ways work. Sudo nautilus is a little scary because there is the risk of accidentally making a mistake while navigating and messing something up (of course with sudo permission), but if one is comfortable navigating a computer it might be ok. 

Depends on personal preference. 
Don't mind using terminal? Then use "sudo gedit.." as in previous post
Prefer to actually see what file you are editing or aren't comfortable in terminal? Maybe use sudo nautilus.

EDIT: I have used sudo nautilus before. I am currently not using ubuntu, so I cannot confirm specifics. Excuse me if I was mistaken myself. I am just going by memory.

---

### Post by bcrom on 2008-01-22
I strongly discourage you from trying to edit the xorg.conf file yourself.  It can be an enormously frustrating experience.  

First go to System->Administration->Restricted Drivers Manager and see if you can enable any video drivers, then reboot.  If that doesn't work, try going to System->Preferences->Screen Resolution.  If you can't fix it there try System->Administration->Screens and Graphics.  If that doesn't work and you have an nvidia graphics card try sudo```
 apt-get install nvidia-settings
``` in a terminal then run ```
sudo nvidia-settings
``` in a terminal.

---

### Post by glotz on 2008-01-22
offtopic but important
> **JoshuaRL said:**
> 
```

sudo gedit /etc/X11/xorg.conf

```

Never use sudo to launch a graphical app. Use gksudo. Otherwise you might face [ownership problems](http://www.psychocats.net/ubuntu/graphicalsudo).

gksudo for graphical
sudo for command line

---

### Post by crjackson on 2008-01-22
> **glotz said:**
> offtopic but important

Never use sudo to launch a graphical app. Use gksudo. Otherwise you might face [ownership problems](http://www.psychocats.net/ubuntu/graphicalsudo).

gksudo for graphical
sudo for command line


Good catch glotz....:KS

---

### Post by glotz on 2008-01-23
Thanks!

---

### Post by JoshuaRL on 2008-01-23
Dude, I didn't know that.  Thanks for enlightening me.  That was a good link too.

---

### Post by glotz on 2008-01-23
:oops:

---

### Post by moonfriedpotatoes on 2008-01-27
im having a very similar problem.  i used the restricted driver manager to get the driver, but it wouldnt enable correctly.  i then used envy, which installed and enabled the driver but still couldn't set the correct resolution or use effects.  i uninstalled the drivers and envy and tried  apt get install nvidia-settings, then running nvidia settings... all i got was a bunch fo errors.  

#moonfriedpotatoes@beater:~$ sudo nvidia-settings

ERROR: NV-CONTROL extension not found on this Display.


ERROR: Unable to determine number of NVIDIA GPUs on ':0.0'.


ERROR: Unable to determine number of NVIDIA Frame Lock Devices on ':0.0'.


ERROR: Unable to determine number of NVIDIA VCSCs on ':0.0'.


ERROR: Invalid X Screen 0 specified on line 19 of configuration file
       '/home/moonfriedpotatoes/.nvidia-settings-rc' (NV-CONTROL extension not
       supported on X Screen 0).


ERROR: Invalid X Screen 0 specified on line 20 of configuration file
       '/home/moonfriedpotatoes/.nvidia-settings-rc' (NV-CONTROL extension not
       supported on X Screen 0).


ERROR: Invalid X Screen 0 specified on line 21 of configuration file
       '/home/moonfriedpotatoes/.nvidia-settings-rc' (NV-CONTROL extension not
       supported on X Screen 0).


ERROR: Invalid X Screen 0 specified on line 22 of configuration file
       '/home/moonfriedpotatoes/.nvidia-settings-rc' (NV-CONTROL extension not
       supported on X Screen 0).


ERROR: Invalid X Screen 0 specified on line 23 of configuration file
       '/home/moonfriedpotatoes/.nvidia-settings-rc' (NV-CONTROL extension not
       supported on X Screen 0).


ERROR: Invalid X Screen 0 specified on line 24 of configuration file
       '/home/moonfriedpotatoes/.nvidia-settings-rc' (NV-CONTROL extension not
       supported on X Screen 0).


ERROR: Invalid X Screen 0 specified on line 25 of configuration file
       '/home/moonfriedpotatoes/.nvidia-settings-rc' (NV-CONTROL extension not
       supported on X Screen 0).


ERROR: Invalid X Screen 0 specified on line 26 of configuration file
       '/home/moonfriedpotatoes/.nvidia-settings-rc' (NV-CONTROL extension not
       supported on X Screen 0).


ERROR: Invalid X Screen 0 specified on line 27 of configuration file
       '/home/moonfriedpotatoes/.nvidia-settings-rc' (NV-CONTROL extension not
       supported on X Screen 0).


ERROR: Invalid X Screen 0 specified on line 28 of configuration file
       '/home/moonfriedpotatoes/.nvidia-settings-rc' (NV-CONTROL extension not
       supported on X Screen 0).


ERROR: Invalid X Screen 0 specified on line 29 of configuration file
       '/home/moonfriedpotatoes/.nvidia-settings-rc' (NV-CONTROL extension not
       supported on X Screen 0).


ERROR: Invalid X Screen 0 specified on line 30 of configuration file
       '/home/moonfriedpotatoes/.nvidia-settings-rc' (NV-CONTROL extension not
       supported on X Screen 0).


ERROR: Invalid X Screen 0 specified on line 31 of configuration file
       '/home/moonfriedpotatoes/.nvidia-settings-rc' (NV-CONTROL extension not
       supported on X Screen 0).


ERROR: Invalid X Screen 0 specified on line 32 of configuration file
       '/home/moonfriedpotatoes/.nvidia-settings-rc' (NV-CONTROL extension not
       supported on X Screen 0).


ERROR: Invalid X Screen 0 specified on line 33 of configuration file
       '/home/moonfriedpotatoes/.nvidia-settings-rc' (NV-CONTROL extension not
       supported on X Screen 0).


ERROR: Invalid X Screen 0 specified on line 34 of configuration file
       '/home/moonfriedpotatoes/.nvidia-settings-rc' (NV-CONTROL extension not
       supported on X Screen 0).


ERROR: Invalid X Screen 0 specified on line 35 of configuration file
       '/home/moonfriedpotatoes/.nvidia-settings-rc' (NV-CONTROL extension not
       supported on X Screen 0).


ERROR: Invalid X Screen 0 specified on line 36 of configuration file
       '/home/moonfriedpotatoes/.nvidia-settings-rc' (NV-CONTROL extension not
       supported on X Screen 0).


ERROR: Invalid X Screen 0 specified on line 37 of configuration file
       '/home/moonfriedpotatoes/.nvidia-settings-rc' (NV-CONTROL extension not
       supported on X Screen 0).


ERROR: Invalid X Screen 0 specified on line 38 of configuration file
       '/home/moonfriedpotatoes/.nvidia-settings-rc' (NV-CONTROL extension not
       supported on X Screen 0).


ERROR: Invalid X Screen 0 specified on line 39 of configuration file
       '/home/moonfriedpotatoes/.nvidia-settings-rc' (NV-CONTROL extension not
       supported on X Screen 0).


ERROR: Invalid X Screen 0 specified on line 40 of configuration file
       '/home/moonfriedpotatoes/.nvidia-settings-rc' (NV-CONTROL extension not
       supported on X Screen 0).


ERROR: Invalid X Screen 0 specified on line 41 of configuration file
       '/home/moonfriedpotatoes/.nvidia-settings-rc' (NV-CONTROL extension not
       supported on X Screen 0).


ERROR: Invalid X Screen 0 specified on line 42 of configuration file
       '/home/moonfriedpotatoes/.nvidia-settings-rc' (NV-CONTROL extension not
       supported on X Screen 0).


ERROR: Invalid X Screen 0 specified on line 43 of configuration file
       '/home/moonfriedpotatoes/.nvidia-settings-rc' (NV-CONTROL extension not
       supported on X Screen 0).


ERROR: Invalid X Screen 0 specified on line 44 of configuration file
       '/home/moonfriedpotatoes/.nvidia-settings-rc' (NV-CONTROL extension not
       supported on X Screen 0).


ERROR: Invalid X Screen 0 specified on line 45 of configuration file
       '/home/moonfriedpotatoes/.nvidia-settings-rc' (NV-CONTROL extension not
       supported on X Screen 0).


ERROR: Invalid X Screen 0 specified on line 46 of configuration file
       '/home/moonfriedpotatoes/.nvidia-settings-rc' (NV-CONTROL extension not
       supported on X Screen 0).


ERROR: Invalid X Screen 0 specified on line 47 of configuration file
       '/home/moonfriedpotatoes/.nvidia-settings-rc' (NV-CONTROL extension not
       supported on X Screen 0).


ERROR: NV-CONTROL extension not found on this Display.


ERROR: Unable to determine number of NVIDIA GPUs on ':0.0'.


ERROR: Unable to determine number of NVIDIA Frame Lock Devices on ':0.0'.


ERROR: Unable to determine number of NVIDIA VCSCs on ':0.0'.



#

what gives?  i've reconfigured xorg.conf which corrects my low resolution until i reboot, at which time i have to reconfigure again to get a usable resolution.  this has left me with about 20 backup copies of xorg.conf.  grrr...

---

### Post by bcrom on 2008-01-27
Nvidia-settings can't run if your nvidia drivers aren't enabled.  That's what these errors are.  

It's possible that envy has messed up your configuration files.  It did the same thing to me.  See if you can strip out everything nvidia that you've installed.  Then just install the nvidia restricted drivers and then nvidia-settings.  I had to do a fresh install of Ubuntu to fix the problems envy left.

---

