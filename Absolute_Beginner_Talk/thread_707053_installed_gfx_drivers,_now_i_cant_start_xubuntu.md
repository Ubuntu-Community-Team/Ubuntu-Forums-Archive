---
title: "installed gfx drivers, now i cant start xubuntu"
date: 2008-02-25
forum: Absolute Beginner Talk
---

### Post by cnstarz on 2008-02-25
i installed my nvidia drivers with envy, and was told to reboot my machine.  i have an 8800gtx and now when it boots, i get a low-resolution screen(800x600) where i change the resolution and the drivers for the card.  however, when i change the drivers to Nvidia 8 Series, and the resolution back to 1024x768, all it does is black out and freeze.   i cant do anything.  is there a way to undo the envy thing?  everything was working fine using stock drivers before i did the envy install.

sorry if this has been asked before. :(

---

### Post by LeAstrale on 2008-02-25
as you probarly noticed in envy before creating this thread there is a option for nvidia driver uninstall.. just use that one and then try with the "real" nvidia driver from nvidia.com and let it automatically create a Xorg for you at the end

---

### Post by oedha on 2008-02-25
have you enable the restricted driver ?
(i also failed on envy on nvidia 7000m then i just install nvidia driver......)

---

### Post by cnstarz on 2008-02-25
> **astral-1 said:**
> as you probarly noticed in envy before creating this thread there is a option for nvidia driver uninstall.. just use that one and then try with the "real" nvidia driver from nvidia.com and let it automatically create a Xorg for you at the end

i cant do that because i cant even get to the desktop.  as soon as i choose the xubuntu os from grub, the screens turns off for a few seconds, then comes back on with an X-shaped cursor and a pop up that says, "Ubuntu is running in low Graphics Mode".  I click "configure" and the Screen Tab already says " Model: Plug and Play" with a resolution of 800x600 @ 61khz.  The Graphics tab says, "Driver: vesa-Generic VESA-Compliant video card".

I change the Monitor Model(in the Screen tab) to that of my monitor; Sony SDM-HS73", and then i switch to the Graphcis Card tab and choose the "Nvidia 8 Series" driver.

Then at the main Screen, whenever I Choose "Test" or "OK", the screen just turns black and becomes unresponsive, and just sits there until i reboot.

> **oedha said:**
> have you enable the restricted driver ?
(i also failed on envy on nvidia 7000m then i just install nvidia driver......)

yes, i enabled restricted driver.

---

