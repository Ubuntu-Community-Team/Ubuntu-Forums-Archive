---
title: "Transmission BitTorrent Client very unstable"
date: 2008-11-28
forum: Apple Hardware Users
---

### Post by giannimaria on 2008-11-28
My computer is an iMac powerpc G4 (the first iMac to have been marketed with a flat panel) with 768MB RAM which has been smoothly running Ubuntu for quite a while now. The only problem, I cannot adjust the screen brightness.

A fresh install of 8.10 from the alternate CD failed due to the CDROM drive detection issue now worked around in the forum, so I upgraded. Things go well, except for Transmission which keeps crashing almost every time I double click items in the download list.

Can anyone help, please.

---

### Post by stream303 on 2008-11-28
> **giannimaria said:**
> The only problem, I cannot adjust the screen brightness.

While I can't help on the transmission problem, you can fake the lack of brightness using *xgamma* or using different themes, such as DarkRoom.

Since using xgamma changes your gamma, I wouldn't do any critical photo editing with the system, but it might do in a pinch.  Dirk and I have talked about this a while back  (anyone know what's up with Dirk?)

[http://ubuntuforums.org/showthread.php?t=710026&highlight=xgamma](http://ubuntuforums.org/showthread.php?t=710026&highlight=xgamma)

Basically, it is as simple as this in a terminal:

To darken
```
xgamma -gamma 0.6
```

To lighten
```
xgamma -gamma 1.4
```

Get back to default (1.0)
```
xgamma -gamma 1.0
```

The usable range for me is from about 0.5 to 1.5

If you find a value you like, you can make it permanent by putting it into your /etc/X11/xorg.conf and logout/login, or reboot as shown in the link.

Since my screen is just a little bit bright, I switched to the DarkRoom theme, and made sure that backgrounds weren't solid white, but light-gray.  This really helped, except for the background of Firefox, since they do their own thing when it comes to background levels.  So here is where xgamma might prove useful.

Note: that link also has a very useful calculator for determining the right font DPI if you have a large screen - at least as a starting point.

---

### Post by giannimaria on 2008-11-28
thanks anyway

---

### Post by mkvnmtr on 2008-11-29
On my last reinstall of 8.04 I installed the KDE desktop also. It included KTorrent and made it the default. I had no idea so when I went to download I was using Ktorrent. I like it and never liked Transmission. Maybe you could try another client.

---

