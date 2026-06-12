---
title: "hdd confusion"
date: 2008-03-05
forum: Absolute Beginner Talk
---

### Post by libran_devil on 2008-03-05
I wanted to install ubuntu in my system. Now I have one sata hdd 160gb in which my c drive is present and so naturally is my master drive. I hav another hdd 80 non sata and had two drives. I installed my ubuntu in the 80gb hdd. I gave 5.8gb for mount point / and gave 600 mb for swap. And kept  automatic setting for grub. After restarting the pc the grub was not installed and my full 80gb hdd is showing bad sector plz tell me wht to do plz I hav lost so much of my data plz help me is tht I shud hav installed in 160 gb or the grub is not properly loaded expecting a reply soon?

---

### Post by Crooksey on 2008-03-05
Load the live cd...

Remount the 80GB HDD / partition, and post the contents of the file...

```

/boot/grub/menu.lst
```

---

### Post by hyper_ch on 2008-03-05
Mixing of SATA and IDE drives is a bit tedious...

My suggestion would be:

(1) Unplug the SATA drive

(2) Install it on the IDE drive

(3) Replug the SATA drive and set in the bios the primary boot device to the IDE drive

---

