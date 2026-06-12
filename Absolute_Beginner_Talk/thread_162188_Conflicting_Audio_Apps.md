---
title: "Conflicting Audio Apps"
date: 2006-04-18
forum: Absolute Beginner Talk
---

### Post by VoiceOvGod on 2006-04-18
Wierd thing...

I've got both GNOME and KDE for desktops...

Since installing KDE, I can't seem to play mp3s...

Amarok said that some other device is using it... but I don't have anything running...

Anyone else had that?

---

### Post by Kimm on 2006-04-18
try running:

killall esd

in your terminal, ESD is the Gnome sound deamon and it might do this.
If this fixes it, run gstreamer-properties and set output to "ALSA - Advanced Linux Sound Architecture"
then open kcontrol and change the sound system to use ESD. After you did this, open your terminal and type:

sudo apt-get install libesd-alsa0

In my experiance this makes sound happier! :)

---

### Post by uteck on 2006-04-18
You may have esd running, which is what gnome uses for sound.  
Also check what engine Amarok is using and try a different one.  If there are no other choices, then you will have to install them with apt first.  Just search for amarok and look for the different sound engiens.

---

