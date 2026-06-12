---
title: "xorg.conf screws itself up"
date: 2006-12-05
forum: Absolute Beginner Talk
---

### Post by fatneck on 2006-12-05
Hi all - sometimes when i come back to my PC after a few hours and move the mouse to wake the screen, the xorg.conf has somehow defaulted to its original state. Being in a Windows frame of mind I usually just reboot it, but this doesn't fix it. So now I'm getting quite good at sudo gediting the file to add back in the screen resolutions I want.

Why does this happen? At the moment ALL I have on this install is Automatix which let me put the nVidia drivers on and a half assed attempt to get Quake III Arena on which has run into some directory permission problems.

Annoying is putting it mildly. I'll stop now before embarking on a fully fledged rant!

Cheers

---

### Post by fatneck on 2006-12-05
anyone...anyone...bueller...

---

### Post by pay on 2006-12-05
To change the permissions for quake3 try ```
sudo chmod 775 /path/to/quake3
```

---

### Post by bodhi.zazen on 2006-12-05
> **fatneck said:**
> Hi all - sometimes when i come back to my PC after a few hours and move the mouse to wake the screen, the xorg.conf has somehow defaulted to its original state. Being in a Windows frame of mind I usually just reboot it, but this doesn't fix it. So now I'm getting quite good at sudo gediting the file to add back in the screen resolutions I want.

Why does this happen? At the moment ALL I have on this install is Automatix which let me put the nVidia drivers on and a half assed attempt to get Quake III Arena on which has run into some directory permission problems.

Annoying is putting it mildly. I'll stop now before embarking on a fully fledged rant!

Cheers

Interesting problem. No I do not know why this is happening.

I can only offer an easier solution:

[list=number][*]First back up a working copy of xorg.xonf.```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
```
[*]To restore your xorg.conf:```
sudo cp /etc/X11/xorg.conf.bak /etc/X11/xorg.conf && sudo /etc/init.d/gdm restart
```
[*]You can script this:

> #! /bin/bash
cp /etc/X11/xorg.conf.bak /etc/X11/xorg.conf
/etc/init.d/gdm restart

Save this script into ~/bin, as restartX run it as root.

sudo ~/bin/restartX[/list]

---

### Post by xpod on 2006-12-05
>  xorg.conf screws itself up

Aint it US who make that happen:-k 

Most troubles i`ve encountered are usually traceable back to me
Good luck regardless

---

### Post by fatneck on 2006-12-05
Probably is something I did - just hard to trace as it was fine when I left it and messed up when I came back... :-)

Is a script something along the lines of a batch file in Windows? I'll give that a go - thanks.

---

