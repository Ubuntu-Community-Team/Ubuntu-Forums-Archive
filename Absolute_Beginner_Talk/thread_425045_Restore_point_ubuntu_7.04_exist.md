---
title: "Restore point ubuntu 7.04: exist??"
date: 2007-04-27
forum: Absolute Beginner Talk
---

### Post by abduliounited on 2007-04-27
Hi All, 

I would like to restore the default configuration of my Ubuntu 7.04..is there a  command which I can use to restore my system as was before? I have a problem with my ATI video controller driver and I made few changes: I think I was typing some command to run X server or GDM something like that to fix my screen problem. Then I rebooted and 

I got a login page with the following error:

Failed to start x server (your graphical interface). It is likely that it is not set up correctly.
Would you like to view x server output to......

Fatal server error no screens found

---

### Post by Cypher on 2007-04-27
Most people suggest backing up your X configuration file with
```

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup

```
before making any changes. This way if you face the situation you have right now, you can always use just the text console to revert back to the back up file.

There maybe a way of re-creating a default configuration if you go through the text-console and try
```

sudo dpkg-reconfigure xorg-server

```

---

### Post by loell on 2007-04-27
there is no restore point yet in ubuntu, maybe in the distant future :)

it is always advisable to backup your configuration, especially the xorg.conf.

---

### Post by thingy on 2007-04-27
loell,
 
To recover the original /etc/X11/xorg.conf file as it was configured during installation of Ubuntu, type in:
 
```
 
sudo dpkg-reconfigure xserver-xorg

```
 
Make a copy of your exisiting first!

---

### Post by bitumen on 2007-06-28
same thing happened to me,
i stupidly configured to much of the xorg.conf file with out testing it,
after losing both monitors tried accessing Ubuntu with   rescue? or recover?  from the grub load screen and when it finally settled to a console screen i couldn't navigate anywhere, so i    
tried live cd again and couldn't edit any of the system files on the hard drive

so i reinstalled, re-edit the xorg.config and promptly forgot to load the graphic card drivers 
again it crashed, retried the before mentioned second option from the grub load screen, again unsuccessful
so ive now again reinstall and loaded the drivers and backup up the xorg.conf file 

so now what do i do if and when this happens again 

[HTML]sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup[/HTML]

this may help me to restore the graphic file but is there anyway of re-editing the hard disc system files from the live cd if so how dose one navigate using the terminal to the files hard drive

and if all else fails can you point to the imaging tutorial thanks  -> found that my windows imaging program works with Linux file system

---

