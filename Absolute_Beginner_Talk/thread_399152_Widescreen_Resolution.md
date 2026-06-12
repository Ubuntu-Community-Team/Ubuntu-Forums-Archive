---
title: "Widescreen Resolution"
date: 2007-04-01
forum: Absolute Beginner Talk
---

### Post by Wotching on 2007-04-01
How can I change the resolution in Ubuntu to 1280x768?  It's at 1024x768 right now, and in the Resolution controls there doesn't seem to be an option for my widescreen setup.

---

### Post by lamalex on 2007-04-01
the easiest (but potentially dangerous) is just to edit xorg.conf.
```
sudo gedit /etc/X11/xorg.conf
``` and replace all of the resolutions with just your desired one. That should force into your resolution.

---

### Post by alien21010 on 2007-04-01
You need to run sudo dpkg-reconfigure -phigh xserver-xorg .  And select the graphics driver and then the resolutions that you want to use.  You'll have to reboot in order to see the selections in the Resolution controls.

That should fix it.

---

### Post by lamalex on 2007-04-02
> **alien21010 said:**
> You need to run sudo dpkg-reconfigure -phigh xserver-xorg .  And select the graphics driver and then the resolutions that you want to use.  You'll have to reboot in order to see the selections in the Resolution controls.

That should fix it.

this often doesn't work for widescreen resolutions. Not once has this ever worked for my on my 1200x800 laptop monitor, I always need to edit xorg.conf by hand.

---

### Post by Wotching on 2007-04-02
Alien21010's suggestion actually worked.

Thanks guys.

---

