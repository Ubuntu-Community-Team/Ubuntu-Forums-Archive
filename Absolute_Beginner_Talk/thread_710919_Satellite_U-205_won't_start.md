---
title: "Satellite U-205 won't start"
date: 2008-02-29
forum: Absolute Beginner Talk
---

### Post by joneez on 2008-02-29
Put in a multi session DVD-R waited for it to show up on the desktop then started up Brasero. Put a 1gig XD card with pics and vids from my Fuji Z1 in the 5in1 slot, went to /dev from Brasero, computer locked up and the HD started spinning up FAST! Never heard it spin that fast before. I panicked and shut it down by holding the power button. When I try to restart it the power light comes then the HD light comes on for two seconds then goes off, I hear the HD park and that's it...nothing but a black screen! I've been running Ubuntu only (no dual boot) for three months with no problems 'till now.


Toshiba Satellite U-205, Texas Inst. 5in1 card reader, Core Two Duo, Ubuntu 7.10 (sorry, working from memory and that's all I can remember!)

---

### Post by joneez on 2008-02-29
Bump! I'm stuck. Is this a hardware or software problem?

---

### Post by joneez on 2008-03-04
Yay, it's working (sort of.) Another forum suggested I check internal connections and also try booting with hardware disconnected one at a time. When I took out #2 sdram it fired right up! I then did a format and reinstall of ubuntu 7.10 but it still won't run with both rams installed. The computer seems to run fine otherwise. Do I possibly have a bios problem? Any suggestions?

---

### Post by crjackson on 2008-03-04
> **joneez said:**
> Yay, it's working (sort of.) Another forum suggested I check internal connections and also try booting with hardware disconnected one at a time. When I took out #2 sdram it fired right up! I then did a format and reinstall of ubuntu 7.10 but it still won't run with both rams installed. The computer seems to run fine otherwise. Do I possibly have a bios problem? Any suggestions?

Sounds like you may have a bad stick of memory.  Swap out the one that's working with the one that's not working.  If it won't boot anymore then it's a bad stick.  Swap back to the know good one, and replace the dead one.

If it boots when the sticks are swaped (menaing both sticks are working) then you have other issues.

---

### Post by joneez on 2008-03-04
Sorry, forgot that part. It doesn't matter which stick is in, they both work. Only malfunctions when both are in.

---

### Post by crjackson on 2008-03-04
> **joneez said:**
> Sorry, forgot that part. It doesn't matter which stick is in, they both work. Only malfunctions when both are in.

On your grub menu, you should have an option to run Memtest86.  Test each stick for errors.

Also, if both sticks are installed, how far into the boot process does it get before it stops.  Does it hang while loading Ubuntu, or does it even get that far?  If you can get to the grub menu with both sticks installed, then have them both installed when running memtest86.

If it won't even boot that far with both sticks, it sounds like hardware still.

---

### Post by joneez on 2008-03-04
I'll try the memtest tonight. With both sticks in, I press the power button, the power light comes on then the hard drive light comes on for about 2 sec. then I can hear the drive heads park and that's it.

---

### Post by crjackson on 2008-03-04
> **joneez said:**
> I'll try the memtest tonight. With both sticks in, I press the power button, the power light comes on then the hard drive light comes on for about 2 sec. then I can hear the drive heads park and that's it.

Okay, it's hardware.  No doubt about it.  You probably have a marginal stick of memory that won't work when the other is installed along with it.  Next step is to fully test each stick by it's self and keep your fingers crossed that one of them throws errors to memtest86.  Then you will know for sure.  If neither present any errors, you could have a problem with the PSU, or the Power regulation circuit on the motherboard itself - it could be that it's not getting enough power to run when the other stick is installed.  I wouldn't think that's the problem but it is a possibility.  Let's keep it simple and test the memory out 1st...

---

### Post by joneez on 2008-03-04
Thanks, I'll check it out. Good excuse to upgrade my ram anyway!

---

