---
title: "Function keys"
date: 2009-03-10
forum: Apple Hardware Users
---

### Post by spencercarran on 2009-03-10
Ubuntu 8.10 64-bit on a Macbook 3,1.

So a lot of useful keyboard shortcuts involve the function keys, and it is growing to be a pain to have to hold down the fn key at the corner of the keyboard anytime I want to use them. I'm trying to get this behavior switched, as described in the Ubuntu Macbook Wiki, but it doesn't seem to be working.
From the relevant Wiki:
> Accessing media keys with the fn-key

The default behavior on Apple keyboards is to have the top row keys primarily function as media keys (brightness, volume, etc), and have the function keys (F1, F2, etc.) accessible with the fn keys. If you want to switch that behaviour, add the following to /etc/modprobe.d/options:

options hid pb_fnmode=2

Rebuild the initd ramdisk with:

sudo update-initramfs -u -v -k `uname -r`

before rebooting to get the above change to work. 
I followed these instructions (sudo gedit /etc/modprobe.d/options and then copy-pasted the line they gave at the end of the file) but it does not seem to have had any effect. After rebooting the function keys all behave exactly as they had before I did anything.

---

### Post by inphektion on 2009-03-11
make sure you run this in a terminal
sudo update-initramfs -u -v -k `uname -r`

not sure what you did when you said you "copy and pasted" it.

---

### Post by spencercarran on 2009-03-11
> **inphektion said:**
> make sure you run this in a terminal
sudo update-initramfs -u -v -k `uname -r`

not sure what you did when you said you "copy and pasted" it.

Yes, I did that. No effect.
"Copy and pasted" just meaning I copied the "options hid pb_fnmode=2" so I know there is not a typo on my part.

---

### Post by cyberdork33 on 2009-03-11
do you have pommed install as well? it will conflict.

---

### Post by spencercarran on 2009-03-11
> **cyberdork33 said:**
> do you have pommed install as well? it will conflict.
Yes, I have pommed installed. I'll get rid of it and see what happens.

Yep, that did it. Thanks, Cyberdork.

It seems that the "thank" and "mark as solved" buttons have been done away with. I wonder why?

---

### Post by cyberdork33 on 2009-03-11
> **spencercarran said:**
> It seems that the "thank" and "mark as solved" buttons have been done away with. I wonder why?
resource loading on the forum webserver.

---

