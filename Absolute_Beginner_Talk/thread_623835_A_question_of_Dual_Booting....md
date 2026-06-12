---
title: "A question of Dual Booting..."
date: 2007-11-26
forum: Absolute Beginner Talk
---

### Post by Jshaw on 2007-11-26
One of my friends is a really seasoned Ubuntu user and web developer. He told me that because I have two drives, I should install Ubuntu on the master drive because it has grub and will allow me to choose which OS to boot into, is this true?

---

### Post by PmDematagoda on 2007-11-26
Are your drives IDE or SATA? If you have IDE then that is recommended, if you have SATA then it is not needed at all.

---

### Post by Dr Small on 2007-11-26
IDE drives have master and slave attributes, but SATA doesn't, since they all go through seperate SATA wires. But in the BIOS, you can choose which drive boots first, so that would not be a big issue as to which drive you wish to install it to.

Dr Small

---

### Post by gn2 on 2007-11-26
> **Jshaw said:**
> One of my friends is a really seasoned Ubuntu user and web developer. He told me that because I have two drives, I should install Ubuntu on the master drive because it has grub and will allow me to choose which OS to boot into, is this true?

No. With IDE drives all you have to do is point the BIOS to the drive where GRUB is installed, it can be either master or slave.
You can choose where to install GRUB, or not install it at all and use an alternative bootloader.

I used to advocate separate drives for separate OS's however recently (since 7.04) there have been some problems with drive numbering after installation which can cause problems booting.
To avoid this, install the OS's on the same drive in a conventional dual boot, and use the other drive as shared storage.

Lots of useful info at Hermanzone, link in my sig. Lots to get through, but well worth a read.

---

### Post by jediquinn on 2007-11-26
I'm new to Ubuntu but I had a similar issue. I was running XP and I was not about to risk all of photos/music/personal files. So I installed Ubuntu on it's own hard drive. Should anything ever happen I can always take out the Ubuntu HD. These are IDE by the way. 

I say separate them if you don't want to risk messing up your original OS.

---

### Post by Jshaw on 2007-11-26
The hard drives are indeed IDE, I need a new hard drive because my current drive is down to the last megabytes. I want to transfer all my files onto the new drive and put Ubuntu on the old one. If Ubuntu is on the master drive, will grub be there as well?

---

