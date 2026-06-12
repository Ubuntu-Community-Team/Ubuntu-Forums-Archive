---
title: "Startup Error"
date: 2006-09-10
forum: Absolute Beginner Talk
---

### Post by amcavoy on 2006-09-10
I have used a dual operating system for quite some time without any trouble.  Recently, however, when I start the computer, I get an "Error 17" instead of the GRUB menu.  I cannot get past this and use either of my OS's.  Does anyone know what this is and how to fix it?  Thank you.

---

### Post by FakeOutdoorsman on 2006-09-10
Error 17 means that your computer is looking for the instructions on how to boot but can't find them.  If you're using Windows as your other OS then you can boot from your Windows installation cd into "rescue mode" and then type "fixmbr", which may fix your Master Boot Record.  If that doesn't work or if it sounds too dangerous then [read these posts]("site:ubuntuforums.org "Error 17" grub") first.

---

