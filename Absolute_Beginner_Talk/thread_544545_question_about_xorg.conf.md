---
title: "question about xorg.conf"
date: 2007-09-06
forum: Absolute Beginner Talk
---

### Post by Hagar55 on 2007-09-06
I followed the guide to make the side buttons on my mouse functional by changing the xorg.conf file.

This went without a hitch....knock on wood again...

Can I find xorg.conf as a file in nautilus ?
and I made a backup before starting (as described in the guide), does the backup stay in the system ?
If I make another backup, will it overwrite or make another one ?

---

### Post by mikewhatever on 2007-09-06
You can either navigate to /etc/X11 with Nautilus or use the following command to list the content of that location
> ls /etc/X11
If you make another backup named exactly the same and in the same directory, yes it would.
Here is the content of mine /etc/X11. The backups are highlighted.
> ls /etc/X11
app-defaults             rgb.txt    xorg.conf~                xserver
cursors                  X          [COLOR="Orange"]xorg.conf_backup15072007[/COLOR]  Xsession
default-display-manager  xinit      [COLOR="Orange"]xorg.conf_nvidia[/COLOR]          Xsession.d
fonts                    xkb        [COLOR="Orange"]xorg.conf_original[/COLOR]        Xsession.options
gdm                      xorg.conf  Xresources                Xwrapper.config


---

### Post by WebSiteGuru on 2007-09-06
for backup.

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
```

This will copy your xorg.conf to xorg.conf.backup. You can also change the extention to xorg.conf.backup1/2/3 etc... to save it to a different file name.

---

### Post by wolfen69 on 2007-09-06
```
gksudo nautilus
```
then just navigate to /etc/x11/xorg.conf

My 1000th post! yay!

---

### Post by Hagar55 on 2007-09-07
Thanks all.

---

