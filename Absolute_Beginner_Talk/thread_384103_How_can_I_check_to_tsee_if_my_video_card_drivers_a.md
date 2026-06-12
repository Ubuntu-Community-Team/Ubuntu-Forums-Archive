---
title: "How can I check to tsee if my video card drivers are correct?"
date: 2007-03-14
forum: Absolute Beginner Talk
---

### Post by diargasm on 2007-03-14
I want to check and see if my OS is recognizing my videocard "Nvidia 6800 go".  I checked system devices and didn't see anything in regards with that.  I tried to install the NVidia drivers with Easy Ubuntu, but it would not let me do the legacy drivers and it just freezes.

---

### Post by tchoklat on 2007-03-14
on boot up your bios will print the name of your video card on your screen and you should be able to see it then.

If unsure download ENVY from synaptic and it will fix all!

Tony

---

### Post by maniacmusician on 2007-03-14
your xorg.conf can tell you what driver you're using. (located at /etc/X11/xorg.conf)

under the Device section, I believe. If the driver is "nv" then you're using the plain open source driver. If the driver is nvidia, you're using the proprietary drivers (needed for 3D acceleration and whatnot).

if you're using vesa, well, I feel sorry for you :)

---

