---
title: "How do I download a sound driver?"
date: 2007-06-09
forum: Absolute Beginner Talk
---

### Post by superhaus on 2007-06-09
I cannot get any sound at all. It looks like Ubuntu sees my sound card, but something is missing. I have been poking around and it looks like I have an ATI SB450 sound card. It appears to be supported, and I have seen some documentation on how to install the driver, but I cannot find out how to actually get the driver for it.

Any help would be appreciated.

---

### Post by ggaaron on 2007-06-09
All drivers are in kernel, usually as modules, ubuntu has almost all modules from kernel compiled, so it can load drivers for detected devices. Probably you don't have to install anything - just load the right modules if ubuntu didn't do that for you. Run lsmod and search for snd* - if there are such modules, then the driver is loaded and problem may be some elsewhere.

---

### Post by superhaus on 2007-06-09
Running lsmod shows a snd_hda_intel driver, so it is there.

Any suggestions on getting the sound to work then?

---

### Post by ggaaron on 2007-06-09
Search for some alsa and intel high definition issues... But at first run alsamixer and unmute everything and install mplayer and use it to play anything. I have two computers with intel and both work well, but I saw that people have problems with these...

---

### Post by martinrandau on 2007-06-09
snd-hda-intel can sometimes be troublesome. On Ubuntu 6.06 I had to compile the latest alsa-drivers myself to get it to work. You can quite easily do this following this guide: 
[http://www.alsa-project.org/alsa-doc/doc-php/template.php?company=Intel&card=ICH+southbridge+HD-audio+and+modem.&chip=ICH6%2C+ICH6M%2C+ICH7%2C+ESB2&module=hda-intel]("http://www.alsa-project.org/alsa-doc/doc-php/template.php?company=Intel&card=ICH+southbridge+HD-audio+and+modem.&chip=ICH6%2C+ICH6M%2C+ICH7%2C+ESB2&module=hda-intel")

Don't forget to install build-essentials so you can compile the thing!

Good luck!

---

### Post by ggaaron on 2007-06-09
On 6.06... I've always used newer version - maybe that is why it worked for me.

---

### Post by martinrandau on 2007-06-10
Well this card does not currently work by default under any of Mandriva 2007 Spring Free, Suse 10.2 and Debian Etch 4.0 - in all cases I have to compile the latest unstable alsa-drivers. Luckily it works out of the box on Ubuntu 6.10 and 7.04!

I have an Acer 5600, in case anyone has the same problem with this laptop.

---

