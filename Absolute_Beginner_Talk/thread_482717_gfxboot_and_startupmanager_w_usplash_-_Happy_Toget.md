---
title: "gfxboot and startupmanager w/ usplash - Happy Together?"
date: 2007-06-24
forum: Absolute Beginner Talk
---

### Post by coldstatue on 2007-06-24
I just got gfxboot working, and I'd like to change the bootsplash, but am concerned it will mess with my gfxboot screen. There are GRUB options in the startupmanager, and I'm not sure I want to fiddle with it. Is anyone running all of these at once? Any special procedures required, or can I just go ahead and install usplash and startupmanager with no worries?

Thank you

---

### Post by ParkingBrake on 2007-06-25
I myself use startupmanager with no problems.  It works great for GRUB, usplash, all that stuff.  But since it is messing with the startup you should be careful.

---

### Post by coldstatue on 2007-06-26
are you using gfxboot as well? If not, I am going to wait. My boot looks pretty cool right now anyways. Just getting into really tricking everything out.

---

### Post by OzzyFrank on 2008-01-17
Not sure I understand the question, but here goes. If you are wanting to change the bootsplash in GfxBoot, just edit **menu.lst** and change the image, like you would with GRUB. If you are used to [COLOR="Indigo"]**Startup-Manager**[/COLOR], well that's only good for GRUB, and the Usplash that appears after the boot menu. This gets uninstalled when you remove GRUB, but i reinstalled it without issue. So if you are asking can one change the usplash without effecting GfxBoot, yeah sure, and you can change it via **[COLOR="#4b0082"]usplash-switcher[/COLOR]** or [COLOR="#4b0082"]**startup-manager**[/COLOR] (just ignore the GRUB part as it is useless after uninstalling GRUB and replacing it with GfxBoot).

---

