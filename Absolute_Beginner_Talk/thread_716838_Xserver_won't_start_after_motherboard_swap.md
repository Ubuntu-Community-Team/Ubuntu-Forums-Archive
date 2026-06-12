---
title: "Xserver won't start after motherboard swap"
date: 2008-03-06
forum: Absolute Beginner Talk
---

### Post by BetterSense on 2008-03-06
I changed my mATX mobo from an ATI x200 motherboard to an Nvidia 7050. When I tried to start it up, it said it couldn't start the xserver because no screens were found. 

Then I ran dpkg-reconfigure xserver.xorg and went through the whole thing, and chose vesa as my drivers, and it finally got me t the gnome desktop. So I rebooted and it finally booted up normally to my KDE, but it was all fuzzy and stuff. I enabled restricted drivers in kcontrol, and it downloaded some stuff put then exited with an error, so I'm not sure if that worked. I was going to run Envy but I thought it would be a good idea to uninstall it first, but I couldn't run synaptic for some reason. I rebooted and it said it couldn't find any screens again. So I ran dpkg-reconfigure xserver.xorg again and picked 'nvdia' as my driver and it didn't work. And then I got angry and made a sandwich.

Do I have to reinstall Ubuntu, or is there some way to get this thing working?

---

### Post by taurus on 2008-03-06
Run that command again but pick either **vesa** or **nv** driver this time.

---

### Post by BetterSense on 2008-03-06
ok I did that and it did the same thing: 

[PHP]Fatal Server error:
no screens found 
X10 fatal IO error 104 on X server ':0.0' after 0 requests with 0 events remaining.
xauth: error in locking authority file /home/chaz/.Xauthority[/PHP]

What am I supposed to put for monitor refresh rate, etc? I have a 19" LCD.
Should I enable the kernal framebuffer thing?

---

