---
title: "gusty hates me"
date: 2008-02-23
forum: Absolute Beginner Talk
---

### Post by kINTO_O on 2008-02-23
I've been trying to install gusty ( 7.10) and I can't do it because ubuntu does not recognize my monitor.  I've gone in to tell it exactly what I have, but my monitor isn't in the list.  When I try to install with the non regular settings (safe gfx settings i think it's called ), I just get some text display and my diskdrive stops spinning and the screen just sits there.    How can I get things to work ???

Monitor: Dell SP 2008 WFP 20 inch
GFX: NVIDIA 8400

thanks : )

---

### Post by harold4 on 2008-02-23
So when you pop in the live cd and boot with the first option, what happens?

---

### Post by kINTO_O on 2008-02-23
an x mouse cursor appears on the screen.. i wiggle it around and i get a prompt saying that my monitor could not be found and it lets me choose the correct driver to use

---

### Post by harold4 on 2008-02-23
Interesting.  I have done installs with the same monitor.  I wonder if you just have a bad burn. 

Try re-burning the .iso at the slowest setting, or test the disk for errors.

---

### Post by kINTO_O on 2008-02-23
i figured before i reburned, i'd try and again with all the usb things taken out of the monitor.. still no luck.. and to top it off... the system had something weird happen... didn't get any splash at all , and the computer started making continuous system beeps

---

### Post by kINTO_O on 2008-02-23
1) i redownloaded gusty
2) i did a checksum test
3) i tried to boot again
4) got same error ... tried different drivers and res to see if anything would work.. nothing
5) clicked ok and it brought me to a black screen w/ some text
6) disk stop spinning after displaying Running local Boot Scripts (/etc/rc.local) [OK]

^-- i go directly to step 6) when i choose safe graphics mode

---

### Post by harold4 on 2008-02-23
When you reburned, did you burn it at 1X?  Also, did you boot the cd and select option "Test disk for error?"

---

### Post by uberlube on 2008-02-23
did you try adding "vga=?" into the boot process? Or pressed F4 i think it is to choose the native resolution?

---

### Post by harold4 on 2008-02-23
> **uberlube said:**
> did you try adding "vga=?" into the boot process? Or pressed F4 i think it is to choose the native resolution?

Good call

---

