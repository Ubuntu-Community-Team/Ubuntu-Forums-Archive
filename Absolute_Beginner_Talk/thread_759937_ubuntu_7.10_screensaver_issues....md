---
title: "ubuntu 7.10 screensaver issues..."
date: 2008-04-19
forum: Absolute Beginner Talk
---

### Post by jeanna22 on 2008-04-19
Alright, so about a month ago my screensaver (molecule) decided to stop working. Instead of molecules appearing, you'd be prompted to the login screen and would lose whatever you had open. After logging back in, I tried to change the screensaver settings, but would be prompted to the login screen (again). I waited until my boyfriend came home (hoping he'd be able to fix the problem), but had little luck. He simply said wait for more updates and maybe they'd fix the problem. They haven't.. so if you could help/give suggestions it'd be greatly appreciated. Thanks!  :)

---

### Post by quirks on 2008-04-19
Sounds to me like your computer has problems with 3D support. Whenever your graphics card should "show something in 3D" (e.g., screensaver or preview in screensaver options), your X server crashes and you are brought back to the initial login screen.

What is your graphics card? Have you enabled proprietary drivers?

---

### Post by Moop on 2008-04-19
Have you checked that your video card driver is properly installed through the restricted driver manager?

---

### Post by jessika-kaos on 2008-04-19
I had one particular screensaver that caused X to freeze (all the others i've tried worked and 3d displays properly in all other cases). I also could not go to the screensaver settings because the preview would cause X to freeze. 

I was able to get around it by opening gconf-editor in a terminal and finding the screensaver settings, then changing it to blank screen from there. Still don't know why the original screensaver kept freezing, but I haven't had the problem since then.

---

