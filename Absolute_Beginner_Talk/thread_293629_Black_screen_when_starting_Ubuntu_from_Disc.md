---
title: "Black screen when starting Ubuntu from Disc"
date: 2006-11-05
forum: Absolute Beginner Talk
---

### Post by Snorglorf on 2006-11-05
Whenever I start Ubuntu from the disc on my old computer that I'm trying to install it on, I get a black screen lockup, with the _ cursor in the top left, not blinking like it's supposed to. Whenever I start in Safe graphics mode, it comes up with an error, I'll check what it says in a minute. I also tried installing Xubuntu, but it doesn't come up with the GUI when I boot it, after I log in (It is installed).

The specs are:

1GHz Celeron
256MB RAM
Nvidia Geforce 5200
40GB Hard drive.


What can I do to fix this? Or is Ubuntu incompatible with my system?

---

### Post by highneko on 2006-11-05
What installation cd are you using? PC (Intel x86) desktop CD?

---

### Post by Snorglorf on 2006-11-05
> **highneko said:**
> What installation cd are you using? PC (Intel x86) desktop CD?

Yeah, should I download the alternate?


Will downloading 6.10 make a difference? It might be missing a graphics driver or something like that. I'm installing XP on there right now, and maybe it'll boot from the disc with Windows installed, as opposed to an empty hard drive.

---

### Post by DraeLee on 2006-11-05
check the disk for errors might be a bad download.  might need to redownload the disc (just a thought)

---

### Post by Snorglorf on 2006-11-05
> **DraeLee said:**
> check the disk for errors might be a bad download.  might need to redownload the disc (just a thought)

Did I not mention that it's not the disc? Well, it works on the computer I'm currently using.

---

### Post by DraeLee on 2006-11-05
well the specs have nothing to do with it really.  ive wiped out the whole hard drive by accident and reinstalled both.  what i did was make up separate partitions for the /, the swap, and the boot and i put 20g for the windoze.  This way worked for me not sure what method you used.  but i dual booted mine.

---

### Post by Snorglorf on 2006-11-05
> **DraeLee said:**
> well the specs have nothing to do with it really.  ive wiped out the whole hard drive by accident and reinstalled both.  what i did was make up separate partitions for the /, the swap, and the boot and i put 20g for the windoze.  This way worked for me not sure what method you used.  but i dual booted mine.

I wiped the hard drive with fdisk (Windows had a virus and wouldn't pick up the CD drives), then booted from the Ubuntu disc without installing anything. Ubuntu wouldn't boot to the "live off CD" thing. That's where my problem was.

---

