---
title: "help sound in ubuntu"
date: 2008-01-17
forum: Absolute Beginner Talk
---

### Post by exneo002 on 2008-01-17
I am currently fixing problems in my install so I can wait until this is answerd I installed via wubi so its in a virtual partion :( so upgrading was a bummer and my bro canceled it with I think the exact words 91hrs thats ******** so I had various HAL problems and gnome problems which Im fixin so basically I need help putting drivers for my hp pavilion a819n sound card realtek alc880 chipset which is onboard I'm a noob and I naivly put pulseaudio packages so I need advice my card only has an alsa driver should I use pulse audio alsa,oss or both with a switch like fedor also how do I install or compile the drives will any body be willing to compile me a .deb and I want easy bash scrip like sudo apt get and one last thing I'm am learning about development now I'm learning xml this september I learnd html4.0basics css basics so I want a good editor and compiling suite to .deb .exe or whatever

---

### Post by Dynaflow on 2008-01-17
This should give you the info you need, or at least a good starting point: [https://help.ubuntu.com/community/HdaIntelSoundHowto]("https://help.ubuntu.com/community/HdaIntelSoundHowto")

For more in-depth troubleshooting, go here: [http://ubuntuforums.org/showthread.php?t=205449]("http://ubuntuforums.org/showthread.php?t=205449")

For a script that semi-automatically compiles the latest version of ALSA for you, see here: [http://www.antonywilliams.com/2007/10/bash-script-to-automate-compiling-alsa.html]("http://www.antonywilliams.com/2007/10/bash-script-to-automate-compiling-alsa.html") (use only if you've determined that that is what you need to do).

Once ALSA is set up, remember to edit /etc/modprobe.d/alsa-base

find a line that looks like

options snd-hda-intel model=somethingorother

and change it to say

options snd-hda-intel model=hp 

(because you have an HP).  I found that was a crucial step to get my (HP) Compaq's sound working right.

---

### Post by exneo002 on 2008-01-18
I m a noob is thier a graphical program to manage alsa

---

### Post by Dynaflow on 2008-01-18
Not that compiles the latest version, so far as I know, though pnce you have it built, there are plenty of graphical tools for it.  Antony Williams's above-linked script is (relatively) pretty easy to use to get everything compiled and where it's supposed to go.  I can guide you through the process if you need help with it.

---

### Post by exneo002 on 2008-01-18
what about kompile

---

### Post by Dynaflow on 2008-01-18
I don't use KDE, so I can't be sure, but kompile might work too.  It's just a question of, does it cover all your bases for configuration, etc.?

---

### Post by exneo002 on 2008-01-20
what about a debian compiling tool then install ing the .deb via gdebpacage installer

---

### Post by Dynaflow on 2008-01-20
I think you have to install the latest version from source; I haven't seen a .deb installer for that version.  Instructions can be found here: [http://alsa.opensrc.org/index.php/Quick_Install]("http://alsa.opensrc.org/index.php/Quick_Install").

---

