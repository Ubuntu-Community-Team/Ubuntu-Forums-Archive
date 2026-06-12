---
title: "Compiz Fusion woes on IBM T20"
date: 2008-01-15
forum: Absolute Beginner Talk
---

### Post by jstyles40 on 2008-01-15
IBM Thinkpad T20 with S3 Inc. 86C270 Savage /IX-MV

Driver="savage"

Tried to follow numerous tutorials on getting Compiz Fusion to work.

1st get indication of no Whitelist drivers...

Added "savage" to usr/bin/compiz file

Now getting :

Checking for Xgl: not present
Detected PCI ID for VGA: 01:00.0 0300: 5333:8c12 (rev 11) (prog-if 00 [VGA])

Checking for texture_from_pixmap: present
checking for non power of two support :present
Comparing resolution (1024x768) to maximum 3d texture size (2048) passed
checking for nVidia: not present
checking for Xgl: not present
/usr/bin/compiz.real (core) - Error: Fatal: No GLXFBConfig for default depth, this isn't going to work

/usr/bin/compiz.real (core) - Error: Failed to manage screen: 0
/usr/bin/compiz.real (core) - Fatal No manageable screens found on display : 20.0

exec: 379 /usr/bin/metacity: not found.

Then my windows lose their borders and lose ability to move windows..and I have to use xfwm4 command to regain control of desktop.

Thanks !!!! really tried many things for days before posting,,,any help is greatly appreciated..

IBM T20 750Mz - 512 Ram.

---

### Post by SunnyRabbiera on 2008-01-15
It might not be possible, your model is pretty old.
I know she has a PIII so that might be one of the factors.

---

### Post by jstyles40 on 2008-01-15
on the compiz fusion forum, I receieved a reply stating compiz only works with ATI / Intel / and NVidia GPu's.

Anyone ever get this to work on a S3 Graphics card ?

Thanks
JS

---

### Post by SunnyRabbiera on 2008-01-15
it might be too old.
Is it vital you use compositing manager or is it just for aesthetics?

---

### Post by jstyles40 on 2008-01-15
just trying to see the nice eye candy I keep seeing on youtube..

---

### Post by SunnyRabbiera on 2008-01-15
It might not be feasible sorry to say...
I know having effects is nice but on those specs I am afraid not much is going to work.

---

