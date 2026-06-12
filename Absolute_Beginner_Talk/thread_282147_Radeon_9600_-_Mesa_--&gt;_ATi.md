---
title: "Radeon 9600 - Mesa --&gt; ATi"
date: 2006-10-22
forum: Absolute Beginner Talk
---

### Post by ctrl_freak on 2006-10-22
[SIZE="4"]**Can someone walk me through installing the ATi Drivers?**[/SIZE]

I'm having problems switching from the Mesa drivers for my card, to the ATi ones...

fglrxinfo outputs the following.
```
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.4.1)

```

I have followed any tutorials online, but to no avail - including the ones on these forums...

I'm running Dapper 6.06 LTS.

If anyone can help me, it would be brilliant.

Thanks

ctrl_freak

---

### Post by ctrl_freak on 2006-10-23
*bump*

---

### Post by podunk on 2006-10-23
Did you try the one from these folks?
[http://wiki.cchtml.com/index.php/Main_Page](http://wiki.cchtml.com/index.php/Main_Page)

Quite a bit of useful info on the lead in page - when it got down to the actual install I followed methood 1.

---

### Post by ctrl_freak on 2006-10-23
Mm... I have, but I'll dig around their a bit more, and see what I can do. Thanks.

---

### Post by ctrl_freak on 2006-10-24
> **ctrl_freak said:**
> Mm... I have, but I'll dig around their a bit more, and see what I can do. Thanks.

fglrxinfo is still coming up with Mesa handling OpenGL...

---

### Post by Circus-Killer on 2006-10-24
if you are trying to get the ati driver running in edgy, 
add the following to the bottom of /etc/X11/xorg.conf:

> Section "Extensions"
    Option  "Composite" "0"
EndSection

this is because the fglrx driver does not support composite managers yet, and composite is enabled by default in edgy.

---

### Post by ctrl_freak on 2006-10-24
Sorry, I'm using Dapper. (6.06 LTS)

The device section in my xorg.conf has this.

```
Section "Device"
	Identifier  "ATI Technologies, Inc. RV350 AQ [Radeon 9600 SE]"
	Driver      "fglrx"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
	BusID       "PCI:1:0:0"
EndSection
```

Is it my understanding that the 'Driver' should still be fglrx? Why is Mesa still coming up under fglrxinfo!??!

UPDATE: I'm follwing Method 2 - and gonna see what heppens...

---

### Post by Circus-Killer on 2006-10-24
the reason for this is because, although fglrx is mentioned in xorg.conf, it isnt loading successfully, so it reverts back to the mesa driver.

try what i said anyway (with the adding that composite section at the bottom). if it doesnt work, then undo that, and do the following.

download the following file:
[http://www.ground-impact.com/libGL.so.1.2]("http://www.ground-impact.com/libGL.so.1.2")

then move that file into /usr/lib/ with root access by doing the following:
 $ sudo mv ~/FileLocation/libGL.so.1.2 /usr/lib/

and try again.

if neither work, then try turning OpenGLOverlay on.

---

### Post by zappa on 2006-10-24
See here: 
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

In your case I'd restart the proces. I'm afraid somewhere along the road the module does not load. If the dapper does not work for you, use the Hoary way. It does the same after all, but it was somewhat simplified in Dapper ;)

---

### Post by ctrl_freak on 2006-10-24
The second method worked perfectly - I've successfully played Enemy Territory online with good fps!

Thanks heaps.

---

### Post by Circus-Killer on 2006-10-24
hehehe, no problem, glad i could help a fellow ET player :D

---

