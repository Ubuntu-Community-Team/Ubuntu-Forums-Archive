---
title: "Grub does not install with 7.04"
date: 2007-05-22
forum: Absolute Beginner Talk
---

### Post by dhongyt on 2007-05-22
Hi, I'm trying to install Ubuntu 7.04 on my new system, it installs and everything but when it finishes GRUB does not boot at all. Did anyone encounter this? How did you solve it?

---

### Post by powder on 2007-05-22
Do you have more than one hard drive?  If this is the case, the BIOS may be looking at the MBR on the wrong drive!

---

### Post by phidia on 2007-05-22
More specifics please. How many hard drives in your system, and if there are more than one which drive are you trying to install to? What exactly happens when you reboot after install? e.g boots to windows, blank screen, etc?

---

### Post by dhongyt on 2007-05-23
I only have one harddrive, after the install it tells me to take out the CD which I do, then it just loads up Windows instead of going to a GRUB screen.

---

### Post by dhongyt on 2007-05-23
Any ideas?

---

### Post by dpar on 2007-05-23
I don't know how you would check from windows, but could you have maybe installed grub to your linux root partition instead of the MBR?

---

### Post by dhongyt on 2007-05-23
Haha I just built this computer, I forgot that I had protection for the boot sector.

---

### Post by phoenix23 on 2007-05-23
> **dhongyt said:**
> Haha I just built this computer, I forgot that I had protection for the boot sector.

I'm having the same problem on a fresh hard drive as well.

Since this is the ABSOLUTE beginners forum, would you mind telling me how you turn off the protection?

---

### Post by dhongyt on 2007-05-24
I just had to go into the bios to disable mine. Hope you can find it cause we might have different motherboards. I have a MSI P6N. Let me know if I can help you more.

---

### Post by phoenix23 on 2007-05-24
I've gotten into BIOS, but the only options I see for (hd0) are AUTO and 500 GB. I see a boot sequence, but that doesn't seem to do much either.

What exactly is the option you have to turn off?

Thanks

---

### Post by dhongyt on 2007-05-24
Well its going to be different for different motherboards. Which one do you have? I have a MSI P6N and there was an option to turn off Boot Sector Protection for me.

---

