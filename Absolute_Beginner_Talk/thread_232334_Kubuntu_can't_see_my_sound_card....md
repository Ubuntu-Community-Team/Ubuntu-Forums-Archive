---
title: "Kubuntu can't see my sound card..."
date: 2006-08-08
forum: Absolute Beginner Talk
---

### Post by telegramsam on 2006-08-08
I recently installed Kubuntu on an HP8670C.  It has a PCI sound card that worked with Windows just before I completely formatted the HDD.  

How can I add this card and make it work?  I don't know the exact model of it, since I've completely reformatted windows and Kubuntu can't even see it.  I could pull it out and check if necessary...

---

### Post by davebgimp on 2006-08-08
> **telegramsam said:**
> I recently installed Kubuntu on an HP8670C.  It has a PCI sound card that worked with Windows just before I completely formatted the HDD.  

How can I add this card and make it work?  I don't know the exact model of it, since I've completely reformatted windows and Kubuntu can't even see it.  I could pull it out and check if necessary...

I hate to say it, but pulling it out and supplying a make and model on the card would help because then you can check the hardware support list for sound cards and see what if any issues you might be facing.

[https://wiki.ubuntu.com/HardwareSupportComponentsSoundCards](https://wiki.ubuntu.com/HardwareSupportComponentsSoundCards)

---

### Post by telegramsam on 2006-08-08
Ok--I'll pull it out after work tonight and report back.
Thanks..

---

### Post by telegramsam on 2006-08-08
Ok, so I've pulled the card out the machine.  Here's all the info I could find.  This, by the way is a sound card/modem/joystick input.  I'm guessing that helps explain why Kubuntu won't have none of it!!

Mfr:  SMART Modular Technologies, Inc.
Model:  90079-2

Anyway, I'm looking online now for a driver for linux--on the right track?  I won't know what to do with it when/if I find it...

---

### Post by davebgimp on 2006-08-08
I believe this is the driver you need. From what I gleaned by hitting up the manufacturers website and googling the model #. It's a Riptide.

[http://www.linuxant.com/drivers/riptide/index.php](http://www.linuxant.com/drivers/riptide/index.php)

---

### Post by telegramsam on 2006-08-08
Ok, so I downloaded the .run file to the desktop and double clicked it.  Kate opened and here's the first couple of lines:

#!/bin/sh
# This script was generated using Makeself 2.1.3
CRCsum="3730497981"
MD5="284f7066deea345c5eaeff001a1748dc"

Did that install it?
I tried using the Konsole commands the website suggested, but I couldn't get it to work (I'm a Linux infant)...

---

### Post by telegramsam on 2006-08-09
So; After a bunch of reading and trial and error, I got my modem driver installed--thanks to the link you gave me.  
However, I still don't have sound.  The only driver I could install was an HCF (not Riptide) because the Riptide driver isn't supported under Linux 2.6... Only 2.4 was available.  I think I might just go buy and sound card that is just a sound card and install it.

Any suggestions for brand/model?  Preferably one that is already supported by Kubuntu?...

Thanks for your help, by the way.  That process was an excellent introduction to CLI for me.  (and a harsh lesson in following instructions given in prompts!!)

---

### Post by davebgimp on 2006-08-09
> **telegramsam said:**
> Any suggestions for brand/model?  Preferably one that is already supported by Kubuntu?..

Here's a list of tested sound cards with (K)Ubuntu and the results you can expect from them:

[https://wiki.ubuntu.com/HardwareSupportComponentsSoundCards](https://wiki.ubuntu.com/HardwareSupportComponentsSoundCards)

Personally, I have a SoundBlaster Audigy 2 card and since Breezy, I've had no problems with it. It was immediately recognized and works great. You might need to disable the onboard sound in BIOS first, though.

---

