---
title: "help wanted :0"
date: 2006-01-12
forum: Absolute Beginner Talk
---

### Post by solstis on 2006-01-12
first i want to apologize if there's already a similar thread and that i'm not giving exact quotes of the system messages
now about the problem:

a few hours ago i tried to run ubuntu 5.10 from a live cd but it couldn't load the x-server (it said that it wasn't properly set up) so i tried some help channels in irc. one guy told me to type 'xfree86config' or 'xf86config' but that was an unknown command according to the system (i understood that this was supposed to run the configuration for the x). another guy told me to type 'sudo apt-get update' and then 'sudo apt-get install x-server-window' . it did update something but it couldn't find that package ( 'x-server-window' i suppose )
so.. any ideas on how to fix the problem?

i haven't worked with any kind of os except for windows, so please be patient and don't hold back the explanations ;) 

thanks in advance

---

### Post by Gustav on 2006-01-12
try this:
```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by solstis on 2006-01-12
it starts to configure the xserver, but on the question about the color quality (the bits) it brings out this below the configuration:
xserver-xorg postins warning : overwritting possibly-customized configuration file; backup in etc/x11/xorg.conf.200601121720

---

### Post by solstis on 2006-01-12
it starts to configure the xserver, but on the question about the color quality (the bits) it brings out this below the configuration:
xserver-xorg postins warning : overwritting possibly-customized configuration file; backup in etc/x11/xorg.conf.200601121720

---

### Post by lolcese on 2006-01-12
Which video card do you have? I had the same problem with a Ati 200M. After install Ubuntu I got the same message, but I installed the drivers and everything is running fine now.

---

### Post by blair on 2006-01-12
All the X warning is saying is that the default X config file has been modified due to changes made during auto-hardware detect. Your update process is just pointing out that it is about to over write the original X config file and so it created a backup file for you. Nothing to worry about.

With regards to editing the file settings, try either of the following:

Try this tool: /usr/X11R6/bin/xorgcfg

Alternatively try this: 

1.	Log in as root so you are able to access X configuration files.
2.	Make a backup copy of your /etc/X11/xorg.conf file, e.g.:
a.	cp /etc/X11/xorg.conf /etc/X11/xorg.conf.original
3.	Shutdown your window manager process (the process is running even if the desktop is not being displayed), e.g. GDM, so it does not interfere with the hardware auto-detect process: /etc/init.d/gdm stop
4.	Launch the graphical xorg.conf editor: dpkg-reconfigure xserver-xorg.
5.	When the editor application runs, select auto-hardware detect.
6.	If you do not see your video chipset listed, simply select VESA.
7.	Work through options and make best-guess selections. 
8.	Save all settings and exit
9.	Enter the startx command to load the window manager and the GUI.

---

### Post by blair on 2006-01-12
All the X warning is saying is that the default X config file has been modified due to changes made during auto-hardware detect. Your update process is just pointing out that it is about to over write the original X config file and so it created a backup file for you. Nothing to worry about.

With regards to editing the file settings, try either of the following:

Try this tool: /usr/X11R6/bin/xorgcfg

Alternatively try this: 

1.	Log in as root so you are able to access X configuration files.
2.	Make a backup copy of your /etc/X11/xorg.conf file, e.g.:
a.	cp /etc/X11/xorg.conf /etc/X11/xorg.conf.original
3.	Shutdown your window manager process (the process is running even if the desktop is not being displayed), e.g. GDM, so it does not interfere with the hardware auto-detect process: /etc/init.d/gdm stop
4.	Launch the graphical xorg.conf editor: dpkg-reconfigure xserver-xorg.
5.	When the editor application runs, select auto-hardware detect.
6.	If you do not see your video chipset listed, simply select VESA.
7.	Work through options and make best-guess selections. 
8.	Save all settings and exit
9.	Enter the startx command to load the window manager and the GUI.

---

