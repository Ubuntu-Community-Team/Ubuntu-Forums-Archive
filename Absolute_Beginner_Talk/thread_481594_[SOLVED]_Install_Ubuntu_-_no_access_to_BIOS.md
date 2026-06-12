---
title: "[SOLVED] Install Ubuntu - no access to BIOS"
date: 2007-06-22
forum: Absolute Beginner Talk
---

### Post by ubername on 2007-06-22
Hi

I have an old laptop (given by a previous employer which went bust). It has win98 on it. When booting I don't get the BIOS screen to allow me to F2 to set the CD as a bootable drive. I would like to put Ubuntu on i.. Any clues? I have a bootable  Ubuntu CD 

(When I boot into Win 98 I have full internet access, and the machine has a floppy drive )

---

### Post by oilchangeguy on 2007-06-22
> **ubername said:**
> Hi

I have an old laptop (given by a previous employer which went bust). It has win98 on it. When booting I don't get the BIOS screen to allow me to F2 to set the CD as a bootable drive. I would like to put Ubuntu on i.. Any clues? I have a bootable  Ubuntu CD 

(When I boot into Win 98 I have full internet access, and the machine has a floppy drive )

when all else fails. hold down the esc key when you start the computer. you'll get a keyboard error, and be prompted to enter setup (the bios). and you can make the cd drive the first boot item.

---

### Post by Jimmyfj on 2007-06-22
I'd say, depending on the make and model of the laptop you should be able to get a boot menu by hitting the F12 key and from there select the cd as 1'st boot device

---

### Post by logos34 on 2007-06-22
here's a list that might help you get into the bios on that machine:
**[http://www.brunolinux.com/01-First_Things_To_Know/Change_BIOS_Settings.html](http://www.brunolinux.com/01-First_Things_To_Know/Change_BIOS_Settings.html)**

---

### Post by ubername on 2007-06-22
Thankyou both. I have tried rebooting the laptop (it's a Dell Lattitude model No. PPL from about 2000) whilst holding down the 'esc' key (lots of beeps but still boots straight into win98) and then rebooting and holding down the F12 key, same thing. any more ideas?

---

### Post by oilchangeguy on 2007-06-22
before we go any farther. please provide your machines specs. it may not even support ubuntu.

---

### Post by MinstrelBoy on 2007-06-22
Try this, found it on Google
Dell is usually keep tapping F2 as soon as you turn it on.
or maybe F12 which gives you a boot menu, then press C for boot to CD 

ALR PC/PCI - F2
ALR PC/non-PCI - CTRL+ALT+ESC
AMD - F1
AMI - DEL
AWARD - CTRL+ALT+ESC
AWARD - DEL
DTK - ESC
PHOENIX - CTRL+ALT+ESC
PHOENIX - CTRL+ALT+S
PHOENIX - CTRL+ALT+INS
ACER - F1,F2,CTRL+ALT+ESC
AST - CTRL+ALT+ESC,CTRL+ALT+DEL
COMPAQ - F10
COMPUSA - DEL
CYBERMAX - ESC
DELL 400 - F3
DELL 400 - F1
DELL DIMENSION - F2 or DEL
DELL INSPIRON - F2
DELL LATITUDE - Fn+F1 (while booted)
DELL LATITUDE - F2 (on boot)
DELL OPTIPLEX - DEL
DELL OPTIPLEX - F2
DELL PRECISION - F2
EMACHINE - DEL
GATEWAY 2000 1440 - F1
GATEWAY 2000 Solo - F2
HP - F1,F2
IBM - F1
IBM EPRO laptop - F2
IBM PS/2 - CTRL+ALT+INS after CTRL+ALT+DEL
IBM THINKPAD - (Windows) Programs-Thinkpad CFG
INTEL TANGENT - DEL
MICRON - F1,F2 or DEL
PACKARD BELL - F1,F2,DEL
SONY VIAO - F2
SONY VIAO - F3
TIGER - DEL
TOSHIBA 335 CDS - ESC
TOSHIBA PROTEGE - ESC
TOSHIBA SATELLITE 205 CDS - F1
TOSHIBA TECRA - F1 or ESC

---

### Post by Xoanan on 2007-06-22
You can also try the DEL key; that works for the Dell Dimension L1000R(Win ME, yech)

---

### Post by ubername on 2007-06-22
> **MinstrelBoy said:**
> Try this, found it on Google
Dell is usually keep tapping F2 as soon as you turn it on.
or maybe F12 which gives you a boot menu, then press C for boot to CD 

ALR PC/PCI - F2
ALR PC/non-PCI - CTRL+ALT+ESC
AMD - F1
AMI - DEL
AWARD - CTRL+ALT+ESC
AWARD - DEL
DTK - ESC
PHOENIX - CTRL+ALT+ESC
PHOENIX - CTRL+ALT+S
PHOENIX - CTRL+ALT+INS
ACER - F1,F2,CTRL+ALT+ESC
AST - CTRL+ALT+ESC,CTRL+ALT+DEL
COMPAQ - F10
COMPUSA - DEL
CYBERMAX - ESC
DELL 400 - F3
DELL 400 - F1
DELL DIMENSION - F2 or DEL
DELL INSPIRON - F2
DELL LATITUDE - Fn+F1 (while booted)
DELL LATITUDE - F2 (on boot)
DELL OPTIPLEX - DEL
DELL OPTIPLEX - F2
DELL PRECISION - F2
EMACHINE - DEL
GATEWAY 2000 1440 - F1
GATEWAY 2000 Solo - F2
HP - F1,F2
IBM - F1
IBM EPRO laptop - F2
IBM PS/2 - CTRL+ALT+INS after CTRL+ALT+DEL
IBM THINKPAD - (Windows) Programs-Thinkpad CFG
INTEL TANGENT - DEL
MICRON - F1,F2 or DEL
PACKARD BELL - F1,F2,DEL
SONY VIAO - F2
SONY VIAO - F3
TIGER - DEL
TOSHIBA 335 CDS - ESC
TOSHIBA PROTEGE - ESC
TOSHIBA SATELLITE 205 CDS - F1
TOSHIBA TECRA - F1 or ESC

Thankyou. Fn+F1 worked. It seems straightforward now, as the F1 button has 'setup' written in blue underneath it!

---

