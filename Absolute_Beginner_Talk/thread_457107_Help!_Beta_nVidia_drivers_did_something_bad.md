---
title: "Help! Beta nVidia drivers did something bad"
date: 2007-05-28
forum: Absolute Beginner Talk
---

### Post by Hobo Joe on 2007-05-28
Ok, I installed the beta nVidia drivers, and everything seemed to be working fine, but when I rebooted, it said that X failed to start.
So I reconfigured xserver, and it started up fine, then I ran 'sudo nvidia-settings' to get my display set up properly again, but it said the nvidia drivers weren't running and I needed to run 'sudo nvidia-xconfig' to get it working again.

So I did that, then rebooted, and it failed to start X. Again.

But I remember when I was installing the drivers, it said that it had saved a backup, but I don't know how to get it back. So if someone could tell me how to get my backup, that would be great.
Or would it be fine if I just uninstalled my drivers with Envy and then installed the normal ones, would that work? I'm not sure if Envy can uninstall the beta drivers.

---

### Post by Hobo Joe on 2007-05-28
Ok, I think I'm overcomplicating this, if someone could just tell me how to uninstall the beta drivers, that would be awesome.

Then I can just install the normal ones again with Envy.

---

### Post by taurus on 2007-05-28
Can you log into a console with your username and password?  If you can, post the output of this command here to see which one is your backup version xorg.conf.

```
ls -la /etc/X11
```
Otherwise, reconfigure X again with

```
sudo dpkg-reconfigure xserver-xorg
startx
```

---

### Post by Hobo Joe on 2007-05-28
I already reconfigured Xserver, and it's running right now, but the thing is, when I try to run nvidia-settings, it says that it's not running becuase Xserver isn't configured right, but when I use nvidia's configure script, X won't start up.

So when I'm running the reconfigured xserver, that command says:
```

total 124
drwxr-xr-x  10 root root  4096 2007-05-28 11:23 .
drwxr-xr-x 122 root root 12288 2007-05-28 11:08 ..
drwxr-xr-x   2 root root  4096 2007-05-13 16:15 app-defaults
drwxr-xr-x   2 root root  4096 2007-05-13 16:15 cursors
-rw-r--r--   1 root root    14 2007-05-14 21:28 default-display-manager
drwxr-xr-x   7 root root  4096 2007-05-25 12:31 fonts
lrwxrwxrwx   1 root root     6 2007-05-14 21:28 gdm -> ../gdm
-rw-r--r--   1 root root 17371 2007-02-13 04:02 rgb.txt
lrwxrwxrwx   1 root root    13 2007-05-13 16:07 X -> /usr/bin/Xorg
drwxr-xr-x   3 root root  4096 2007-05-13 16:13 xinit
drwxr-xr-x   2 root root  4096 2007-05-13 16:06 xkb
-rw-r--r--   1 root root  3416 2007-05-28 11:23 xorg.conf
-rw-r--r--   1 root root  2191 2007-05-28 11:05 xorg.conf.20070528110500
-rw-r--r--   1 root root  4265 2007-05-28 11:08 xorg.conf.20070528110840
-rw-r--r--   1 root root  3388 2007-05-28 11:22 xorg.conf.20070528112205
-rw-r--r--   1 root root  3386 2007-05-28 11:23 xorg.conf.20070528112341
-rw-r--r--   1 root root  3416 2007-05-28 11:05 xorg.conf.backup
-rw-r--r--   1 root root  3398 2007-05-13 21:45 xorg.conf_backup_200705132145
-rw-r--r--   1 root root  1988 2007-05-13 22:04 xorg.conf.backup.beryl-script
drwxr-xr-x   2 root root  4096 2007-05-13 16:06 Xresources
drwxr-xr-x   2 root root  4096 2007-05-13 16:07 xserver
-rwxr-xr-x   1 root root  3911 2006-08-07 14:01 Xsession
drwxr-xr-x   2 root root  4096 2007-05-25 10:41 Xsession.d
-rw-r--r--   1 root root   234 2006-08-07 14:01 Xsession.options
-rw-r--r--   1 root root    13 2006-09-11 22:44 XvMCConfig
-rw-------   1 root root   614 2007-05-13 16:06 Xwrapper.config

```

(sorry if I'm making this really confusing.)
All I really want to know is how I can uninstall the beta drivers.

---

### Post by taurus on 2007-05-28
Didn't we just went though how to shutdown X first before you can install nVidia beta driver not that long ago?

<Ctrl><Alt>F2
```
sudo /etc/init.d/gdm stop
```

---

### Post by Hobo Joe on 2007-05-28
> **taurus said:**
> Didn't we just went though how to shutdown X first before you can install nVidia beta driver not that long ago?

<Ctrl><Alt>F2
```
sudo /etc/init.d/gdm stop
```

Yes. :redface:

And that all worked fine, and the install worked fine to, but apparently my comp didn't like how nVidia configured xorg.conf.

I'm just wondering if there is a command similar to this:
```

sudo aptitude purge

```
So that I can uninstall the drivers.

---

