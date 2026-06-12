---
title: "Lost display on laptop"
date: 2007-04-02
forum: Absolute Beginner Talk
---

### Post by cmhill on 2007-04-02
Hey guys, I was messing around with setting up dual display for my laptop at work. My laptop sits in a dock and I have 2 19" flat panels on my desk. I went through the instructions on this site and set up xinerama succesfully by editing the xorg.conf file. So I had both displays working and everything was cool. 

Then I undocked my laptop.

No display on the laptop screen at all. The computer boots up and you can hear it do the ubuntu chime at login, but the screen is black. And by black i mean BLACK for real, no grub, no nothing, not even my DELL bios splash screen.

I plugged an external monitor into the VGA port and got a display there, went back and restored the original xorg.conf file and rebooted. Still no primary display. I used the external monitor to reinstall Unbuntu from the CD. Still no display. I went into the BIOS and reset it to factory defaults. No display. I removed the harddrive from the laptop to totally eliminate the possibility of any software causing this and still no BIOS display or anything. 

So, would you guys agree that at this point I am just looking at hardware failure on the screen itself? If so it seems awfully coincidental that it happened when I was messing with xorg.conf. 

Please somebody confirm for me that what I was doing with xorg.conf could not have caused these problems.

sry for the length and thanks in advance.

---

### Post by compmodder26 on 2007-04-02
Is there a switch on the laptop itself to go between the vga port and the lcd screen?

---

### Post by cmhill on 2007-04-02
The Function F7 or whatever it is (its docked now) is the only toggle I am aware of. But I don't think that functions without windows, and certainly should be a higher level than BIOS.

---

### Post by cmhill on 2007-04-02
:|

---

### Post by cmhill on 2007-04-02
Anyone else have a suggestion before I ship this off to Dell?

---

### Post by compmodder26 on 2007-04-02
Have you actually tried using FN+F7?

---

### Post by cmhill on 2007-04-02
yes

---

### Post by compmodder26 on 2007-04-02
To me, it sounds like a hardware problem.  If it was an Ubuntu issue, I would think that you would still be able to see a BIOS splash on bootup.  For that to not even show up makes me think that it is something with the hardware.

---

