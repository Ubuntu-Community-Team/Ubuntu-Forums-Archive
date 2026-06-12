---
title: "Easy question regarding installation"
date: 2006-07-25
forum: Apple PPC Users
---

### Post by UNIVSOUTHFLA on 2006-07-25
Hey every1, with my further research into opensource software, I decided to give Ubuntu another shot. Right now, I have Q (Mac version of QEMU) and downloaded the "desktop" version of Ubuntu. Now I want to install Ubuntu onto Q. Now, when I transfer Ubuntu to make a "home made;)" boot disk, do I transfer the .iso file, or do open the .iso file and transfer all the extracted files onto a disk?

TIA

---

### Post by 3rdalbum on 2006-07-26
> **UNIVSOUTHFLA said:**
> Hey every1, with my further research into opensource software, I decided to give Ubuntu another shot. Right now, I have Q (Mac version of QEMU) and downloaded the "desktop" version of Ubuntu. Now I want to install Ubuntu onto Q. Now, when I transfer Ubuntu to make a "home made;)" boot disk, do I transfer the .iso file, or do open the .iso file and transfer all the extracted files onto a disk?

TIA

Actually, you do neither. The .iso file is a disc image: It contains the exact same data that a real Ubuntu CD would contain. You must burn it as a disc image. In Toast, there is a setting called "Disc Image". It will ask you to specify the file, at which point you choose the ISO. Toast will burn it correctly onto the disc.

If you're using Nero on a Windows PC, you choose (I believe) "Burn Image to Disc". Once again, it asks you for the image file, and burns it correctly. DON'T choose "Create bootable disk".

---

### Post by timka1 on 2006-07-27
> **UNIVSOUTHFLA said:**
> Hey every1, with my further research into opensource software, I decided to give Ubuntu another shot. Right now, I have Q (Mac version of QEMU) and downloaded the "desktop" version of Ubuntu. Now I want to install Ubuntu onto Q. Now, when I transfer Ubuntu to make a "home made;)" boot disk, do I transfer the .iso file, or do open the .iso file and transfer all the extracted files onto a disk?

TIA

Just did something similar and made the mistake of letting the .iso image mount and then writing files from the ensuing volume. Wrong! What you should do is drag the .iso file to Toast icon and it will know what to do. I did this when Toast wasn't already running in case that makes a difference...

---

