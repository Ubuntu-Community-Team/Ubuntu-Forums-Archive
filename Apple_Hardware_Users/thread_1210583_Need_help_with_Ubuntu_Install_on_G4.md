---
title: "Need help with Ubuntu Install on G4"
date: 2009-07-11
forum: Apple Hardware Users
---

### Post by P_ReeD on 2009-07-11
Hi, My name is Preston, and this is my first undertaking of installing Linux. I am having problems getting my G4 to read the Install Disk. I downloaded 8.04 Minimum Install for 64-Bit Power PCs. The installer program worked fine on My g5 I just Typed "cli" and it wen directly to the installer program, prompting me to selct language etc. My G4 is being a little bit more of a pain. I type in "cli" and then get prompted to OpenFirmware. I then Type "boot cd:,\\:tbxi" It then Changes to a white screen with black text and then said the following:


Loading ELF


CLAIM FAILED



Any ideas anyone? Did I download the wrong version I thought all of G4s and G5s were 64-bit....

---

### Post by wojox on 2009-07-11
Step 1 - Get the image for Ubuntu 8.04.1 for PowerPC... You can go here
[http://cdimage.ubuntu.com/ports/releases/hardy/release/](http://cdimage.ubuntu.com/ports/releases/hardy/release/)

Step 2 - Burn that image to a disk when it is finished downloading and reboot your iBook with the disk in the drive. Holding "c" after you hear the bootup chime.

Step 3- Do not boot it right away you need to type in this command line. "live-nosplash-powerpc modprobe ide-core video=radeonfb:1024x768-24@60"

Step 4- Patience is key, you must wait for it to load because of course it is a liveCd.

Step 5- If it loaded, Thats the hardest part, now all you have to do is install it. Which is very simple, there is a shortcut on the desktop when Ubuntu Loads.

---

### Post by tiresia on 2009-07-11
> **P_ReeD said:**
> 
Any ideas anyone? Did I download the wrong version I thought all of G4s and G5s were 64-bit....
Only G5 are 64-bit. PowerPC G4 are 32-bit

---

