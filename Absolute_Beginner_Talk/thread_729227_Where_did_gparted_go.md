---
title: "Where did gparted go?"
date: 2008-03-19
forum: Absolute Beginner Talk
---

### Post by Nessa on 2008-03-19
I can't find it after I upgraded to Gutsy. Add/Remove shows that I do have it installed. When I do alt+f2 and type gparted, I get a pop up saying that I have to be root.

---

### Post by (((X))) on 2008-03-19
You have to be root.

---

### Post by Nessa on 2008-03-19
I found it. It was just named differently in Gutsy. It just keeps scanning though...

---

### Post by Captainm on 2008-03-19
type gksudo gparted.

---

### Post by Nessa on 2008-03-19
It won't stop scanning. :(

---

### Post by glennric on 2008-03-19
> **Nessa said:**
> It won't stop scanning. :(

I had that problem a few weeks ago.  It turned out it was because I had unplugged the floppy drive and forgot to plug it back in, and hadn't disabled it in the bios.  If I ran grub from a terminal the same thing happened with grub.  It sat on the line "Probing devices to guess BIOS drives. This may take a long time." for a very long time.  For both gparted and grub they did eventually detect the drives.  Check your physical drive setups and bios settings.

---

