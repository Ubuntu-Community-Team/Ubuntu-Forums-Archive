---
title: "Adding new hardware?"
date: 2007-08-24
forum: Absolute Beginner Talk
---

### Post by chrome307 on 2007-08-24
I just wanted to know if it would be safe to exchange my GFX card with a new one?

Will Ubuntu automatically detect this new card and install the drivers?

Moving from an ATi card to a Nvidia card.

OR do I need to reinstall the OS completely?

---

### Post by Seisen on 2007-08-24
If you replace your graphics card you are going to need to reconfigure your xorg.conf. To do that put this in the terminal.

```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by chrome307 on 2007-08-24
Okay, but will it just boot up with a default resolution so that I can get back into my desktop to make this change?

---

### Post by Seisen on 2007-08-24
Most likely it will tell you that xorg is all messed up so you have two options

1. Boot into recovery mode and enter the command or 
2. Change you xorg.conf manaully to "vesa" then restart and download the drivers if needed.

---

### Post by chrome307 on 2007-08-24
I'm not sure how to Boot into Recovery mode (onscreen prompt? when booting up initially) - so can I just reconfigure it now to VESA and then rebooot?

I'm pretty sure that's what you have already said, but I just wanted clarification.

Thanks

---

### Post by igknighted on 2007-08-24
Change your xorg driver by modifying xorg.conf to vesa (instead of ati/radeon/fglrx/whatever you use) BEFORE you swap the cards.  Then run the reconfigure.  Then reboot with the new xorg.conf.  This is all to clear the ATI specific stuff out.  Then install the nvidia drivers and enable them and you should be good to go.

NOTE: always backup xorg.conf when you make a change, just in case.

---

### Post by Seisen on 2007-08-24
You can do that, when you boot into grub you have two kernel options the regular one and one that will say recovery mode,

---

### Post by A3sthetix on 2007-08-24
When booting up, press tap the ESC button. This will bring up your options to run recovery mode. Then do what the gurus are telling you.

---

### Post by chrome307 on 2007-08-25
Unfortunately I made a mess of it, I did follow the instructions as best as I could but my could not get a display with my GFX card, I guess it was a spare for a good reason LOL

Anyway I reinstalled the OS.

---

