---
title: "Unistalling Ubuntu and installing windows"
date: 2006-07-02
forum: Absolute Beginner Talk
---

### Post by boyes on 2006-07-02
Hello all,
The other day i installed ubuntu and thought it was ok untill i realized that nearly all programs are designed for microsoft :( so i then decided to unistall ubuntu and re-install windows xp and then later attempt to create a dual boot system, so i deleted all the partitions on my hard drive to completely remove ubuntu (using gparted) and then i inserted my xp disc into the cd tray and restarted, when the text came up i pressed ESC and selected to boot from my xp disk. It then sounds like it is running the disk and initializing set up, but then it tries to boot from the hard disk (whih has no data on) and so grub error appears and i come to a dead end. How can i install xp? my disk runs in linux using wine and then when i select install an error comes up. Any suggestions?

---

### Post by boyes on 2006-07-02
this i a screenshot of the error i receive

---

### Post by someusernoob on 2006-07-02
Try booting from the Windows CD to install. Note that you have to press a key to really start from the cd, otherwise it boots the hard drive again, which it did now. And check if your boot device priority in the bios is set up properly.

---

### Post by ubu-for on 2006-07-02
1. Enter the BIOS
2. Choose your CD-ROM as first boot device and your HDD as second.
3. Save BIOS settings
4. Insert your XP CD
5. Reboot
6. XP will start from CD

---

### Post by ubu-for on 2006-07-02
[QUOTE=boyes]this i a screenshot of the error i receive[/QUOTE]

It's impossible to install an OS (Linux/Windows/...) under another OS! You always have to boot from the installation CD!

---

### Post by boyes on 2006-07-02
My cd won't boot even when i adjust my bios.
It says non bootable.
Even though i have booted from it before.

---

### Post by chambis on 2006-07-02
That is your punishment for installing windows instead of linux. Even your machine is against your decision. :P :rolleyes:


ANW lets see what is happening here... 
You have to run the cd before running grub or whatever. So be sure that the cd is in the tray before turning your pc on. Question: Are you sure that you configured bios properly?

---

### Post by roxics on 2006-07-02
Is your windows copy legal? Some illegal copies won't boot properly and give errors all over the place.

---

