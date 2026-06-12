---
title: "Speakers Don't Work in Ubuntu"
date: 2007-07-09
forum: Absolute Beginner Talk
---

### Post by orbitcow on 2007-07-09
So I installed Ubuntu and I love it the only problem is that my speakers don't work.
I have a Toshiba Satellite A135-S4527.  the speaker icon has an x over it.  I've looked everywhere, one place said to add "options snd-hda-intel probe_mask=8 model=3stack" at the bottom of /etc/modprobe.d/alsa-base.  Did that and it still doesn't work.  I installed the GStreamer Plugins and it doesn't work.

---

### Post by lisati on 2007-07-09
I use one of the Toshiba A100 range of laptops, and had no sound when first installing Ubuntu 7.04. It wasn't until I had installed update through Update Manager, rebooting, clicking on the speaker to open up the volume control and then turning up the volume that I had sound. Maybe this will work for you too.

**Afterthought** I didn't need to mess round looking for ALSA drivers - doing the update, a reboot, and turning up the volume was enough for my machine

---

### Post by orbitcow on 2007-07-09
Mines up to date just no sound.

---

### Post by lisati on 2007-07-09
> the speaker icon has an x over it
Do you get a volume control appear on your screen when you double-click on the speaker?

---

### Post by orbitcow on 2007-07-09
**This post could be related to an Ubuntu bug filed at**: [http://ubuntuforums.org/showthread.php?p=2977305](http://ubuntuforums.org/showthread.php?p=2977305) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				i fixed it, found this in another thread here:

 In terminal type in the following,

gksu gedit /etc/modprobe.d/alsa-base

Add the following to the bottom of the file,

options snd-hda-intel model=3stack

Save the file and reboot.



Thanks for your help though.

---

