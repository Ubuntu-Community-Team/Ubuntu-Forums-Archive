---
title: "lost my 1680x1050 resolution"
date: 2008-02-14
forum: Absolute Beginner Talk
---

### Post by ptviperz on 2008-02-14
so I'm trying to setup my HTPC and enabled the second monitor. I was trying to get it configured correctly, had to reboot and now I can't set my main monitor higher than 1600x1024....looks terrible. It was @ 1680x1050 and looked beautiful.

I tried to reset it using nvidia-settings like I did before but 1680x1050 isn't listed as an option. Anyone know how I screwed it up or how to fix it?

---

### Post by ptviperz on 2008-02-14
forgot to mention 7950GT video card and 226BW Syncmaster

---

### Post by OffAxis on 2008-02-14
have you tried
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by djbsteart1 on 2008-02-14
have you tried to reconfigure the xserver and tell it to use that resolution you want. here is the code but make sure you make a backup first, so that if something goes wrong you can still have something to look at. 

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
```to make a backup

```
sudo dpkg-reconfigure xserver-xorg
```to open the config

---

### Post by ptviperz on 2008-02-14
OMG, there was a 'widescreen' box that got unchecked. Checked it (admin->screens+graphics), then was able to select 1680x1050, still didn't look right, then had to switch it to 1680x1050 in Preferences->resolutions too.

Shouldn't I only have to change it in one spot? That's flat out weird. Hrm, back to trying for HTPC now.....LOL

Thanks guys, I asked for help to soon on this one...

---

### Post by djbsteart1 on 2008-02-14
no worries, glad its working. good luck with htpc

---

