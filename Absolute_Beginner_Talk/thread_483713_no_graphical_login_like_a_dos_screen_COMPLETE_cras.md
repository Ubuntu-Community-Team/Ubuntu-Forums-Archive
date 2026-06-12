---
title: "no graphical login like a dos screen COMPLETE crash on Fawn"
date: 2007-06-25
forum: Absolute Beginner Talk
---

### Post by LiNuXxToOthEMaX on 2007-06-25
i have tried sudo dpkg-reconfigure-xorg and all that, it doesn't work i get an error about  a repository and need to update my graphical login???? any ideas im really stumped this has happened like 2 times alrady

---

### Post by Crafty Kisses on 2007-06-25
> **LiNuXxToOthEMaX said:**
> i have tried sudo dpkg-reconfigure-xorg and all that, it doesn't work i get an error about  a repository and need to update my graphical login???? any ideas im really stumped this has happened like 2 times alrady

Since the command "sudo dpkg-reconfigure xserver-xorg" didn't work I'm thinking it's a repository issue. So If you have the Ubuntu Alternate Installer CD, you can enter these following commands and see what happens:
```
sudo aptitude update
sudo aptitude install ubuntu-desktop
```

---

### Post by avik on 2007-06-25
Can you give us the actual error (what repository or anything else that might be significant)?

---

### Post by Crafty Kisses on 2007-06-25
Did the command work? Let me know.

---

