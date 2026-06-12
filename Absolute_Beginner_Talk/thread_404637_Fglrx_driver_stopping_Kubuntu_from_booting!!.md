---
title: "Fglrx driver stopping Kubuntu from booting!!"
date: 2007-04-08
forum: Absolute Beginner Talk
---

### Post by miggols99 on 2007-04-08
I recently installed Beryl which works really well. But when I turned off my computer, then came back to turn it on, it goes to the terminal. When I type in "startx" an error message appears saying something like "fglrx driver not found". Why is this happening?! I installed the driver with Envy (ATI) and worked ok then. Please help me. I have no idea what to do...

---

### Post by mattgaunt on 2007-04-09
If you made a back-up of your x-org.conf file then try gettin that back, or there is a way you can reset you xorg.conf through the live or text CD try searching for that i hav done it but cant remember it

---

### Post by jhenager on 2007-04-09
When I had the same problem, I started up to get to the terminal, and then found a backup of my original xorg.conf file in the same directory. The steps I followed created an xorg.conf.original file. I renamed the existing xorg.conf to xorg.conf.bad, and then renamed xorg.conf.original to xorg.conf.
It was a lot easier than reinstalling.

---

### Post by miggols99 on 2007-04-10
Ok. I've installed Kubuntu Feisty Fawn instead and everything works! I think I'll be keeping this :)

---

