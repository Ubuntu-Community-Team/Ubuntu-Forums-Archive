---
title: "Alsa Volume Control"
date: 2006-11-14
forum: Absolute Beginner Talk
---

### Post by DSn0wMan on 2006-11-14
Is there any way to tie the headphone volume in Alsa to the master volume?

I would like to be able to control the volume of my headphones with my media buttons. As it is now the media buttons adjust the master volume, but have no affect on headphone volume. This has been the case since I upgraded to Edgy.

---

### Post by ingomueller.net on 2007-01-11
Hi!

I had a similar problem one month ago and have spent a lot of time in its solution. As I stumbled upon this post, probably others will, so I'll post the link to a howto I wrote:

[http://alsa.opensrc.org/How_to_use_softvol_to_control_the_master_volume](http://alsa.opensrc.org/How_to_use_softvol_to_control_the_master_volume)

I hope this helps someone...

Ingo

---

### Post by DSn0wMan on 2007-01-12
Thanks for trying to help. The sugested solution did not improve anything. It seems like the master volume control does not control anything. I guess it's just a decoration in Edgy. Thats a shame, because it worked perfectly fine in dapper.

---

### Post by Shatrat on 2007-01-12
I'm not sure if this is related or will help you, but I've found that my gnome volume control panel applet thing works properly when I right click it and in Preferences highlight PCM instead of Master.

I'm not sure if your media buttons are working through the gnome panel volume applet but you can set it to control other audio channels than Master if you want.

---

### Post by DSn0wMan on 2007-01-13
You are right about the PCM / Master thing. Master should actually control PCM.

I found the fix. It is a bug in the driver for my sound card

[https://launchpad.net/ubuntu/+source/linux-source-2.6.15/+bug/41015](https://launchpad.net/ubuntu/+source/linux-source-2.6.15/+bug/41015)

Now Master controlls everything again, and media buttons control master by default.

---

### Post by ingomueller.net on 2007-01-20
Hi!

I just updated the howto from above. I tried to clarify, that you can only create a real master volume control, which is used by every application as such, if you don't have one yet. If you do have one, you can't overwrite it. What you can do, is create a volume control with another name (like "SoftMaster"), but only a few applications let you choose which control is the master control (I believe GMix/Gnomemixer) does. That's not a perfekt solution, but it may help anyway.

If you have more questions about the howto, please post them on the discussion page of the howto.

Greets, Ingo

---

