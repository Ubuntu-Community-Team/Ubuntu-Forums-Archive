---
title: "Dual Booting with Vista"
date: 2008-04-04
forum: Absolute Beginner Talk
---

### Post by Cheese Roller on 2008-04-04
Alright, so I am trying to dual boot for the first time.

I have Vista installed on its own Hard Drive, and I'm gonna put Linux on the new one I just got.

Once I install Linux on the currently empty drive and I reboot, will it give me a choice of what to boot into or what?

Please tell me how this works.

---

### Post by tamoneya on 2008-04-04
Ubuntu will install something called a bootloader(GRUB).  This allows you to select which Operating system you want to boot.  Ubuntu will detect Windows and will add it to the list of OSes that you can boot.  By default ubuntu will configure GRUB so that Ubuntu is the default and will boot automatically after 3 seconds.  If you hit esc in these three seconds you will then get a change to boot XP.

---

### Post by Cheese Roller on 2008-04-04
Do you know about other distros like Fedora and SuSe?

---

### Post by tamoneya on 2008-04-04
linux distros have been doing this for years.  Fedora and SuSE should do very similar things.

---

