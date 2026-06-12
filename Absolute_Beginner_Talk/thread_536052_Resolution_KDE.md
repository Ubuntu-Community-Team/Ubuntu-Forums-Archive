---
title: "Resolution KDE"
date: 2007-08-27
forum: Absolute Beginner Talk
---

### Post by chrispche on 2007-08-27
How do you turn down the res in KDE? I can't seem to find it in the control centre. Is there a file I can edit?

Thanks.

When I use Gnome there is a simple GUI to change res.

---

### Post by stevebakerj on 2007-08-27
K Menu
System Settings
Monitor & Display

---

### Post by lukejmorrison on 2007-08-27
Steve, if you change your video card using the advanced monitor & display settings and then reboot and then you get a blank screen. Is there a way to get back to the default vid card setup?

---

### Post by chrispche on 2007-08-27
Whats the file you edit though?

---

### Post by stevebakerj on 2007-08-27
> **lukejmorrison said:**
> Steve, if you change your video card using the advanced monitor & display settings and then reboot and then you get a blank screen. Is there a way to get back to the default vid card setup?

The way I would do it is to boot from your Live CD and edit the "/etc/x11/xorg.conf" file.

Always worth remembering when you are going to play with your Video/Monitor settings is to always backup the xorg.conf file.

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
```

If you want to completely re-make your xorg.conf use

```
sudo dpkg-reconfigure xserver-xorg
```

and answer the questions as best as you can

---

### Post by chrispche on 2007-09-13
> **stevebakerj said:**
> K Menu
System Settings
Monitor & Display

The Monitor & Display is not there.

---

### Post by chrispche on 2007-09-13
> **stevebakerj said:**
> The way I would do it is to boot from your Live CD and edit the "/etc/x11/xorg.conf" file.

Always worth remembering when you are going to play with your Video/Monitor settings is to always backup the xorg.conf file.

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
```

If you want to completely re-make your xorg.conf use

```
sudo dpkg-reconfigure xserver-xorg
```

and answer the questions as best as you can

I did completely remake my xorg.conf file and f'ed up. How do I get .bak one back online?

---

### Post by taisao on 2007-09-13
with 
```
sudo cp /etc/X11/xorg.conf.bak /etc/X11/xorg.conf
```

---

### Post by chrispche on 2007-09-14
So where is The Monitor & Display in KDE?

---

### Post by taisao on 2007-09-14
I do see the screen & resolution settings.

Try kde control center -> kcontrol

---

### Post by chrispche on 2007-09-14
Nope not there. Is it because my monitor is old and KDE won't go down to 800X600? The refresh on 1024X768 is not good on my eyes.

---

### Post by chrispche on 2007-09-15
Maybe I didn't install something or something is missing.

---

### Post by chrispche on 2007-09-16
Anyone?

---

