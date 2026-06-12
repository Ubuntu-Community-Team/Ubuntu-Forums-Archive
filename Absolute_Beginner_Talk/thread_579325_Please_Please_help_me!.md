---
title: "Please Please help me!"
date: 2007-10-18
forum: Absolute Beginner Talk
---

### Post by Ionamay on 2007-10-18
I installed Ubuntu a few days ago, and I'm having loads of problems. Everything keeps not responding, even opening my home folder causes it to stop responding and I can hardly do anything without having nothing left to do but switch the computer off at the wall, it's that annoying. Can anyone help me?

---

### Post by PmDematagoda on 2007-10-18
Could you please post the specifications of your computer?

---

### Post by Officer Dibble on 2007-10-18
> **Ionamay said:**
> I installed Ubuntu a few days ago, and I'm having loads of problems. Everything keeps not responding, even opening my home folder causes it to stop responding and I can hardly do anything without having nothing left to do but switch the computer off at the wall, it's that annoying. Can anyone help me?

1. What are the specifications for your computer? (Just the basics, CPU, Memory, Hard Drive size)

2. Boot from your Live CD, (ie, not hard drive install) does that work okay?

3. Are you, or are you attempting to Dual Boot with XP/Vista, etc?

4. When you installed Ubuntu did you have two partitions? an EXT3 partition and a Swap partition? Do you know how large each one is? 

5. How much memory do you have in your computer? When you first boot from the Live CD, on the menu there is an option to perform a memory test, please run that.

---

### Post by bapoumba on 2007-10-18
Moved to Absolute Beginner Talk.

---

### Post by Ionamay on 2007-10-18
494.5 memory, 2.66ghz, 71.9 hard drive size
The live cd works, I'm not dual booting
the swap partition is 1.4gb, ext3 is 71.9gb.

---

### Post by Officer Dibble on 2007-10-18
Is this a newly built computer?

Would it be a problem to download Ubuntu again, write it to another disc and reinstall? On my first attempt at installing Ubuntu I had issues with core systems and found this to be the source of the problem... not Ubuntu, but the disc or the way the disc was written.

When writing to the disc, write at a slower speed, maybe 18x or 24x.

Hope it works out for you... but if it doesn't then report back and more experienced guys will have better suggestions. :)

---

### Post by Ionamay on 2007-10-18
I ordered one of the live cds, so I'm pretty sure it was okay...

---

### Post by mramsey on 2007-10-18
> **Officer Dibble said:**
> 

5. How much memory do you have in your computer? When you first boot from the Live CD, on the menu there is an option to perform a memory test, please run that.

Did you run the memory test?

---

### Post by kenweill on 2007-10-18
Try adding:

**noacpi acpi=off**

in your kernel options, found in /boot/grub/menu.lst

---

### Post by Ionamay on 2007-10-18
It won't let me do that.

---

### Post by wpshooter on 2007-10-18
> **Ionamay said:**
> I ordered one of the live cds, so I'm pretty sure it was okay...

Even if you got the CD from Canonical, that does not mean that it can not be bad.

Did you check the integrity of the CD by running the verification function that is found on the initial Ubuntu boot screen menu ?

---

### Post by Ionamay on 2007-10-18
I'll try that, thanks. :)

---

### Post by Ionamay on 2007-10-18
I checked the cd and it's fine. I don't know what to do now...

---

### Post by blazerw on 2007-10-18
> **kenweill said:**
> Try adding:

**noacpi acpi=off**

in your kernel options, found in /boot/grub/menu.lst

Try:
```
sudo nano /boot/grub/menu.lst
```

Or at bootup, choose Ubuntu from the menu and press "e" to edit the line, then add ```
noacpi acpi=off
```, then, I think you press "b" to boot that.

Does anybody know if the liveCD uses "noacpi acpi=off"?

---

