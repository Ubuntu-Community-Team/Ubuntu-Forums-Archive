---
title: "Nvidia: Composite Extension not available"
date: 2007-09-04
forum: Absolute Beginner Talk
---

### Post by anandus on 2007-09-04
Hi,

Yesterday I installed Ubuntu/Linux for the first time.
I installed the Nvidia-driver (by first closing gdm, installing nvidia-blabla.run and after starting gdm again). Desktopeffects worked fine, everything was wobbly as can be :P

But then I rebooted and the xserver wouldn't start :(

I loaded the Vesa driver (through dpkg-reconfigure) and started X again, this worked.

Then I installed Envy and ran it.
I uninstalled nvidia-drivers and installed them again. Envy is a very nice piece of work! :)

But now the problem:
When I want to turn on Desktop Effects, I get this error:
"The Composite Extension is not available"

The Nvidia-drivers are there, I can configure them (nvidia settings), so I think the driver is installed okay?

When I go to the terminal and do 'glxinfo | grep "GLX version" it returns 'GLX Version 1.3'.
So GLX is also okay?

I've searched through the forums, but most (if not all) topics with this error were about ATI-cards, not Nvidia.

Anybody knows what I did wrong?

One more thing, though:
The Software Updater says there's one update, compiz-core.
But the update is the same (eg. from: version x.y.z to: version x.y.z), and it&#347; in a loop, as soon as I update, and the software updater reloads the same update is there again. Maybe this is part of the problem?

Any help is certainly appreciated!

(Systemspecs: C2D E6300, 2Gb, 8800GTS320)

---

### Post by afonic on 2007-09-04
Envy for some weird reason disables the composite extension in xorg.conf.

gksudo gedit /etc/X11/xorg.conf

In the bottom you'll see that composite is "Disabled" just make it "Enabled" and it should work.

---

### Post by njknight on 2007-09-04
If its any help my xorg.conf file has the following for my nvidia card

Section "Device"
Identifier "nVidia Corporation MCP51 PCI-X GeForce Go 6100"
Driver "nvidia"
Option "AddARGBGLXVisuals" "True"
Option "RenderAccel" "True"
Option "AllowGLXWithComposite" "True"
Option "backingstore" "True"
Option "TripleBuffer" "True"
Option "DisableGLXRootClipping" "True"
EndSection

and at the end

Section "Extensions"
Option "Composite" "Enable"
EndSection

---

### Post by anandus on 2007-09-04
> **afonic said:**
> Envy for some weird reason disables the composite extension in xorg.conf.

gksudo gedit /etc/X11/xorg.conf

In the bottom you'll see that composite is "Disabled" just make it "Enabled" and it should work.This worked!

Thanks, both of you! I can enjoy my wobbliness again \o/

---

### Post by afonic on 2007-09-04
Have fun with Ubuntu. :)

---

