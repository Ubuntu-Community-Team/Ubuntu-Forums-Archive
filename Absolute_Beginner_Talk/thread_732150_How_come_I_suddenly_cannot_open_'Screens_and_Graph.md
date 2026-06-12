---
title: "How come I suddenly cannot open 'Screens and Graphics' or 'Frostwire'?"
date: 2008-03-22
forum: Absolute Beginner Talk
---

### Post by whoscheesemine on 2008-03-22
After messing around a bit in my Nvidia Server settings, I didn't know that changes did not take effect untill you clicked save to X configuration. Well, even though I never saved any of my changes, I restarted my computer, and I clearly saw my tv and monitor both display POST. They then both displayed the Xubuntu loading screen, then when X started it went back to just my monitor. Well, after that I went to Applications -> Accessories -> Screens and Graphics... saw the little thingy on my mouse pointer show that something was loading and... that was it! Nothing! It's been like that ever sense. I cannot open my Screens and Graphics! I also tested other programs to see if I was having the issue with anything else. I also cannot open Frostwire. When I enter the  following command in terminal:

```
sudo displayconfig-gtk

```

I get:

Traceback (most recent call last):
  File "/usr/bin/displayconfig-gtk", line 75, in <module>
    app = DisplayConfig(options)
  File "/usr/lib/python2.5/site-packages/displayconfiggtk/DisplayConfig.py", line 190, in __init__
    debug_scan_pci_filename=self.options.pcitable)
  File "/var/lib/python-support/python2.5/displayconfigabstraction.py", line 392, in __init__
    self._finalizeInit()
  File "/var/lib/python-support/python2.5/displayconfigabstraction.py", line 411, in _finalizeInit
    self.setLayout(gfxcard._getDetectedLayout())
  File "/var/lib/python-support/python2.5/displayconfigabstraction.py", line 965, in setLayout
    gfxcard.setLayout(XSetup.LAYOUT_CLONE)
  File "/var/lib/python-support/python2.5/displayconfigabstraction.py", line 1177, in setLayout
    screen._resyncResolution()
  File "/var/lib/python-support/python2.5/displayconfigabstraction.py", line 1854, in _resyncResolution

    self.gfx_card.setup.getPrimaryScreen()._resyncResolution()
  File "/var/lib/python-support/python2.5/displayconfigabstraction.py", line 1810, in _resyncResolution
    (preferred_width,preferred_height) = self.getAvailableResolutions()[-1]
IndexError: list index out of range


What's wrong?!:confused:

---

### Post by mikeyphi on 2008-03-23
Try this:
Open a terminal and enter:

sudo dpkg-reconfigure -phigh xserver-xorg

you will get a lot of text with a question at the end of each section - accept the default answer unless you know better! When finished reboot. You should see at least a default screen resolution but should now have the option of opening 'Screens and Graphics' to set the required resolution.

---

### Post by whoscheesemine on 2008-03-23
Doing that gave me this:

xserver-xorg postinst warning: overwriting possibly-customised configuration
   file; backup in /etc/X11/xorg.conf.20080323135006


I have a driver installed with envy would that cause a problem?

---

### Post by mikeyphi on 2008-03-23
> **whoscheesemine said:**
> Doing that gave me this:

xserver-xorg postinst warning: overwriting possibly-customised configuration
   file; backup in /etc/X11/xorg.conf.20080323135006


I have a driver installed with envy would that cause a problem?

The only problem could be that (depending on what answers you gave) you might have to reinstall the driver.

---

### Post by whoscheesemine on 2008-03-25
Okay, I hate to bump this, but seriously, no one has an answer? Now, I know there's a lot of smart people on this board.

---

