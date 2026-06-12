---
title: "[SOLVED] .bin problems"
date: 2007-07-28
forum: Absolute Beginner Talk
---

### Post by WarholsGhost on 2007-07-28
I'm getting this when ever i try to open a .bin

Could not open the file /home/gregg/Desktop/jre-6u2-linux-i586.bin.
gedit has not been able to detect the character coding.
Please check that you are not trying to open a binary file.
Select a character coding from the menu and try again.

how can i get it to work?

---

### Post by tomcheng76 on 2007-07-28
```

chmod 755 /home/gregg/Desktop/jre-6u2-linux-i586.bin
cd /home/gregg/Desktop
./jre-6u2-linux-i586.bin

```

---

### Post by WarholsGhost on 2007-07-28
thanks

---

