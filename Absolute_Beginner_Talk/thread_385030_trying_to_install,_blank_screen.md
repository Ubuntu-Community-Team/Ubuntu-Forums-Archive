---
title: "trying to install, blank screen"
date: 2007-03-15
forum: Absolute Beginner Talk
---

### Post by phuefi on 2007-03-15
hey all, 
so, i've just downloaded ubuntu, burnt it to a cd and booted with it.  I get the list of options and when I select the install one I get the ubuntu logo with the orange underneath moving back and forth, then the bar fills up.  However, at this point the screen goes black and has the message "no input detected, please check cable" but i still hear the ubuntu startup sound.  

I'm not really sure what could be going wrong here, the only things I can guess are my graphics card/monitor or my memory.  

I have an x1800xt graphics card with a 19" widescreen tft
the mem I'm using is kingston value 256mb cos my 1GB of corsair is on RMA atm :(

Any help you guys can give would be great, 
cheers

---

### Post by Kobalt on 2007-03-15
You can try to add 'vga=771' at the end of the boot options. To do so, boot normally with the LiveCD in your drive. When you get to the Ubuntu menu (start/install, check disk, etc.) press F6 to reach boot options and simply add [quote]vga=771[/code] at the end of the line then press Enter to boot.

---

### Post by phuefi on 2007-03-16
cheers, i've tried that now but it just does the same thing :confused: the ubuntu logo does have a lot less colours and is bigger when i do that tho
any other ideas?

---

### Post by pbaehr on 2007-03-16
Your problem sounds similar (but not identical) to one I had when trying to install. In your boot options (where you put the vga code before) try adding
```

noapic nolapic

```

---

### Post by PeRKoniX on 2007-03-27
Hi phuefi,

I have exactly the same problem as you describe (with Ubuntu 7.04b).

I see the loading bar. For a couple of seconds I see a blinking pointer in the upper-left corner. After some screen-flickers the screen turns black (and monitor goes automatically in stand-by mode).

I have a `21" EIZO Flexscan F931` on a `NVIDIA Geforce FX5200`

I tried the command-line options described in this thread, adding:

- "vga=771"
- "noapic nolapic"
- "vga=771 noapic nolapic"

Tried those three combinations. None of them gave any result.

I also tried some different resolutions.

During the black screen I can switch to console mode using CTRL+ALT+F1.
All I see is that the installation is hanging on "Running local boot scripts..." and I can't type a thing.
Switching back to graphical mode using CTRL+ALT+F7 is resulting in a black screen again.

I Hope someone can help us with this problem, I can't wait to try the new Ubuntu!

---

### Post by ssachida on 2007-08-03
Have the same problem as PeRKoniX. I can actually type  commands in the console mode, but dont know how to install linux onto the harddrive from there or how to start up gnome.

Help please.

---

