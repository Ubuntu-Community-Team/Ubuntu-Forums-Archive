---
title: "Wanted: detailed info about the gnome-volume-control"
date: 2008-01-13
forum: Absolute Beginner Talk
---

### Post by wayfarer51 on 2008-01-13
I admit defeat.  I've looked all over trying to find information about gnome-volume-control, but I've been unsuccessful.  The arcane meanings behind such checkboxes as "Line Jack Sense", "Headphone Jack Sense"  and "Line-in Capture" elude me.  What is PCM?  LFE?  Channel Mode?  V_REFOUT Enable?

I'd really appreciate it if someone would tell me where I might find this information.

Thanks for your help,
Neill

---

### Post by mattismyname on 2008-01-13
I would download the source code for this program itself.  In there you should find some documentation of the features.

---

### Post by disturbed1 on 2008-01-13
> **wayfarer51 said:**
> I admit defeat.  I've looked all over trying to find information about gnome-volume-control, but I've been unsuccessful.  The arcane meanings behind such checkboxes as "Line Jack Sense", "Headphone Jack Sense"  and "Line-in Capture" elude me.  What is PCM?  LFE?  Channel Mode?  V_REFOUT Enable?

I'd really appreciate it if someone would tell me where I might find this information.

Thanks for your help,
Neill

These are just features for your sound card. Any general documentation will work, it is industry wide acronyms and options.

For the one's you listed -
LFE - Low Frequency Effects - your subwoofer output channel.
PCM - [SIZE=-1]Pulse code modulation -- a standard method of encoding analog audio signals in digital form. It's your volume control.
[/SIZE]Line Jack Sense - If you plug in your headphones to the front/headphone jack, it will be sensed and other outputs muted.
Line-in Capture - Available in 2 areas. To select this as the capture port (rather than microphone), and the level (volume) of the Line-in port.
Channel Mode - choose between stereo (2 channel), 4 channel, 6 channel (dolby 5.1) output modes.

Hope that helps.

You may also want to **R**ead **T**he **F**ine **M**anual for your soundcard and/or motherboard.


-----------edit-----------------

PCM is also used for digital out. For sending uncompressed audio via SPDIF or Coaxial to an outboard D/A converter such as your home reciever.

---

