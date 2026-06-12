---
title: "How do you get Alsa to work?"
date: 2007-02-28
forum: Absolute Beginner Talk
---

### Post by bot42 on 2007-02-28
Hi there!
           I'm a newbie to Gnu/Linux and Ubuntu. Great system by  the way especially for making use out of old pcs like my Pentium II. However as the title suggests I dont know how to get Alsa to work for my Creative SoundBlaster AWE32 soundcard. The Alsa site appears to contain the drivers but the installation sounds too technical (and outdated) for guys like me that have no idea about Unix commands and safely compling code into the kernal. 

This is a link to the driver page.   [http://www.alsa-project.org/alsa-doc/doc-php/template.php?company=Creative+Labs&card=Sound+Blaster+64+Value.&chip=sb16%2C+emu8000&module=sbawe#opt](http://www.alsa-project.org/alsa-doc/doc-php/template.php?company=Creative+Labs&card=Sound+Blaster+64+Value.&chip=sb16%2C+emu8000&module=sbawe#opt)


PS: Any jargon definitons would appreciated.

---

### Post by xyz on 2007-02-28
Hi,
To start with, type
```
alsamixer
```
in a terminal and see what's on or not.

---

### Post by bot42 on 2007-03-01
i've done that it reads "function snd_ctl_open failed for default: No such device found". Shouldnt Alsa detect the sound card if it already has the drivers. It did that when i booted up the live cd of ubuntu on my other pc which uses a sound blaster audigy 2zs. Anywayz the problem is that don't know how to install the sound drivers (which i downloaded) for my AWE32.

---

### Post by bot42 on 2007-03-03
To make more sense of the problem, My pc (with the AWE32) doesn't get any sound and all i know is that my copy of ubuntu (6.06 LTS) didn't come with the ALSA sound driver for my AWE32 and that I need to download the driver which I have already done. however as far as i know is i'll have to use the command line which i have no idea on how to use, although i can only do basic browsing on it. Is there any way to install the driver via GNOME or KDE?

---

