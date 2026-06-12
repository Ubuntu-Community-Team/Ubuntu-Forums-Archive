---
title: "gui install window offscreen"
date: 2007-08-13
forum: Absolute Beginner Talk
---

### Post by tommason on 2007-08-13
Hey,
I have been trying to install ubuntu on an old pc of mine...the live cd works absolutely fine until i try and run the install program, that seems to work fine, but the bottom half of the window is off the screen. I've tried maximising (it doesn't) resize window (it is at its smallest size and won't reduce further) tabbing (doesn't seem to want to get to the 'next' button)

I have a widescreen flat monitor (1440x900-19inch) which is connecting to my pc via an analogue cable - the only screen resolutions i can get is 800x600 or 640x480 which is why the problem is there. In 'blocked drivers' or whatever it's called it mentions a nvidia driver that it is preventing from being used. I try to force it to use it, it downloads something, attempts an install and then says 'can't do it' (pardon my lack of jargon)

Any ideas? (I am downloading the alternate cd as we speak, but wondered if there was a simple fix to this)

Cheers!

Tom

---

### Post by Tiekyl on 2007-08-13
Try using alt then the mouse to drag the window. Then after you install it, you can go to System-administration-Restricted drivers manager and tell it to use the Nvidia driver. But the alt-moving should help until then.

---

### Post by tommason on 2007-08-13
...so that would allow me to move the top of the install window beyond the top of the screen?

---

### Post by Tiekyl on 2007-08-13
Yup! :-)

---

### Post by Coward on 2007-08-13
I think Alt+f7 is what allows you to move the window above the screen easily.

---

### Post by tommason on 2007-08-13
to answer my own question - yes it will!
Cheers - installing now....

---

### Post by Hobo Joe on 2007-08-13
Yes.


What is your graphics card?

---

### Post by Tiekyl on 2007-08-13
> **Coward said:**
> I think Alt+f7 is what allows you to move the window above the screen easily.

Oh..apparently alt-f7 does that 2? Haha cool. Never knew that ^_^

---

### Post by tommason on 2007-08-13
> **Hobo Joe said:**
> Yes.


What is your graphics card?

gainward GeForce4 Ti 4200 agpx8

---

### Post by Hobo Joe on 2007-08-13
Once you install, get Envy and install your nVidia drivers. Saves you a load of trouble with drivers.

Link is in my sig.

---

### Post by tommason on 2007-08-13
cheers - all sorted. :)

---

### Post by tommason on 2007-08-14
done that! all seemed fine shutdown and went to bed - woke up to my computer still humming (having not shut down) and when i try to restart i get a:  'failed to start the xserver....' message... :(
Tried:
"sudo dpkg-reconfigure xserver-xorg"
selected nv drivers and followed line of least resistance to no avail.... :( :(

---

