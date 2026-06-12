---
title: "No Sound"
date: 2007-12-31
forum: Absolute Beginner Talk
---

### Post by frenchsquared on 2007-12-31
NO Sound card installed

it says -

The volume control did not find any elements and/or devices to control. This means either that you don't have the right GStreamer plugins installed, or that you don't have a sound card configured.

You can remove the volume control from the panel by right-clicking the speaker icon on the panel and selecting "Remove From Panel" from the menu.

but there is sound in vista, its a new laptop gateway m6824

Thanks in advance and you guys were great helping with the ATI card

---

### Post by frenchsquared on 2007-12-31
ok so I went to gateway andof course they only make the sound driver for Vista
I downloaded it, but I have no idea if I can do anything with it

---

### Post by tptbz on 2007-12-31
I have no idea if this will help but perhaps try,

A)
sudo gedit /etc/modprobe.d/alsa-base

and add the line "options snd-hda-intel model=5stack" without quotes under the heading # Prevent abnormal drivers from grabbing index 0.

B)
Then the following commands:

sudo apt-get install module-assistant
sudo m-a update
sudo m-a prepare
sudo m-a a-i alsa

You will need your ubuntu disc in your drive for the third command.

Reboot and see if sound works.

---

### Post by frenchsquared on 2007-12-31
thanks for trying

still get:
The volume control did not find any elements and/or devices to control. This means either that you don't have the right GStreamer plugins installed, or that you don't have a sound card configured.

You can remove the volume control from the panel by right-clicking the speaker icon on the panel and selecting "Remove From Panel" from the menu

when I click on the volume icon

---

### Post by frenchsquared on 2007-12-31
so anyone else have any idea
ubuntu think that I dont have any sound cards?
actually it has built in sound card and speakers

---

### Post by frenchsquared on 2007-12-31
should I move this to a more advanced forum

---

### Post by Xavieran on 2007-12-31
Try installing the GStreamer plugins in synaptic...search for GStreamer and install anything with -plugin on the end...

---

### Post by mattismyname on 2007-12-31
I would look through your kernel logs (/var/log/kern.log, or use the "System Log" GUI tool) and see if any messages about failing to load the sound driver module are present.

If so, pasting them here might help.

---

