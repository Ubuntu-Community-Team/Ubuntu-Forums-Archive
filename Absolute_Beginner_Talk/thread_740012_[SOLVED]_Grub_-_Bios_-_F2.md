---
title: "[SOLVED] Grub - Bios - F2"
date: 2008-03-30
forum: Absolute Beginner Talk
---

### Post by N1N31NCHN41L5 on 2008-03-30
I wanted to go into ny bios and put usb devices before hdd so it will load off a usb drive if i wanted to before running straight to the internal. But with the grub I cant access F2 before the grub loads and cant get into F2 bios option either when starting either windows or ubuntu. Does anyone know how to do a F2 to change bios after the grub is installed????

---

### Post by Daveth on 2008-03-30
you should be hitting the bios command key strokes well before grub pops up, just as the pc is booting. Remember it is a low level system, so nothing fancy should be loading.

---

### Post by Dr Small on 2008-03-30
GRUB loads after the BIOS POST screen, so you should be able to access the BIOS Setup Utility by pressing the correct key to enter the Setup.

---

### Post by N1N31NCHN41L5 on 2008-03-30
> **Daveth said:**
> you should be hitting the bios command key strokes well before grub pops up, just as the pc is booting. Remember it is a low level system, so nothing fancy should be loading.

ive tried hitting F2 as the comp is powering up and didnt get it - bad timing on my part????

---

### Post by bumanie on 2008-03-30
Don't know about your mobo, but on mine I hit the delete key to enter bios. This is way before grub loads, straight after the memory test and the recognising of hard drives. I think you need to hit your F2 key much earlier.

---

### Post by N1N31NCHN41L5 on 2008-03-31
> **bumanie said:**
> Don't know about your mobo, but on mine I hit the delete key to enter bios. This is way before grub loads, straight after the memory test and the recognising of hard drives. I think you need to hit your F2 key much earlier.

Finally got the F2 to work - just cant get the dern comp to boot off the USB yet for some crazy reason even though it's set up to run that way first.

---

### Post by Zralou on 2008-03-31
Do you have a bootable file on the USB drives root?, if its inside of a folder on the drive BIOS won't see it and ignore the drive.

Sara Lou

---

### Post by N1N31NCHN41L5 on 2008-03-31
> **Zralou said:**
> Do you have a bootable file on the USB drives root?, if its inside of a folder on the drive BIOS won't see it and ignore the drive.

Sara Lou
I reformatted the USB to DOS and installed Back Track Linux. BTL said it was installing to the root drive.

---

