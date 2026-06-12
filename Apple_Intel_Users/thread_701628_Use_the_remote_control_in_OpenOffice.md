---
title: "Use the remote control in OpenOffice"
date: 2008-02-19
forum: Apple Intel Users
---

### Post by FFuser on 2008-02-19
Hi all,

I want to control an openoffice slide show (or evince) by the remote control that is delivered with any apple computer.

This doesn't work out of the box (and I don't even know if it is possible).
Does anyone have an idea how to do this?

Greetings
Nathan Samson

---

### Post by [woodstock] on 2008-02-19
Maybe [this]("http://ubuntuforums.org/showthread.php?t=502924") post will help.
Please report here if it worked for you.

---

### Post by cyberdork33 on 2008-02-19
The apple remote should work out of the box on most Mac hardware. What is the hardware you are using?

---

### Post by FFuser on 2008-02-20
Well, my remote worked out of the box:

I could manage volume with +/- and I think (but I'm not sure), that even play/pause/rewind and forward worked in totem.

But after installing these packages (or amybe after upgrading some stuff) nothing of my control worked anymore. Even after uninstalling and rebooting the volume controls don't work.

But what never worked was controlling openoffice by the remote control (maybe I needed to change configuration for that?)

Anyway, I'm using a macbook (june 2007, so before last generation), with Hardy Heron on it (so maybe the problems lay there)

I tried now installing mythubuntu-lirc-generator, but that din't help (It created config files, but they didn't work).
Maybe I'm trying the wrong lirc config. I choose the Apple Mac mini remote control, and No transmitter

---

### Post by cyberdork33 on 2008-02-20
I think that the module "appleir" has to be loaded for the remote to work. You will have to get lirc working before you can do anything with OpenOffice.org I am sure, so check out the previously posted thread. I can't really find anything in particular on OppenOffice + remote controls, so it may be a matter of mapping the remote buttons to certain keyboard commands in the lirc configuration or something.

---

### Post by FFuser on 2008-02-20
For some reason I can't get my remote working.

It seems that I tried everything but nothing workde (sudo moprobe appleir didn't give anything).

Maybe someone can help me with some debugging pointers (I seem not to get any result wit xev for example, but maybe that is normal)

---

