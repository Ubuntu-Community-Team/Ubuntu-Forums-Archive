---
title: "Stuck in the prompt"
date: 2007-07-12
forum: Absolute Beginner Talk
---

### Post by themaskswewear on 2007-07-12
I installed Ubuntu using the alternate CD image. Now all it does it boot to the prompt. "Ubuntu, kernel 2.6.20-15-generic"  It will not boot to cd's anymore and I have no clue what to do. Please help!

I am completely new to this I was trying to fix the computer but now I can't even get to the Ubuntu OS

---

### Post by Inxsible on 2007-07-12
Did you by any chance install the server version instead of the desktop version ?

The server version does not have a GUI, it only has a CLI

---

### Post by bradmayne on 2007-07-12
try using this command:    startx

let me know what happens.

---

### Post by themaskswewear on 2007-07-12
i'm in grub.  i apologize for the ignorance, but this is what i see

grub> 

so i type in startx

grub> startx

Error 27: Unrecognized Command.



How do I boot to the CD drive?  I would like to re-attempt the installation, and get back to XP if it doesn't work. Right now I'm stuck in the water.  Thanks!

---

### Post by Outrunner on 2007-07-12
What do you mean, you can't get into the OS? Did you try pressing Enter while having Ubuntu, kernel 2.6.20-15-generic highlighted ?

---

### Post by themaskswewear on 2007-07-12
when I type startx it says 

Fatal server error: 
no screens found
XIO: fatal IO error 104 (connection reset by peer) on X server ":0.0"
after 0 requests (0 known processed) with 0 events remaining.

---

### Post by Inxsible on 2007-07-12
See post # 2 again

---

### Post by TheOtherShoe on 2007-07-12
Your BIOS might be set up so that booting from the hard drive takes precedence over booting from the CD. When you first boot up you should see a message go by quickly that says something like:
```
Press F2 for BIOS settings, press ESC for boot options
```
The exact keys vary from computer to computer. See if you can find out what those keys are, press one of them repeatedly while the computer is booting up. If you get the boot options you can tell it to boot from the cd; if you get the BIOS settings there should be an option somewhere to change the order of precedence for booting - just boot the cd drive at the top.

If you can't find out what keys you need to access these settings, there is another option. When you first turn your computer on, start mashing as many keys as you can until you get dumped into a settings screen. The function keys are good bets.

Good luck!

---

### Post by themaskswewear on 2007-07-12
I've tried that several times...

I select to boot from "IDE CD-ROM Device" and the machine beeps twice and says

"strick F1 to retry boot, F2 for setup utility"

It does this with the LIVE CD, the alternate CD, and the XP Recovery Disk.


Can I boot to a CD from GRUB?

---

### Post by Inxsible on 2007-07-12
> **themaskswewear said:**
> I've tried that several times...

I select to boot from "IDE CD-ROM Device" and the machine beeps twice and says

"strick F1 to retry boot, F2 for setup utility"

It does this with the LIVE CD, the alternate CD, and the XP Recovery Disk.


Can I boot to a CD from GRUB?
Dont get ahead of yourself. Grub comes in later. 

When the computer is starting up, hit the F2 key. Go into the BIOS and change the boot sequence to boot from CD first then HDD. Make sure you do a save and exit(F10 -- in most cases) and NOT just an exit(Esc).

At the bottom of the screen, it will list all the options. See what is yours for 'Save and Exit'

Then reboot.

---

