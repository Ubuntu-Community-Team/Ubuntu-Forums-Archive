---
title: "No sound on Lenovo N200"
date: 2008-03-10
forum: Absolute Beginner Talk
---

### Post by aberadam on 2008-03-10
No sound on Lenovo N200 0769

I followed these instructions:  [https://wiki.ubuntu.com/LaptopTestingTeam/Lenovo_IBM](https://wiki.ubuntu.com/LaptopTestingTeam/Lenovo_IBM)

With the idea of doing this afterwards: 

> Sound does not work out-of-the-box, but this is simply fixed by adding the following to etc/modprobe.d/alsa-base

options snd-hda-intel single_cmd=1 model=lenovo

Now my volume is permanently muted and any attempt to interact with it gives the following message: No volume control Gstreamer plugins and/or devices found. 

Plus, I don't know how to edit "etc/modprobe.d/alsa-base"

Someone tell me how to fix this mess please! :)  I need my laptop to work properly.

---

### Post by aberadam on 2008-03-10
Trying to open the preferences for it gives this:

> "The volume control did not find any elements and/or devices to control. This means either that you don't have the right GStreamer plug-ins installed, or that you don't have a sound card configured.

You can remove the volume control from the panel by right-clicking the speaker icon on the panel and selecting "Remove From Panel" from the menu."

Before I followed the instructions above the volume thing would at least move up and down even if it had no effect.  Is there any way to revert back to that?

---

### Post by superprash2003 on 2008-03-10
hope this helps [http://prash-babu.blogspot.com/2008/02/sound-problems-in-ubuntu-gutsy-710.html](http://prash-babu.blogspot.com/2008/02/sound-problems-in-ubuntu-gutsy-710.html)

---

### Post by aberadam on 2008-03-10
Thanks, tried that but didn't work.

---

