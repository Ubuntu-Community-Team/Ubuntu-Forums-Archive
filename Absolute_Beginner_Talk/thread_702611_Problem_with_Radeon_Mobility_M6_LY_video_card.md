---
title: "Problem with Radeon Mobility M6 LY video card"
date: 2008-02-20
forum: Absolute Beginner Talk
---

### Post by kalle_ka on 2008-02-20
Hi,

I have installed gutsy gibbon on my laptop (hp omnibook vt6200) with a pci videocard (Radeon Mobility M6 LY). However when I start ubuntu it always starts in low resolution mode, but when I use the live CD it works fine.

I tried some suggestions from another thread, starting in recovery mode and then issue the command dpkg-reconfigure xserver-xorg and changed video driver to "vesa". However, no luck....

I have attached my xorg.conf file and hope that someone can support me?

best regards,

/Mattias

---

### Post by miriad on 2008-02-20
The M6 card (Radeon 7500 I think) should be using the radeon driver instead of teh VESA driver.
I cant remember if this is provided by its own package still in Gutsy, or is in the newer ati driver package.
run (In terminal)
```

sudo apt-get install xserver-xorg-video-ati

```

If that gives an error, run this command instead:

```

sudo apt-get install xserver-xorg-video-radeon

```

Then, change the line in your xorg.config from:
```

Driver		"vesa"

```

to 

```

Driver           "radeon"

```

Then reboot X (control-alt-backspace) (Save all open windows first, it will kill all X programs).

You should be running the radeon driver by this point, and *should* be able to select resolutions.

---

### Post by kalle_ka on 2008-02-26
Hi again,

I tried the changes proposed in the earlier post but no luck. Still starts up in low-graphics mode with the vesa driver and the default monitor. I think it is also a problem with my monitor settings actually. Hope anybody has any suggestion how I can modify my xorg.conf file or any additional driver to load.

Attaching my Xorg.0.log file if it can be to any help....

/Mattias

---

### Post by oedha on 2008-02-26
what if :--> sudo dpkg-reconfigure -phigh xserver-xorg
from terminal and do not use vesa

---

### Post by kalle_ka on 2008-03-05
Hi,

That solved it. Now the driver used is "ati" and I get a resolution of 1024x768.

thanks

---

