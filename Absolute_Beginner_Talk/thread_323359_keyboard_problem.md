---
title: "keyboard problem"
date: 2006-12-22
forum: Absolute Beginner Talk
---

### Post by Jorge32 on 2006-12-22
Since I've changed my configuration on the xserver-xorg to have a better resolution I can not configure the alt keys. If I try using them it just don't happen anything, and when I try configuring it a message like this appears: 
Error activating XKB configuration.
It can happen under various circumstances:
- a bug in libxklavier library
- a bug in X server (xkbcomp, xmodmap utilities)
- X server with incompatible libxkbfile implementation

X server version data:
The X.Org Foundation
70101000

If you report this situation as a bug, please include:
- The result of xprop -root | grep XKB
- The result of gconftool-2 -R /desktop/gnome/peripherals/keyboard/kbd

And by the way I have a genius luxemate, slimastar series with a lot of media keys, do you know how can I configure it? or do I need to search for drivers or something like that?:confused:

---

### Post by KLineD on 2006-12-22
I have the exact same problem, look at [here]("http://www.ubuntuforums.org/showthread.php?t=323327"). What I did is to look at a xorg.conf backup to compare differences in the Device "InputDevice" section and restarted the X server. However I cant get rid of the error message yet.

To configure your media keys look at System > Preferences >Keyboard Shortcuts

---

### Post by Jorge32 on 2006-12-22
Sorry but I can't understand, I can run the locate xorg.conf and a bunch of coommands or specifcitations appear, but I can't run /etc/X11/xorg.conf, either I try it that way, or with sudo.
](*,)

---

### Post by KLineD on 2006-12-22
I'm sorry I'll try to be more specific. In order to solve your problem, I suggested you look at a backup of your xorg.conf config file. In order to locate such backup you must run:
```
sudo updatedb
locate xorg.conf
```

And as you saw, a bunch of locations appear. In my machine the results are:
> cesar@frodo:~$ locate xorg.conf
/var/lib/dpkg/info/xserver-xorg.config
/var/lib/x11/xorg.conf.md5sum
/var/lib/x11/xorg.conf.roster
/etc/X11/xorg.conf
/etc/X11/xorg.conf.original-0
/etc/X11/xorg.conf.20061220222536
/etc/X11/xorg.conf_bkp
/etc/X11/xorg.conf~
/etc/X11/xorg.conf.20061220231634
/etc/X11/xorg.conf.fglrx-0
/usr/share/gnome/help/desktopguide/sample/xorg.conf_disablectrlaltbackspacegnome
/usr/share/gnome/help/desktopguide/sample/xorg.conf_disablenvidialogo
/usr/share/man/man5/xorg.conf.5x.gz
/usr/share/xresprobe/xorg.conf


But it will be different for your machine. If you look closely, you'll see that several files named xorg.conf exists in /etc/X11/ such as xorg.conf (the actual file), xorg.conf.original-0 and so on. All of those files are backups of the same file, after it was modified by some program. So what you can do is open one of those backup files (I'll go with /etc/X11/xorg.conf_bkp):

```
sudo gedit /etc/X11/xorg.conf_bkp
```

And copy the part where it says something like: 
> Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc104"
	Option		"XkbLayout"	"latam"
EndSection

And paste it elsewhere so you can remember it. Now close that backup file, and open the actual xorg.conf file:
```
sudo gedit /etc/X11/xorg.conf
```

And locate the same part. It's likely to be slightly modified and that's whats causing your keyboard to malfunction. Paste what you copied from the backup file, save the file and close it. Now restart X server (or the whole system if that's easier) and you should be good to go.

If you have any more questions, feel free to ask. Se habla español!

---

### Post by Jorge32 on 2006-12-22
Muchas gracias! that solved the problem. I just changed the "kbd" for "keyboard". Even the message dissapeared. 
De verdad muchas gracias y disculpa las molestias!

---

### Post by KLineD on 2006-12-22
No hay problema para eso estamos.

No problem that's what we are here for.

---

