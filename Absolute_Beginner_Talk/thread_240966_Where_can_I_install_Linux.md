---
title: "Where can I install Linux?"
date: 2006-08-21
forum: Absolute Beginner Talk
---

### Post by edman2 on 2006-08-21
Can I install ubuntu on a secondary, non-boot drive that I use just for storage in xp? I want to install it on my G drive, and winxp is my C drive. My C and D drives are part of a raid-0 array so I don't want to touch them. 

What are the steps I need to take to install on G now that Ive cleared about 20 gigs from it?

---

### Post by VirtuAlex on 2006-08-21
if you do not want to touch your raid, then most simplest case is to make your G default boot drive and install everything there.

---

### Post by TFX360 on 2006-08-21
Dear Edman2


Ubuntu automatically can use "the lagest amount of free space" option. It will find that 20 gigs. I had windows XP installed first and later Ubuntu. No problems found here. Except for some grub menu changes.


Kind regards,


TFX

---

### Post by edman2 on 2006-08-21
> **VirtuAlex said:**
> if you do not want to touch your raid, then most simplest case is to make your G default boot drive and install everything there.

I make G my default boot drive through the bios correct?

---

### Post by VirtuAlex on 2006-08-21
> **edman2 said:**
> I make G my default boot drive through the bios correct?
That's right

---

### Post by VirtuAlex on 2006-08-21
and one more thing - you better install from alternate CD, because it has option to choose where your boot loader will be installed. Especially if your G is SATA.

---

### Post by edman2 on 2006-08-21
> **VirtuAlex said:**
> and one more thing - you better install from alternate CD, because it has option to choose where your boot loader will be installed. Especially if your G is SATA.

haha you beat me to it, i was just about to ask if I am supposed to use the alternate cd. So do I choose to install the bootloader to the G drive? btw it isn't sata.

---

### Post by kinematic on 2006-08-21
yes...install grub to your primary boot drive.
ubuntu's installer will add an entry for windows.

---

### Post by rowanparker on 2006-08-21
One more thing to note:
There are no drive letters in Linux. It's all hda1, hdb2, sda3, sdb4 etc.
If you need to know what they are, google can help you.

Rowan.

---

### Post by VirtuAlex on 2006-08-21
of course you install bootloader, grub as a matter of fact, to the drive which you are planning to boot from. Otherwise it would either boot nothing if there are no proper boot record, or boot straight back to your "other os" if it has its boot record there.

---

### Post by edman2 on 2006-08-21
> **kinematic said:**
> yes...install grub to your primary boot drive.
ubuntu's installer will add an entry for windows.

That's the confusion I have though. My G drive ISN'T my primary boot drive right now. I'm installing to a second drive that I have some space in...did you mean my primary linux boot drive once I've installed ubuntu on it and changed the bios to boot from G?

---

### Post by edman2 on 2006-08-21
Nevermind, virtualex answered my question. Guess I'll see how the install goes...

---

