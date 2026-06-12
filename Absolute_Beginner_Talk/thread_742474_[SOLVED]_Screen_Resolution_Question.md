---
title: "[SOLVED] Screen Resolution Question"
date: 2008-04-01
forum: Absolute Beginner Talk
---

### Post by Samurai Penguin on 2008-04-01
I just built a box that has an nVidia GeForce3 500 agp card
I installed the restricted drivers and everything works ok
however, when I open Screen Resolution it shows a refresh rate
of 50Hz and I know for sure the monitor is refreshing at 85Hz.
Why don't the refresh rates match?

---

### Post by Matthewslf on 2008-04-01
What are the choices for refresh rate?
Also, after a fresh install mine just said Default Screen with 1024x768 at 60 hz. I think yours is just the default just the default. You've probably done this but in system -> administration ->screens and graphics, make sure your graphics card is selcted properly in the second tab, and i might recommend selecting your screen model. I warn you, though, when I did that, my default resolution was set to 800x600 and i had to reset it with gconf. In the end, your eye won't know the difference anyway.

---

### Post by alexforcefive on 2008-04-01
> **Samurai Penguin said:**
> I just built a box that has an nVidia GeForce3 500 agp card
I installed the restricted drivers and everything works ok
however, when I open Screen Resolution it shows a refresh rate
of 50Hz and I know for sure the monitor is refreshing at 85Hz.
Why don't the refresh rates match?

In my experience, none of that stuff works properly. Someone needs to make the "screen resolution" and "screens and graphics" apps just read from /etc/X11/xorg.conf, because that's the only way to reliably change your settings right now

---

### Post by forrestcupp on 2008-04-01
If you have a Geforce 3, you are probably using the legacy drivers, so you probably need to install the nvidia-settings package.  To find out, try typing
```
nvidia-settings
```
If it doesn't bring up a GUI for nvidia settings, then type
```
sudo apt-get install nvidia-settings
nvidia-settings
```
and try setting your resolution with that.

---

### Post by Samurai Penguin on 2008-04-01
> **forrestcupp said:**
> If you have a Geforce 3, you are probably using the legacy drivers, so you probably need to install the nvidia-settings package.  To find out, try typing
```
nvidia-settings
```
If it doesn't bring up a GUI for nvidia settings, then type
```
sudo apt-get install nvidia-settings
nvidia-settings
```
and try setting your resolution with that.

I used  nvidia-settings  and the GUI opened and I set the
refresh rate to 85Hz, closed the GUI and checked 
System > preferences > Screen Res and it shows 118Hz

when I check the rate using the monitor controls it still says 85Hz (which is what I want)

the choices I now see in Scren Res are  50, 56, 57, 118Hz

the GUI shows the following driver: NVIDIA 1.0-9639

after a reboot I opened the GUI and it shows the refresh rate set to auto,
It was set to 85Hz before I rebooted.
The GPU it shows id correct: GeForce3 Ti 500

---

### Post by forrestcupp on 2008-04-02
For nvidia cards, the nvidia-settings is much more accurate than Gnome's Screen Resolution settings.  Just make your changes with nvidia-settings and don't pay attention to the other.

---

