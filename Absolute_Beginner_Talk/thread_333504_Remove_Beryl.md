---
title: "Remove Beryl"
date: 2007-01-07
forum: Absolute Beginner Talk
---

### Post by fasoulas on 2007-01-07
I installed beryl using this how-to :
[http://www.ubuntuforums.org/showthread.php?t=268036](http://www.ubuntuforums.org/showthread.php?t=268036)
I only follow the instructions of the last part of the how to (_**Install & Configure XGL and Beryl**_)

And now i want to completely remove it from my ubuntu.!

How can i do that?

---

### Post by fasoulas on 2007-01-07
if i put in the terminal :

```
[COLOR=#fe000a]sudo apt-get remove xserver-xgl libgl1-mesa xserver-xorg libglitz-glx1 beryl emerald emerald-themes[/COLOR]
```

Is that going to remove the things i installed???

---

### Post by jvc26 on 2007-01-07
If you installed those packages during the install, then the command you have put up there will remove them. You could also do a:
```

sudo apt-get --purge remove xserver-xgl libgl1-mesa xserver-xorg libglitz-glx1 beryl emerald emerald-themes

```
Which will totally remove them from your system (with config packages they also installed). This is not necessary really but if you want to totally remove them then thats the process.
Note:
```

sudo gedit /etc/X11/xorg.conf
sudo gedit /etc/gdm/gdm.conf-custom

```
Were both edited during the install - it may be worth putting them back to how they were as that could well cause some issues. Hope that helps
Il

---

### Post by fasoulas on 2007-01-07
> **Illuvator said:**
> If you installed those packages during the install, then the command you have put up there will remove them. You could also do a:
```

sudo apt-get --purge remove xserver-xgl libgl1-mesa xserver-xorg libglitz-glx1 beryl emerald emerald-themes

```Which will totally remove them from your system (with config packages they also installed). This is not necessary really but if you want to totally remove them then thats the process.
Note:
```

sudo gedit /etc/X11/xorg.conf
sudo gedit /etc/gdm/gdm.conf-custom

```Were both edited during the install - it may be worth putting them back to how they were as that could well cause some issues. Hope that helps
Il

thnx for the information .
i tried your command
```
sudo apt-get --purge remove xserver-xgl libgl1-mesa xserver-xorg libglitz-glx1 beryl emerald emerald-themes
```

but it seems that the file **/etc/gdm/gdm.conf-custom **doesn't exist maybe it was deleted with the other configuration files can u post me what that file has in it so i can make it back where it was?

---

### Post by fasoulas on 2007-01-08
Can anyone help me please. When i rebooted my pc the only thing that i can see is the command line and i can't access the ubuntu gui.I am writing this from my xp installation please help me.

I want from someone that is experienced enough to tell me what to do and how i can back up my **VERY IMPORTANT FILES **if i need to format

Please help

---

### Post by Efwis on 2007-01-08
here is my /etc/gdm/gdm.conf-custom file. Hope this helps.
to make this work type the following at the command line:
```
sudo nano /etc/gdm/gdm.conf-custom
```
since you won't be able to do copy and paste you will have to type it in. Providing you get a blank file. Otherwise just type the important parts, those are the ones without the # in front of them.
```
# GDM Configuration Customization file.
#
# This file is the appropriate place for specifying your customizations to the
# GDM configuration.   If you run gdmsetup, it will automatically edit this
# file for you and will cause the daemon and any running GDM GUI programs to
# automatically update with the new configuration.  Not all configuration
# options are supported by gdmsetup, so to modify some values it may be
# necessary to modify this file directly by hand.
#
# To hand-edit this file, simply add or modify the key=value combination in
# the appropriate section in the template below.  Refer to the comments in the
# gdm.conf file for information about each option.  Also refer to the reference
# documentation.
#
# If you hand edit a GDM configuration file, you should run the following
# command to get the GDM daemon to notice the change.  Any running GDM GUI
# programs will also be notified to update with the new configuration.
#
# gdmflexiserver --command="UPDATE_CONFIG <configuration key>"
#
# For example, the "Enable" key in the "[debug]" section would be specified by
# "debug/Enable".
#
# You can also run gdm-restart or gdm-safe-restart to cause GDM to restart and
# re-read the new configuration settings.  You can also restart GDM by sending
# a HUP or USR1 signal to the daemon.  HUP behaves like gdm-restart and causes
# any user session started by GDM to exit immediately while USR1 behaves like
# gdm-safe-restart and will wait until all users log out before restarting GDM.
#
# For full reference documentation see the gnome help browser under
# GNOME|System category.  You can also find the docs in HTML form on
# http://www.gnome.org/projects/gdm/
#
# NOTE: Lines that begin with "#" are considered comments.
#
# Have fun!

[daemon]

[security]

[xdmcp]

[gui]

[greeter]
Browser=true

[chooser]

[debug]

[servers]


``` save and exit.
Next you should make sure you have your original xorg.conf file from the initial installation type the following at the command line:
```
cd /etc/X11/
dir 
```
and look for this file ```
xorg.conf~
```
If it is there then do the following command:
```
sudo cp /etc/X11/xorg.conf~ /etc/X11/xorg.conf
```
This will copy the original xorg.conf file back to the status before you installed beryl.

then reboot your computer using
```
sudo reboot
```

I've never used beryl so I don't know what all it modifies or changes. good luck

---

### Post by fasoulas on 2007-01-08
Thnx **Efwis** i will try it and post back later to tell if it worked


That is what :

i putted in the command line to install beryl and its components :
```
sudo apt-get install xserver-xgl libgl1-mesa xserver-xorg libglitz-glx1 beryl emerald emerald-themes
```


And thats what i putted in order to uninstall it
```
sudo apt-get --purge remove xserver-xgl libgl1-mesa xserver-xorg libglitz-glx1 beryl emerald emerald-themes
```

and after that all happend 

Just to give some more info about what i deleted

---

### Post by Efwis on 2007-01-08
> **fasoulas said:**
> Thnx **Efwis** i will try it and post back later to tell if it worked


That is what :

i putted in the command line to install beryl and its components :
```
sudo apt-get install xserver-xgl libgl1-mesa xserver-xorg libglitz-glx1 beryl emerald emerald-themes
```


And thats what i putted in order to uninstall it
```
sudo apt-get --purge remove xserver-xgl libgl1-mesa xserver-xorg libglitz-glx1 beryl emerald emerald-themes
```

and after that all happend 

Just to give some more info about what i deleted
everything that you removed is associated strictly with beryl. You do need to do one more step that I forgot about though.

After you have repaired the two files, you should issue the following command before rebooting.

```
sudo aptitude install metacity
```
This will reinstall the metacity system so you can access Gnome

---

### Post by fasoulas on 2007-01-08
thnx i will try it

---

### Post by fasoulas on 2007-01-11
I have done what u said but it seemed that was not working because when i rebooted i was again in the terminal so i wrote the command ;

```
sudo startx
```

but it was saying something about that 
locking  /home/username/.Xauthority
no such file usr/bin/x 

or something like that and some other things above it

so i wrote

```
sudo aptitude install x-window-system-core
```

after that i tried again the command 

```
sudo startx
```

and it was saying that there is no screen and no drivers for my nvidia 6600

what is the problem?

---

