---
title: "GStreamer plug-ins gone bye bye"
date: 2007-01-31
forum: Absolute Beginner Talk
---

### Post by Mark_in_Hollywood on 2007-01-31
Closed thread

Success, by accident I solved the problem, but have no idea as to how.

Following instrctions at

Comprehensive Sound Problem Solutions Guide v0.5e

I did:

aplay -l

which I received a success response from: 
success

next:

lspci -v

showed the pci devices, mine is Ensoniq 1371
success

Next, I found my soundcard driver info at:
[http://www.alsa-project.org/alsa-doc/](http://www.alsa-project.org/alsa-doc/)

and

sudo modprobe snd-
with the <tab>
showed about 120 devices mine was listed as: snd-ens1371

so I

sudo nano /etc/modules

and added snd-ens1371

wrote the file out and exited,

looked at

alsamixer

which seemed normal, next I did:
sudo alsactl store 0

grep 'audio' /etc/group
shows me as a authorized user

and lastly

sudo nano /etc/modprobe.d/alsa-base
options snd-ens1371 mpu_port=0x330

I left home, turning the computer back on after the chores to find that the panel icon loudspeaker now has a red ring and diagonal bar, indicating no sound/soundcard

clicking the icon returned:
No volume control GStreamer plugins and/or devices found.

So, what do I do now?

---

### Post by jernomer on 2007-02-02
I am having this problem, too. The little icon in the panel is not responding and when I click on it this message pops up: "No volume control GStreamer plugins and/or devices found".

As far as I know, I have the GStreamer plugins installed and the sound enabled. Any ideas on how we can fix this?

---

