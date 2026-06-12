---
title: "Live CD leaves me with blank screen"
date: 2008-03-08
forum: Absolute Beginner Talk
---

### Post by doctorbighands on 2008-03-08
Just got my hands on a Sony VAIO laptop. I tried to boot both Gutsy and DSL live CDs, and neither one will go. I've tried vga=771, vga=773, vga=788, and vga=normal, and none seem to work. I get the boot selector screen, I hit enter (with or without boot options), the screen goes black with a small blinking cursor, the CD sounds like it's working on something for awhile, and then it stops, but the screen stays black.

I have no idea what to do. If not even DSL will load, it makes me worried.

EDIT: I tried loading the Gutsy text-based installer CD just to see if I could get SOMETHING to show up on the screen. It gets to the boot selector, I hit enter on "Install Ubuntu in text mode," and the screen goes dark like usual. Not even any CD activity this time.

---

### Post by JoshuaRL on 2008-03-08
Is the CD drive okay?

---

### Post by doctorbighands on 2008-03-08
The drive seems to be functioning properly. I ran a repair CD in it to check for bad sectors on the hard disk, and everything seemed normal.

If there's some other way to check for sure, I'd love to know about it.

---

### Post by doctorbighands on 2008-03-08
I just plopped in a Windows XP installation CD. It seems to be loading fine, except that I discovered something weird: the display doesn't fill the screen! My laptop screen is a 14.1" display, but the actual displayed portion (the good ol' Windows blue screen) is in a box that's about 9" wide by 6" tall, centered within the screen, surrounded by black.

When I boot into the BIOS, it's the same story - shrunken screen. I don't see anything in the BIOS to fix this.

I don't know if this has anything to do with why linux won't boot (I've tried Ubuntu, DSL, Sabayon, Debian, and Knoppix CDs), but I thought I'd bring it up.

I'm looking to eventually resell this machine, so as a last resort, I'd be willing to install Windows on it. If someone could at least help me to get the display to fill the screen, that would be wonderful.

---

### Post by doctorbighands on 2008-03-08
I've tried hooking up an external monitor and booting into the Ubuntu live CD, and it acts the same way as before.

Frustration!

---

### Post by spiderbatdad on 2008-03-08
Possibly a bios config setting. look for a vga option in the bios.

---

### Post by doctorbighands on 2008-03-08
I don't see anything display-related in the BIOS at at all except for being able to change the TV setting to either NTSC or PAL. That doesn't have anything to do with VGA, though.

*whimper*

---

### Post by spiderbatdad on 2008-03-08
You could try turning of PnP in the bios. If you post your bios version, it might be helpful.

---

### Post by basicxman on 2008-07-23
type in 'startx' and press eneter, smame thing happened to me

---

