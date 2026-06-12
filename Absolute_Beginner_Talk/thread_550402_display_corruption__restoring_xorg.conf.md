---
title: "display corruption / restoring xorg.conf"
date: 2007-09-13
forum: Absolute Beginner Talk
---

### Post by Odoacer on 2007-09-13
Hi,
I installed Gutsy on a Thinkpad X61s. After installation, I attached an external monitor (via the Thinkpad Ultrabay). Worked OK, but couldn't get the display to stretch to my laptop's screen as well as the external monitor (Dell 2001FP). 

In the process of trying to get this figured out, I fiddled around with the monitor driver via the System>Admin>Screens and Graphics interface, setting it to 2001FP for awhile. Now, whenever I try to boot and use just the laptop display, the screen is incredibly corrupted. (I've since reverted it to the Plug-n-Play driver, but no dice.) I can only do things on the external monitor now.

I didn't make a backup before doing all this.

From what I can gather, my xorg.conf file needs to be fixed, but I have no idea what my defaults should be. I'm also loath to edit it by hand, seeing as I could completely break a lot of things that way. Any ideas on how I can safely restore my settings to the installation defaults?

---

### Post by bsharp on 2007-09-13
boot into a recovery mode and see if the system made a backup for you named 

/etc/X11/xorg.conf~ 

or something like that 

If not then you can rebuild the conf file by typing (also in recovery mode)

```
dpkg-reconfigure x11-common
```

---

### Post by Odoacer on 2007-09-13
Thanks for the prompt reply. Upon inspecting /etc/X11 (should've done that earlier), I saw a few files named xorg.conf.1, xorg.conf.2 and so forth. At first glance, xorg.conf.1 looked like what I needed, so I did a quick cp and all seems to be good... writing this from my laptop's primary display right now.

Bless whoever had the foresight to automatically back up display settings before having users change them.

---

