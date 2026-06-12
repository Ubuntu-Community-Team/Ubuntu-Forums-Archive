---
title: "Linux on a Gateway® ML6721 Notebook"
date: 2007-12-17
forum: Absolute Beginner Talk
---

### Post by renec2006 on 2007-12-17
I just purchased my laptop about 3 weeks ago and removed VISTA and installed Ubuntu 7.10. I'm only having trouble with my WiFi and my screen resolution. My panels don't go across the whole screen. I only goes about 3/4 of the screen. I've installed 915 resolution and kinds of stuff. Can somebody help me? Please! thanks
 rene :confused:

---

### Post by jken146 on 2007-12-17
You'll have to be more specific.  Tell us which graphics and wifi cards you have.  If you're not sure do ```
lspci
```

---

### Post by renec2006 on 2007-12-18
I have:
Intel® GL960 Chipset
Intel® Graphics Media Accelerator X3100 with up to 384MB of Dynamic Video Memory
Realtek RT8187B Wireless v.6.1090

thanks

Rene

---

### Post by lvleph on 2007-12-18
For the wireless check [donnieknows](http://donnieknows.com/bin/view/Main/GatewayML3109).

How did you get the sound working?

---

### Post by clayt0njknight on 2007-12-29
sound works native with Gutsy 32-bit, and all recent linux distros (last 6 months recent).  The newest kernel release and alsa releases support the Sigmatel audio chips that come in the ML6721, ergo they work out of box.

As far as resolution- I can only get 1024x768 in Ubuntu 7.10.  I did however figure out by changing the monitor on screen 1 to an LCD 1280x800 it fills the screen, but looks horrible.  I switched back to opensuse 10.3 Gnome/32-bit and i have a beautiful 1280x800 resolution view of my desktop.

The wireless is ridiculous on this notebook, but it is workable using NDISWRAPPER.  I've had limited success in using it, getting the NDISWRAPPER module to initialize but having to force a wireless connection manually.  I recently switched back to OpenSuse 10.3, and using NDISWRAPPER 1.5.1 I've successfully gotten a manageable wireless connection using ndiswrapper and the windows ME drivers from realtek's website.  If you'd like assistance feel free to reply to this post or PM me i'll do what i can to help.

Side note:  Compiz is blacklisting the 965GM (or x3100 as it's referred to on this notebook) so if you're looking for glitz and glamour it's going to require removing the 965 series from the blacklist section of /usr/bin/compiz.  I'm not an expert by any means as linux is massive, yet so so beautiful.  But I've been using and abusing for about 10 years now, and will provide whatever assistance i can :)


Clay

---

### Post by sharn on 2007-12-30
Don't give up on it. ;) Wireless works great now that I have it running. Using the Win98 driver from Realtek. Just follow the general directions for ndiswrapper and it ought to work.

As for resolution - I am still wondering the same thing.. I have the exact same laptop and the exact same problem. (Just in arch linux instead)

clayt0njknight, would you mind sharing your xorg.conf from your opensuse setup? 'Twould be much appreciated. :)

---

### Post by lvleph on 2007-12-30
Adding ndiswrapper to /etc/modules will get the ndiswrapper driver to load on system startup.

---

