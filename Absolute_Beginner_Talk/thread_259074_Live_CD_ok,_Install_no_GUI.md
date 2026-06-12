---
title: "Live CD ok, Install no GUI"
date: 2006-09-16
forum: Absolute Beginner Talk
---

### Post by uzd4ce on 2006-09-16
The live cd works fine on my Dell E510, but after I got it installed, I have no GUI.  It boots up ok, but then it tells me that X server couldn't start.

If the live cd worked ok, shouldn't the install work too?  Is that a sign of a faulty install?

Thanks

---

### Post by smartalecks on 2006-09-16
Boot to the Live CD, but when it boots with the prompt asking you whether you want to start the Live CD, choose "Check CD for Defects." Sorry if I sound unclear, here is what I mean:

The 3rd option
[IMG]http://shots.osdir.com/slideshows/659/1.gif[/IMG]

Could be a bad CD. (Did you burn it yourself or get it from Shipit?)
Also, can you post your hardware specs?

---

### Post by Bobido on 2006-09-17
Are u using ATI card?
If so, you need to edit the xorg.conf

sudo gedit /etc/X11/xorg.conf 

In the "device"
change"ATI" to "radeon" 

Hope it helps.

---

### Post by smartalecks on 2006-09-17
> **Bobido said:**
> Are u using ATI card?
If so, you need to edit the xorg.conf

sudo gedit /etc/X11/xorg.conf 

In the "device"
change"ATI" to "radeon" 

Hope it helps.

If the Xserver doesn't work, then gedit won't work either.
```

sudo nano /etc/X11/xorg.conf 

```

---

