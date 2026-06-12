---
title: "driver install"
date: 2005-10-28
forum: Absolute Beginner Talk
---

### Post by Hesselaar on 2005-10-28
I wanna install a soundcard driver, the readme (for linux) says that i need to copy something from a folder,
but that folder does not exist :???: 

What to do now?

---

### Post by Surfoo on 2005-10-28
Which driver ? Which is your soundcard ?

---

### Post by az on 2005-10-28
If your sound card does not currently work, look at this:
[http://packages.ubuntu.com/breezy/admin/pcmcia-source](http://packages.ubuntu.com/breezy/admin/pcmcia-source)

It is unlikely that you have a sound card that does not have drivers already available in ubuntu.

---

### Post by Hesselaar on 2005-10-28
C-Media CMI8738 this soundcard and the folder is  (/usr/src/linux/driver/sound).
I tried to play a music file but xmms said no soundcard found :???:

---

### Post by az on 2005-10-29
Boot into recovery mode and type

sudo modprobe cmpci


and then 
init 2


Does this make your card work?  If so, edit /etc/modules and add
cmpci
at the end on a line by itself.

If this does not work, post the output of
dmesg
and
lspci

---

