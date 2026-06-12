---
title: "No video on boot of install cd (Powermac G4 MDD, 877mhz, Geforce4 MX)"
date: 2010-11-12
forum: Apple Hardware Users
---

### Post by besby11 on 2010-11-12
Hello everyone,

   In an attempt to revive this sexy beast, I'm trying to install the community version of Ubuntu 10.10 for ppc on my old MDD G4. I burned the CD and got it to boot and whatnot, but it gets to a point and the video stops displaying, the monitor goes dead and stops receiving a signal. This happens right after you are allowed to select boot options, it goes to a white screen with some text, after that boom, gone. If that wasn't weird enough get this, the rest of the machine goes on it's merry way booting. I can even hear the Ubuntu chime over the speakers as if it was booted and ready to go. I've looked around but can't find a definitive answer to why this is. The graphics card is a Geforce4 MX series. This is an older card so I would think it would be supported. Anyway thanks!



                                                         Hunter Baker

---

### Post by linuxopjemac on 2010-11-12
You might want to switch to the nv driver instead of the standard nouveau.
Have a look at some xorg.conf files at:
[http://mac.linux.be/content/xorgconf-files](http://mac.linux.be/content/xorgconf-files)

---

### Post by besby11 on 2010-11-12
Alright, well how would I get at the xorg.conf file if I cannot get video on the screen past yaboot. I've tried getting into the terminal but I can't even do that. Is there any solutions I can enter at the yaboot prompt?

---

### Post by linuxopjemac on 2010-11-12
you could try
```
video=ofonly
```

---

### Post by besby11 on 2010-11-13
Yea I've tried that, after the yaboot on ether tries I get a white screen with some text about expanding trees or something. Is there anyway to edit the xorg before I burn the ISO so that it uses the correct one?

---

### Post by linuxopjemac on 2010-11-13
Go for the alternate install, without GUI.

---

### Post by harlock59 on 2012-07-27
At yaboot screen type live nouveau.modeset=0

---

### Post by wildmanne39 on 2012-07-28
Hi, this is an old thread so it has been closed, please do not post in threads that are a year or more old, and thanks for sharing.

---

