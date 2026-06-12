---
title: "Install error"
date: 2007-06-27
forum: Absolute Beginner Talk
---

### Post by Ogrish on 2007-06-27
I installed a 2nd hard drive to install Ubuntu on it. I wanted to have dual boot with my XP drive. After installation when the computer boots up, I get an error "Error 21" at GRUB loading stage.  I think it installed over my XP because I completely removed the new drive from my computer and the same thing happens at boot up.  Is it safe to assume I'm s.o.l?

---

### Post by confused57 on 2007-06-27
> **Ogrish said:**
> I installed a 2nd hard drive to install Ubuntu on it. I wanted to have dual boot with my XP drive. After installation when the computer boots up, I get an error "Error 21" at GRUB loading stage.  I think it installed over my XP because I completely removed the new drive from my computer and the same thing happens at boot up.  Is it safe to assume I'm s.o.l?
Enter your bios setup and make sure your hard drive controller is set to "auto" for the Ubuntu drive and if you have an IDE drive make sure the jumpers are set correctly.

You can always repair your Window's boot by restoring Window's IPL to the mbr:
[http://www.users.bigpond.net.au/hermanzone/p18.htm](http://www.users.bigpond.net.au/hermanzone/p18.htm)

---

