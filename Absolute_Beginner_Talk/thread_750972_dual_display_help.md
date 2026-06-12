---
title: "dual display help"
date: 2008-04-10
forum: Absolute Beginner Talk
---

### Post by catroaring on 2008-04-10
im going through this [http://ubuntuforums.org/showthread.php?t=221174](http://ubuntuforums.org/showthread.php?t=221174)

i have only one display plugged in.  

how do i know if i have the binary drivers installed?

Just hit enter for the most options, though if you have the binary drivers installed, you might want to select that. This code will generate a new, clean, standard xorg.conf file for us to work on.

---

### Post by warbread on 2008-04-10
What video card do you have?  If you have an nVidia card, install the driver using the Restricted Driver gui in System> Administration and then apt-get install nvidia-settings.  Run nvidia-settings from terminal (no sudo is required) and configure your dual monitor setup from there.

---

### Post by forestpixie on 2008-04-10
If you don't use sudo to run nvidia-settings the changes won't be written to xorg.conf and you'll need to run it each time, unless there's been a chnage to it.

---

### Post by warbread on 2008-04-10
> **forestpixie said:**
> If you don't use sudo to run nvidia-settings the changes won't be written to xorg.conf and you'll need to run it each time, unless there's been a chnage to it.

This has not been my experience, but it makes perfect sense.  Still, I would suggest not using sudo on the first try for this very reason.  If something happens to go wrong, it won't persist to the next boot.

---

### Post by forestpixie on 2008-04-10
> If something happens to go wrong, it won't persist to the next boot.

There is that - I always make sure I have a good xorg.conf, and any other files I've modified, backed up into my home for just such an occasion :) 

But I never got the changes to save to xorg without running it as root.

---

### Post by warbread on 2008-04-10
Yes, and the more I think about it, the more I realize that I haven't actually made any persistent changes using nvidia-settings since I stopped using dual monitors.

---

### Post by catroaring on 2008-04-10
i am using a nvidia card.  i have installed the restricted driver.  when i do nvidia-settings i get this

human@athlon1800:~$ nvidia-settings

ERROR: NV-CONTROL extension not found on this Display.


ERROR: Unable to determine number of NVIDIA GPUs on ':0.0'.


ERROR: Unable to determine number of NVIDIA Frame Lock Devices on ':0.0'.


ERROR: Unable to determine number of NVIDIA VCSCs on ':0.0'.

---

