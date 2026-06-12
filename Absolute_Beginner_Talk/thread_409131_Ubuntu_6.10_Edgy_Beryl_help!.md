---
title: "Ubuntu 6.10 Edgy Beryl help!"
date: 2007-04-14
forum: Absolute Beginner Talk
---

### Post by makinasvp on 2007-04-14
In the Beryl Manager, I have 2 options 

-Beryl
-Metacity (GNOME window manager)

My Beryl won't work, I can't get to my cube or anything... When I try to switch from Metacity to Beryl, it wont let me, for some reason it just sticks with Metacity.

I have nvidia by the way.

---

### Post by makinasvp on 2007-04-14
By the way, I typed "Beryl" in my terminal, and this is what I get:

```

**************************************************************
* Beryl system compatiblity check                            *
**************************************************************

Detected xserver                                : NVIDIA

Checking Display :0.0 ...

Checking for XComposite extension               : failed

No composite extension

```

---

### Post by makinasvp on 2007-04-14
bump

---

### Post by makinasvp on 2007-04-14
ok so I went to my /etc/X11/xorg.conf and changed the Section Extensions composite thing from Disable to Enable and restarted X11 but no luck, since my graphics displays were gone, so I restored them, typed Beryl in the terminal and now get this:

```

**************************************************************
* Beryl system compatiblity check                            *
**************************************************************

Detected xserver                                : AIGLX

Checking Display :0.0 ...

Checking for XComposite extension               : passed (v0.3)
Checking for XDamage extension                  : passed
Checking for RandR extension                    : passed
Checking for XSync extension                    : passed

Checking Screen 0 ...

Xlib:  extension "GLX" missing on display ":0.0".
Root visual is not a GL visual
Xlib:  extension "GLX" missing on display ":0.0".
beryl: Root visual is not a GL visual
beryl: Failed to manage screen: 0
beryl: No manageable screens found on display :0.0
```

---

### Post by joeashcraft on 2007-04-15
What kind of video card to you have?

---

### Post by jvc26 on 2007-04-15
By the looks of it you don't have compositing enabled. Depending on your gfx card you will need to enable it and install the correct drivers - there are loads of guides out there if you find one for your card/manufacturer. Please note beryl is BETA software and as such may cause your computer to crash, so you use at your own risk (as [here]("http://ubuntuforums.org/showthread.php?t=349732") explains it is offtopic in the beginners talk section, and would be better placed in the desktop environments section.)
Il

---

