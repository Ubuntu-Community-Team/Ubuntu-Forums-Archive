---
title: "failed to star X server"
date: 2006-12-25
forum: Absolute Beginner Talk
---

### Post by s_x_g_t on 2006-12-25
When i boot i get a messy screen that says

" Failed to star the X server ( your graphical interface). It is likely that it is not set up correctly. Would you like to view the X server output to diagnose the problem?  yes or no"

---

### Post by slimdog360 on 2006-12-25
did you just try to install the nvidia drivers? Also did you make a backup of your xorg.conf file before it went bung?

dont worry, this sort of thing is usually pretty easy to fix.

---

### Post by NeoLithium on 2006-12-25
Well, you can reconfigure it like so, first, back up the config:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
```
Stop the X-server so the autodetection works better
```
sudo /etc/init.d/gdm stop (or kdm for KDE)
```
Reconfigure the server:
```
sudo dpkg-reconfigure xserver-xorg
```
and the restart Gnome or KDE:
```
sudo /etc/init.d/gdm start (again, KDM for KDE)
```

---

### Post by s_x_g_t on 2006-12-25
i click yes and get some information on what version i have then it says

Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting, (++) from command line, !! notice, (II) informatinal, (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: " /var/log/Xorg.0.log", Time: Mon Dec 25 2:29 2006
(==) Using config file: "/etc/X11/org.conf"
<ok>

---

### Post by s_x_g_t on 2006-12-25
> **NeoLithium said:**
> Well, you can reconfigure it like so, first, back up the config:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
```
Stop the X-server so the autodetection works better
```
sudo /etc/init.d/gdm stop (or kdm for KDE)
```
Reconfigure the server:
```
sudo dpkg-reconfigure xserver-xorg
```
and the restart Gnome or KDE:
```
sudo /etc/init.d/gdm start (again, KDM for KDE)
```



does this get typed into the blank black screen after hitting OK?

---

### Post by s_x_g_t on 2006-12-25
video card bus identifier?

---

### Post by NeoLithium on 2006-12-25
Vesa is the save mode decision I believe, that works for most video cards; as far as I'm aware (I'm currently using that driver, actually...)

---

### Post by s_x_g_t on 2006-12-25
> **NeoLithium said:**
> Vesa is the save mode decision I believe, that works for most video cards; as far as I'm aware (I'm currently using that driver, actually...)

I picked savage cause i have a S3 Prosavage 8   , see edited post.

---

### Post by s_x_g_t on 2006-12-25
god that was a mess, i had no idea what i was doing on that set up , bt everything is back to normal , only one load error "failed to load HAL"

---

### Post by s_x_g_t on 2006-12-25
Some screen savers wont load..  It asked me how much memory to give the grpahics cards and i guessed and said 10000 KB. If i make a new user account will all of the setting for it go back to default? then i can just deleted the 1st account.

whops NVM it says i dont have access to system configuration.

---

### Post by s_x_g_t on 2006-12-25
some screen savers not working , other then that everything seems ok, anything I can run to inspect?

---

### Post by DarkW0lf on 2006-12-26
I am having the same issue, except that I cannot log in as root and the sudo command is not accepting my password. I am trying to run the dpkg-reconfigure command to correct X.

The shell is slow to respond and I am not sure if the password is inputted correctly but I have no way of knowing.

I had considered using the Live CD to boot the system and edit the config file. But of course that won't work, it's read only and not the filesystem that's on my hard drive.

---

