---
title: "Desktop Effects not working after reboot"
date: 2007-10-27
forum: Absolute Beginner Talk
---

### Post by akiratheoni on 2007-10-27
So I have Ubuntu 7.10 Gutsy Gibbon and an Intel GMA 950 using the intel driver that came with 7.10

The desktop effects have been working perfectly fine for me, until just a couple minutes ago and it just completely died out after I rebooted the computer.

When I run compiz --replace &, I get this error.

```
abong@zantherus-desktop:~$ compiz --replace &
[1] 6436
abong@zantherus-desktop:~$ Checking for Xgl: not present. 
Detected PCI ID for VGA: 00:02.0 0300: 8086:2772 (rev 02) (prog-if 00 [VGA])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: not present. 
aborting and using fallback: /usr/bin/metacity 

```

When I run the glxinfo, it says I have no direct rendering.

```
abong@zantherus-desktop:~$ glxinfo
name of display: :0.0
display: :0  screen: 0
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)

```

Going to System > Preferences > Appearance > Visual Effects and selecting any of the options for desktop effects tells me that 'Desktop effects could not be enabled'.

It was just working earlier today!

---

### Post by Maestro23 on 2007-10-27
Here's the Intel GMA section of the Compiz-Fusion Wiki.  Might shed some light on some things for ya.
[http://wiki.compiz-fusion.org/Hardware/Intel](http://wiki.compiz-fusion.org/Hardware/Intel)

Hope it helps. Good luck.:)

---

### Post by akiratheoni on 2007-10-27
> **Maestro23 said:**
> Here's the Intel GMA section of the Compiz-Fusion Wiki.  Might shed some light on some things for ya.
[http://wiki.compiz-fusion.org/Hardware/Intel](http://wiki.compiz-fusion.org/Hardware/Intel)

Hope it helps. Good luck.:)

I followed the instructions for the XGL one (I'm pretty positive I used that before) but it didn't work. 

Inputting the command they told me to (INTEL_BATCH=1 compiz --replace ccp&), I got this error:

```
abong@zantherus-desktop:~$ INTEL_BATCH=1 compiz --replace ccp&
[1] 6264
abong@zantherus-desktop:~$ Checking for Xgl: not present. 
Detected PCI ID for VGA: 00:02.0 0300: 8086:2772 (rev 02) (prog-if 00 [VGA])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: not present. 
aborting and using fallback: /usr/bin/metacity 

```

And using the compiz --replace & got me the same error. 

Any other suggestions? Thanks.

---

### Post by The O'Really Factor on 2007-10-28
Hmm, That sounds like the problem I had when I used beryl a while back. Try switching to AIGLX

EDIT: Oh and make sure that this line is present in the device section of your xorg.conf;
```
Option		"AddARGBGLXVisuals"	"True"
```

---

### Post by akiratheoni on 2007-10-28
Still isn't working. I had to manually add sections of my xorg.conf since most of the sections weren't there according to the instructions. I'm starting to get really mad at this, but I don't want to reinstall unless there is a quick way for me to download and install all the programs I had previously.

---

### Post by The O'Really Factor on 2007-10-28
Hmm. One question: What kind of video card are you using?

---

### Post by akiratheoni on 2007-10-28
I'm using an Intel GMA 950, which is why I followed the instructions for the Intel chipset on the Compiz-Fusion wiki.

---

