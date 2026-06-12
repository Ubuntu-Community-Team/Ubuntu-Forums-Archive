---
title: "Cannot get to BIOS"
date: 2007-08-04
forum: Absolute Beginner Talk
---

### Post by Eldar11 on 2007-08-04
when booting my Intel Pentium III coppermine will not give the option to go to BIOS, it just goes straight to the grub loader and boots into Ubuntu, is there any way to fix this, or am 
I stuck not being able to get into bios?

---

### Post by diatribe on 2007-08-04
once your computer turns on it starts grub?

---

### Post by taurus on 2007-08-04
When the machine first boots up, press F2 or a del key to get into the BIOS.  You can't get into the BIOS from GRUB menu.

---

### Post by Brunellus on 2007-08-04
> **diatribe said:**
> once your computer turns on it starts grub?
that would be cool--and possible, too, using the LinuxBIOS project--but that's not what we're dealing with here.

to OP:  power up and hit F12 or DEL repeatedly until you come to a BIOS setup screen.  BIOS runs off ROM chips before anything else.

---

### Post by w4ett on 2007-08-04
Here is a listing of the bios access boot keys.....and there are a bunch of them...no two manufacturers use the same keys (or so it seems):

[http://www.michaelstevenstech.com/bios_manufacturer.htm](http://www.michaelstevenstech.com/bios_manufacturer.htm)

It's a pretty interesting page...also has the beep codes listed.

---

### Post by Eldar11 on 2007-08-04
thanks guys
I tried to get BIOS off of grub and it gave me a boot menu, but I was using F1 so I'll try other combo keys.

---

### Post by w4ett on 2007-08-04
Yon have to enter the bios BEFORE the grub menu....Immediately after pushing the power on button, you have to press (sometimes repeatedly) the indicated key or keys to enter the bios (sometimes called Setup)

---

### Post by Eldar11 on 2007-08-04
thank you it worked, but then I had a stupid moment and I set the BIOS password, and now it won't accept the one I set and I cant get into BIOS settings. It is a Dell Dimention 4100 about 4 years old, so I don't know if it has a backdoor password or what.

---

### Post by Steveway on 2007-08-04
Remove the Bios-battery, wait for about half an hour, put the battery back in.
But be careful! Unplug the Pc first.

---

### Post by Eldar11 on 2007-08-04
won't that kill all my settings?

---

### Post by Steveway on 2007-08-04
Yup, it will revert the settings to the defaults.

---

### Post by w4ett on 2007-08-04
You can remove the battery, it only takes about 1-2 minutes of no power to reset...also usually there will be a small jumper (refer to your mobo mfgr book or website documentation to show you which one.   This will set the bios back to it's default "safe" setting and zero out the password.  If you have a computer where you are the only user, or in a family situation, give the bios password a miss....more trouble than it's worth.

---

