---
title: "Sound and Screen resolution problems."
date: 2008-02-23
forum: Absolute Beginner Talk
---

### Post by Kingfisher9 on 2008-02-23
Hi there,

I have just completed a new Ubuntu installation (7.10) + 188 updates to my PC. Specs are below:

Athlon mobile processor, Nvidia NF2 Ultra Inifity mbd (from DFI), 1GB mem, Gforce 7800GS graphics card, lots of disk (and disk space), onboard sound (nforce2 AC97 audio controller).

And whilst I have taken the plunge away from Windows and I am really loving ubuntu and learning lots, I am still having some rather strange quirks at the moment.

**Sound**
There isn't any! Tried playing some movies and mps files and I get nada. Went to System->Preferences->Sounds and played with the settings. On the devices tab I get 5 settings for each of the main field ("Sound events", "Music and Movies", "Audio Conferencing"). These are
- Autodetect (default)
- NVidia nforce2 - IEC 958
- NVidia nforce2
- ALSA,
- ESD,
- OSS

I have tried testing all of them and still get to hear nothing.... I am listening through my headphones.

Any ideas?

**Screen resolution**
When I installed ubuntu, it mentioned that I would need to install some "non-free" drivers. I think these were drivers for the Gforce card. I agreed on the assumption that that would "make my experience more pleasant" and "allow me to use the full functionality of the card" or something like that.

Anyway it installed fine and I changed the resolution down to 1024x768 because I don't have a large screen. That changed fine too. I then rebooted slightly later and I am now back to 1600x1200 resolution. Strangely I cannot move away from that! If I change the settings in System->Preferences->Screen Resolution to something else I get a message saying that "Do you want to keep this resolution?", but nothing has actually changed.... I am still at the 1600x1200 resolution.

Suggestions would be very welcome... :)

Thanks in advance.

---

### Post by Presto123 on 2008-02-23
Well...this should help your video issues (that is, if you installed drivers from Add/Remove):

```
gksudo nvidia-settings
```

Within that menu, you should be able to change your video resolution with their menu and have it stick.

---

### Post by Kingfisher9 on 2008-02-23
Thanks Presto. After a reboot that seemed to work and I no longer have my nose pressed up against the monitor!

Still having sound problems though....

---

### Post by superprash2003 on 2008-02-23
try this, go to system->preferences->sound ... mostly all the options (like sound playback etc)would be auto detect.. change it to some other option like CS46XX..that worked for me.. try all options

---

### Post by Kingfisher9 on 2008-02-23
Thanks for all the ideas, but at the moment none of it seems to be hitting the mark. I have tried changing to all the different settings, but everytime I press test I get to hear nothing.

I have also tried the ideas shown in 
[http://ubuntu-utah.ubuntuforums.org/showthread.php?t=205449&highlight=ac97+audio+nvidia](http://ubuntu-utah.ubuntuforums.org/showthread.php?t=205449&highlight=ac97+audio+nvidia)
and
[http://ubuntuforums.org/showthread.php?t=620796&highlight=nvidia+nforce2+sound](http://ubuntuforums.org/showthread.php?t=620796&highlight=nvidia+nforce2+sound)

but all to no avail... 

:-|

---

### Post by Kingfisher9 on 2008-02-29
After searching around a bit I came across this...
[http://ubuntu-utah.ubuntuforums.org/showthread.php?t=253725&highlight=nvidia+AC97+sound](http://ubuntu-utah.ubuntuforums.org/showthread.php?t=253725&highlight=nvidia+AC97+sound)

The net result is that I can now hear sound (wheeee!). At first it didn't work and it was only when i realised that the was a hardware fault as well that I managed to achieve success.

Thanks to everyone for their help.

---

