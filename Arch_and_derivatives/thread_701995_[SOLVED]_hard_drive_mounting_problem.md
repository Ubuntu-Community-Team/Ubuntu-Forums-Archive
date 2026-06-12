---
title: "[SOLVED] hard drive mounting problem"
date: 2008-02-19
forum: Arch and derivatives
---

### Post by JohnnyBoy022 on 2008-02-19
hey everyone, I just installed arch on my laptop. I wanted to install on my external usb hard drive. I unplugged my internal hard drive (with windows) on it for the install, since I was kind of paranoid about ruining something. So during the install the only drive was the external which was identified as sda, great. Everything works fine when the internal is not plugged in.

When I have the internal plugged in and try to boot I get the nasty error message about not being able to mount sda and not finding something or other, kernel panic. Obviously the internal is being identified as sda now so it is looking there. How do I change this, so it looks in sdb (the external) to find the stuff to boot? Thanks for the help

---

### Post by dgray_from_dc on 2008-02-19
I'm not sure I understand, are you setting the BIOS to boot from the external drive?  If not, how is your windows drive booting into Linux in the first place?

Anyway, I was thinking, reinstalling GrUB may make things better.  Grub is probably looking for sda.  If you reinstall, it'll probably reconfigure for sdb.

---

### Post by K.Mandla on 2008-02-19
Maybe when the internal is installed, the drives are renamed in a different sequence. In other words, it's finding the internal drive first, labeling it as /dev/sda1 or something, then trying to find the boot information on that drive. But the external has been labeled as /dev/sda2 or something, and so it's technically looking in the wrong place.

Does that make sense?

---

### Post by JohnnyBoy022 on 2008-02-19
Sorry for the misunderstanding, I will try to explain a bit better.

Arch is installed on the external. Windows is installed on the internal. GRUB is installed on the MBR of the external. My BIOS sees the external (where arch is) just fine, and I can get to GRUB. GRUB works fine and I can start booting Arch. About 10 seconds into the Arch boot, I get a message about starting kinit. This is what looks for some "init" file in sda. However, since the external is being mounted as sdb (i believe), it can't find it. So how can I change where this kinit looks for the init file? I think its looking in sda but I want it to look in sdb. Thanks for the help

---

### Post by JohnnyBoy022 on 2008-02-19
> **K.Mandla said:**
> Maybe when the internal is installed, the drives are renamed in a different sequence. In other words, it's finding the internal drive first, labeling it as /dev/sda1 or something, then trying to find the boot information on that drive. But the external has been labeled as /dev/sda2 or something, and so it's technically looking in the wrong place.

Does that make sense?

This makes sense, except I think the file i want is located in sdb. So how do I change where kinit looks for this file, I want to change from sda to sdb?

---

### Post by dgray_from_dc on 2008-02-19
I think you're on the right track for what you want to do, but the file and/or setting you're looking for is beyond my scope of knowledge.  The only advice I can offer is a reinstall with the internal connected.  Sorry I couldn't be of more help.

---

### Post by bwtranch on 2008-02-20
> **JohnnyBoy022 said:**
> Sorry for the misunderstanding, I will try to explain a bit better.

Arch is installed on the external. Windows is installed on the internal. GRUB is installed on the MBR of the external. My BIOS sees the external (where arch is) just fine, and I can get to GRUB. GRUB works fine and I can start booting Arch. About 10 seconds into the Arch boot, I get a message about starting kinit. This is what looks for some "init" file in sda. However, since the external is being mounted as sdb (i believe), it can't find it. So how can I change where this kinit looks for the init file? I think its looking in sda but I want it to look in sdb. Thanks for the help
I can almost get my arms around this one, but not quite. I can't figure out why it wants to look at sda. Hmmm, probably gets detected at startup. Ah, well ok, you could disable auto hardware detection. I'll bet that's what it is. There are several things that would fix this. Depending. What does ```
nano /etc/fstab
```look like?

---

### Post by K.Mandla on 2008-02-20
> **JohnnyBoy022 said:**
> This makes sense, except I think the file i want is located in sdb. So how do I change where kinit looks for this file, I want to change from sda to sdb?
You might be able to adjust the kernel boot line to look for the root drive elsewhere. It might be something like 
```
root=/dev/sdXY
```
I'm not really sure though. I'm having a hard time wrapping my brain around the issue right now. Please stand by. ... :D

---

### Post by JohnnyBoy022 on 2008-02-20
K. Mandla, I messed around with it a lot and your fix was the one that worked although I eventually figured it out myself. Thanks for the help though, marked as solved.

---

