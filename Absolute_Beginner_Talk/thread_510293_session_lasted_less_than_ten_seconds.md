---
title: "session lasted less than ten seconds"
date: 2007-07-26
forum: Absolute Beginner Talk
---

### Post by scorziello on 2007-07-26
I am having problems logging in I can log in under failsafe and I can also create a new user, but I want to be able to use the original user account because of the large amount of data stored in the home folder i.e. music. I have already read and tried everything else I could find. This had happened a few days ago when i installed compiz fusion, so I uninstalled it and everything was ok. I reinstalled compiz and everything was working fine, then when I changed some of the settings in compiz it gave me this error the next time I logged in. I have already removed compiz again. Here is the error I am getting:

/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp 
/etc/gdm/PreSession/Default: running: /usr/X11R6/bin/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "enzo" 
/etc/gdm/Xsession: Beginning session setup... 
SESSION_MANAGER=local/enzo-laptop:/tmp/.ICE-unix/5489 
Starting gdesklets-daemon... 

Connecting to daemon [###          ]Initializing gnome-mount extension 
Window manager warning: "" found in configuration database is not a valid value for keybinding "toggle_shaded" 

Connecting to daemon [ ###         ] 
Connecting to daemon [  ###        ] 
(gnome-cups-icon:5563): GnomeUI-WARNING **: While connecting to session manager: 
IO error occured opening connection. 

(gnome-power-manager:5559): GnomeUI-WARNING **: While connecting to session manager: 
IO error occured opening connection. 

(evince:5569): GnomeUI-WARNING **: While connecting to session manager: 
IO error occured opening connection. 

Connecting to daemon [   ###       ] 
(update-notifier:5558): GnomeUI-WARNING **: While connecting to session manager: 
IO error occured opening connection.

---

### Post by cek on 2007-07-26
From your failsafe terminal, try typing sudo startx

If X doesn't start, then post the output of the command here (optionally you can post the /var/logs/XOrg.log file).

---

### Post by scorziello on 2007-07-26
I typed in sudo startx and this is what i get

Fatal Server error:server is already active for display 0. If this server is no longer running, remove /tmp/.X0-lock and start again.

---

### Post by aysiu on 2007-07-26
Your original error message means you've either accidentally changed ownership of the ~/.ICEauthority file, or you're out of disk space.

More details in these threads (including solutions):
[session lasted less than 10 seconds](http://ubuntuforums.org/showthread.php?t=278222)
[ your session lasted less than 10 seconds](http://ubuntuforums.org/showthread.php?t=97540)

---

### Post by scorziello on 2007-07-26
i have plenty of disk space i think. the system tells me i have 80 gig free but i don't know how to check that for sure. and i cant find this .ICEauthority file. even when I enable show hidden files it does not show up.

---

### Post by aysiu on 2007-07-26
From the command line, can you type ```
sudo updatedb
``` (this may take a few minutes) and then ```
locate ICEauthority
``` ? That should tell you if you have an ICEauthority and where it is. If all goes well, it should say ```
/home/username/.ICEauthority
``` If not, post back the result here.

---

### Post by scorziello on 2007-07-26
Yes that is what it says. But what to do with it when I find it.

---

### Post by aysiu on 2007-07-26
```
sudo chown *username:username* /home/*username*/.ICEauthority
``` and see if that allows you to log in.

---

### Post by scorziello on 2007-07-26
The command line gives the error that there is no such file or directory.

---

### Post by aysiu on 2007-07-26
That's weird. So ```
locate ICEauthority
``` pops up ```
/home/username/.ICEauthority
``` but ```
sudo chown username:username /home/username/.ICEauthority
``` turns up ```
no such file or directory
```? I'm not sure what to do, then.

---

### Post by scorziello on 2007-07-26
Sorry typo on my part. I enter it as displayed and i get the same error as before when I try to login. If there is a way I can move the files from one user to the other I will do that, and just delete the original username. I just don't want to be unable to access about twenty gig of music.

I got something to work. I was able to move the files I didn't want to lose and I made a new ID. I just have to rebuild my settings.

---

