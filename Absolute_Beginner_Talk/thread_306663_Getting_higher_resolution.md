---
title: "Getting higher resolution"
date: 2006-11-25
forum: Absolute Beginner Talk
---

### Post by RideP2 on 2006-11-25
Hi, right now my resolution is at 1024 x 768. On the slider or menu drop down to change the resolution, it's the max according to that, but I was able to get higher resolutions in Windows XP. Is there a way to change some config file to let me go higher? 

Thx

---

### Post by bodhi.zazen on 2006-11-25
> **RideP2 said:**
> Hi, right now my resolution is at 1024 x 768. On the slider or menu drop down to change the resolution, it's the max according to that, but I was able to get higher resolutions in Windows XP. Is there a way to change some config file to let me go higher? 

Thx

Try starting with this,
Open a terminal and type:

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by RideP2 on 2006-11-25
I got this message.

xserver-xorg postinst warning: overwriting possibly-customised configuration
   file; backup in /etc/X11/xorg.conf.20061125105527

---

### Post by bodhi.zazen on 2006-11-25
> **RideP2 said:**
> I got this message.

xserver-xorg postinst warning: overwriting possibly-customised configuration
   file; backup in /etc/X11/xorg.conf.20061125105527

LOL :lol: Sorry, that is normal. It saved a backup is all.

now re-start X (log out or Ctrl-Alt-Backspace).

---

### Post by RideP2 on 2006-11-25
Ok, did that. (hope it dosent matter that i'm in KDE right now, just expirementing with it.)

---

### Post by bodhi.zazen on 2006-11-25
You can also try [This thread](http://ubuntuforums.org/showthread.php?t=251917)

---

### Post by bodhi.zazen on 2006-11-25
> **RideP2 said:**
> Ok, did that. (hope it dosent matter that i'm in KDE right now, just expirementing with it.)

Is it working ? Can you select a higher resolution ?

---

### Post by RideP2 on 2006-11-25
Nope, it's still saying that it's at the max reso.

---

### Post by RideP2 on 2006-11-25
Oh my refresh rate is ok, it's at 85. It was 75 in windows but its not having any problems so i'm not gonna play with that.

---

### Post by RideP2 on 2006-11-25
Hello?

---

### Post by drphilngood on 2006-11-25
Try this guide:

[HOWTO: change resolution/refresh rate in Xorg]("http://ubuntuforums.org/showthread.php?t=83973")

---

### Post by bodhi.zazen on 2006-11-25
> **RideP2 said:**
> Hello?

Videocard ? Monitor ?

Also look at this thread: [Monitor resolution](http://ubuntuforums.org/showthread.php?t=269052)

---

### Post by lazyfirecloud on 2007-04-05
Ubuntu has all the information you need:
[https://help.ubuntu.com/community/DebuggingXAutoconfiguration](https://help.ubuntu.com/community/DebuggingXAutoconfiguration)
I personally just had to change the refresh rate

---

### Post by Jean Of mArc on 2007-05-08
After using the X auto-detection, that is, moving the xorg,conf file altogether and letting X do the work of auto-detecting on the way in, is there a way to see/edit the auto-detected file? I find that the auto-detection does a good job with my monitor, but I would like to edit some stuff involving the mouse, but I'm not sure where or how to do that.

Thanks!

Jean Of mArc

---

### Post by bodhi.zazen on 2007-05-08
> **Jean Of mArc said:**
> After using the X auto-detection, that is, moving the xorg,conf file altogether and letting X do the work of auto-detecting on the way in, is there a way to see/edit the auto-detected file? I find that the auto-detection does a good job with my monitor, but I would like to edit some stuff involving the mouse, but I'm not sure where or how to do that.

Thanks!

Jean Of mArc

Yes. The file to edit is /etc/X11/xorg.conf

You can edit it with : ```
gksudo gedit /etc/X11/xorg.conf
```

Or you may use vim or nano if you are outside of X : ```
sudo nano -B /ect/X11/xorg.conf
```

the -B flag with nano makes a back-up at /etc/X11/xorg.conf~

---

### Post by Jean Of mArc on 2007-05-08
Well, what I'm saying is that there is no /etc/X11/xorg.conf , as I would expect there to be, when I do the X autodetection... as provided in the tutorial in the link above... that's what confuses me, because I'm not sure where the settings are then saved...

---

