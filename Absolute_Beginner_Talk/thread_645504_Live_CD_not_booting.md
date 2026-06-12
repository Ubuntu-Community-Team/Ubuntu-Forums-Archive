---
title: "Live CD not booting"
date: 2007-12-20
forum: Absolute Beginner Talk
---

### Post by littledude565 on 2007-12-20
Every time i try and boot i get this screen and nothing then happens??? i  have tried many discs

---

### Post by shadow-of-sin on 2007-12-20
Hmm...your CD might be corrupted. Did you check the MD5 sum of the image you downloaded? Also, did you burn the disc at a low speed?

---

### Post by overdrank on 2007-12-20
> **littledude565 said:**
> Every time i try and boot i get this screen and nothing then happens??? i  have tried many discs

Hi and I just recently received that type of error and it turn out to be replacing the cd drive. Have you checked the cd for errors and [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
You can also try when you reach the screen to start/install ubuntu press F6 and edit the kernel line and remove quiet splash and add break=top before the -- then press enter. When you recieve the error again type modprobe piix then hit enter and then type exit then hit enter again this will hopefully continue the livecd to boot.

---

### Post by littledude565 on 2007-12-20
hi the CD's are fine i got them from Connacol and used them before the one i made myself works since i used it before aswell

---

### Post by littledude565 on 2007-12-20
Trying now ^^

---

### Post by littledude565 on 2007-12-20
that didnt work but just now i unpluged the DVD-RW and Floppy and im into Ubuntu posting but if i install it would it work with the DVD-RW drive?

---

### Post by littledude565 on 2007-12-20
bump

---

### Post by shadow-of-sin on 2007-12-20
Try only unplugging the floppy disk drive (as the screenshots you posted give an fd0 error)

I think the floppy drive will still work if you plug it in after the installation (as on my installation the floppy drive is still in the fstab even though I dont have one!)

---

