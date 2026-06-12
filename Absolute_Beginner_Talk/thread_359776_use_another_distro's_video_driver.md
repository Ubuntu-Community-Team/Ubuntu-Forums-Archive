---
title: "use another distro's video driver"
date: 2007-02-12
forum: Absolute Beginner Talk
---

### Post by S P O R K on 2007-02-12
I have a working version of Puppy Linux running on a ATI Radeon 7000 video card.

The S-video out to my TV works on Puppy Linux.  It does not work with Ubuntu.

How can I use the drivers and settings from the Puppy Linux on the Ubuntu Linux?

thanks

---

### Post by r4ik on 2007-02-12
Try Envy,

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

supports ATi also.

---

### Post by FenrisAbraxas on 2007-02-12
> **S P O R K said:**
> I have a working version of Puppy Linux running on a ATI Radeon 7000 video card.

The S-video out to my TV works on Puppy Linux.  It does not work with Ubuntu.

How can I use the drivers and settings from the Puppy Linux on the Ubuntu Linux?

thanks

Install the same driver version in ubuntu and just copy the xorg.conf (just if it's the same PC or same hardware) that should do it.

---

### Post by S P O R K on 2007-03-02
Ok, I brought the linux box back into the office.

(Can't get the modem to work so I have to use the office network.)

I downloaded the ENVY package and installed the ATI driver to no avail.  I recovered the orignial xorg.conf file so the GUI works again.

It looks like Puppy Linux works in the xvesa mode but not the xorg mode.  I don't know what mode Myth TV is running.

How/where (explicitly please) do I get the video driver out of either Puppy Linux or Myth TV distro.  Where do these things reside in the Linux world.  After I find the files how do I install them?


thanks

---

