---
title: "Add a &quot;normal&quot; console login?"
date: 2007-06-26
forum: Absolute Beginner Talk
---

### Post by _rcb_ on 2007-06-26
Hi all!

I was wondering if someone could tell me how to add a basic console login to the GDM login manager? I need something that will take me to a plain-text no-framebuffer console with no X-server running. Ctrl-Alt-F2 won't do it, as X is still running in the background (and the framebuffer console in Ubuntu won't display on my video card without the driver loaded).

Also, is it possible to set a root password (by typing "sudo passwd root") without breaking anything else? I don't care if the graphical login shows it as an option, but I do want to be able to open a root console or virtual terminal...

---

### Post by Nekiruhs on 2007-06-26
Well, you can select recovery mode at the GRUB menu, this presents you with a text only, no X, root console.

---

### Post by _rcb_ on 2007-06-26
Oh, thanks. My GRUB wasn't installed by the Ubuntu installer (the computer is triple-boot), so I didn't see that option in the menu.

I see that /boot/grub on the Ubuntu partition still has the (unused) menu.lst file in it with that option, so I can just copy / paste that into the other one...

---

