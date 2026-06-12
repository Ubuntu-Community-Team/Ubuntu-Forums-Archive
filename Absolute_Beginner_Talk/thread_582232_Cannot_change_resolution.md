---
title: "Cannot change resolution"
date: 2007-10-19
forum: Absolute Beginner Talk
---

### Post by mongee on 2007-10-19
Hi,

I have just updated from 7.04 to 7.10, my resolutions were all handled correctly on 7.04 (I was running 1280x1024). However now that I have updated to 7.10 I get a GUI message saying that it cannot detect my screen size and requests me to set it, so I select the monitor (Phillips 190B) and then select my video card (nVidia Geforce 2) and select 1024x768 (as this is the only one that I can read anything with when I hit "test"), when I click OK, it boots into Ubuntu, then loads as a generic video card set on 800x600 and I can only select that screen size if I try to change.

Then when I reboot, it s back into the window saying it cannot detect my video card when I restart. It's baffling because 7.04 used to detect it without me having to do anything (plus it would actually run at 1280x1024).

---

### Post by zagieman on 2007-10-19
I'm having the same problem. On 7.04 I ran dual monitors on my ATI 9600xt and now it won even let me set the resolution for one monitor. When i reconfigure and save, it just reverts back to the 800x600 after rebooting.

---

### Post by Qwerty_ on 2007-10-19
Have you installed the restricted drivers for your graphics card?

System>Administration>Restricted Drivers Manager.

---

### Post by Wiebelhaus on 2007-10-19
Crtl+Alt+F2 to drop to console ,

Run:

```
sudo dkpg-reconfigure xserver-xorg 
```

Manually choose your configuration , read carefully , three finger salute to restart.

---

### Post by zagieman on 2007-10-19
> **Qwerty_ said:**
> Have you installed the restricted drivers for your graphics card?

System>Administration>Restricted Drivers Manager.

Yes I have.

> **sx66gns said:**
> Crtl+Alt+F2 to drop to console ,

Run:

```
sudo dkpg-reconfigure xserver-xorg 
```

Manually choose your configuration , read carefully , three finger salute to restart.

This was the first thing I tried but it just reverted back to the normal settings when i rebooted.

---

### Post by zagieman on 2007-10-19
Now it wont even let me keep my old xorg.conf file. 

Every time I change a setting and test it inside "Screens and Graphics" it either does nothing or crashes and closes and when I open it up again it hasn't changed. I cant change the drivers using this either because it just changes itself back to "vesa".

I have simplified it to just one monitor now and can't even change the monitor model without it crashing.

---

### Post by javeer on 2007-10-20
i have the same problem...

anybody can help us?

thanks

---

### Post by badguyanil on 2007-10-20
read thru the post belpw completely with one link in the post... this will surely help!

[http://ubuntuforums.org/showthread.php?t=581322](http://ubuntuforums.org/showthread.php?t=581322)

---

### Post by boubou on 2007-11-09
Hello,

Just installing Ubuntu 7.10 on a laptop Acer Aspire 9420 with a nVidia GeForce 7300 and encoutner the same problem: settings set via Gnome GUI or by reconfiguring xserver were lost at next reboot.

Nevertheless I found a workaround and don't ask me the logic behind it.

At boot time when I got the warning screen telling your graphic card cannot be detected, I enabled the checkbox "always run in low graphic mode" and then continue.

By doing this you will not have the warning screen at boot anymore but you are still in 640x480.

Then I adapted my graphic card and my screen resolution manually via the System/Administration/Screen and Graphics application.
Ok, then log out once to verify that  the screen is now in perfect resolution.

But now when I reboot my graphics settings are kept and I boot now with 1440x900 resolution and with the right driver.

Why? I don't know but this solved the problem for me and I hope for others...

---

