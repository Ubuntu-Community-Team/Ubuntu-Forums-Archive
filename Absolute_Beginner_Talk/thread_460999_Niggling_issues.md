---
title: "Niggling issues"
date: 2007-06-01
forum: Absolute Beginner Talk
---

### Post by deuchar1 on 2007-06-01
Hey guys,

I'm having an irritating issue that I can't seem to fix - hopefully you might be able to shed some light on it for me.

Firstly, since upgrading to Feisty I have a problem on system load. When Ubuntu loads all the Windows I open are missing their top bar (the one with the minimize/close buttons) - and my desktop icons are shunted off the top of the screen slightly. The fix for it seems to be opening the new Desktop Effects panel, enabling them, then disabling them again. Is there a better, permanent fix for this?

Thanks in advance.

Oh yeah before I forget - XMMS appears twice in my right-click menu (the one that comes up when I right-click a file). Any way of removing a duplicate entry?

---

### Post by Mazza558 on 2007-06-01
> **deuchar1 said:**
> Hey guys,

I'm having an irritating issue that I can't seem to fix - hopefully you might be able to shed some light on it for me.

Firstly, since upgrading to Feisty I have a problem on system load. When Ubuntu loads all the Windows I open are missing their top bar (the one with the minimize/close buttons) - and my desktop icons are shunted off the top of the screen slightly. The fix for it seems to be opening the new Desktop Effects panel, enabling them, then disabling them again. Is there a better, permanent fix for this?

Thanks in advance.

Oh yeah before I forget - XMMS appears twice in my right-click menu (the one that comes up when I right-click a file). Any way of removing a duplicate entry?

Try this:

> sudo gedit etc/X11/xorg.conf

Then find the "device" section, and add a new line with this:

> Option "AddARGBGLXVisuals" "True"

So it'll look something like this:

> Section "Device"
Identifier "(anything)"
Driver "(anything)"
Option "AddARGBGLXVisuals" "True"
EndSection

Save this and then press CTRL + ALT + Backspace.

Log in again, and you should be good to go.

---

### Post by deuchar1 on 2007-06-01
Okay I'll try that.
One thing - how is it I backup and then restore from backup the xorg.conf file in the command line? Every time I make changes to that file I bugger it up :)

---

### Post by jd65pl on 2007-06-01
**To backup the file**
cp /etc/X11/xorg.conf /etc/X11/xorg.conf.myBackUp

[B]To restore the backup
[/B]cp /etc/X11/xorg.conf.myBackUp /etc/X11/xorg.conf

See [this]("http://jamie.dumbill.googlepages.com/ubuntucommands2") for more commands

---

### Post by dreadlord_chris on 2007-06-01
> **jd65pl said:**
> **To backup the file**
cp /etc/X11/xorg.conf /etc/X11/xorg.conf.myBackUp

[B]To restore the backup
[/B]cp /etc/X11/xorg.conf.myBackUp /etc/X11/xorg.conf

See [this]("http://jamie.dumbill.googlepages.com/ubuntucommands2") for more commands

Those commands both need to be sudo'd to work. Also, to restore, it will first be necessary to remove the the old xorg.conf:
```

sudo rm /etc/X11/xorg.conf
sudo mv /etc/X11/xorg.conf.myBackUp /etc/X11/xorg.conf

```

---

### Post by deuchar1 on 2007-06-01
Cool, thanks guys!

---

### Post by Cypher on 2007-06-01
> **dreadlord_chris said:**
> Those commands both need to be sudo'd to work. Also, to restore, it will first be necessary to remove the the old xorg.conf:
```

sudo rm /etc/X11/xorg.conf
sudo mv /etc/X11/xorg.conf.myBackUp /etc/X11/xorg.conf

```
SUDO indeed needs to be added to those commands, but you do not need to remove the original file if you're going to use "mv". It will overwrite as long as the "rwx" permissions are set..

---

