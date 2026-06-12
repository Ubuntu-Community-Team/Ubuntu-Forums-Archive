---
title: "install fonts with exe's"
date: 2007-07-01
forum: Absolute Beginner Talk
---

### Post by amantonas on 2007-07-01
So I'm running wine on ubuntu. I finally get wireless network working. I have almost switched my mom over to ubuntu, but she does this business thing called stampin' up and she needs certain fonts. so i say no problem, open it with wine and the installer opens but there is a problem. there are 2 things you can click on, and they are both filled in black. I can't seem to find the fonts on the cd either, just the installer. HELP PLEASE

---

### Post by Bachstelze on 2007-07-01
What fonts are those ?Maybe you can just extract them from the EXE with cabextract.

---

### Post by cogadh on 2007-07-01
Just do this:
```
sudo apt-get install msttcorefonts
```
That will install al of the MS True Type core fonts, which should cover almost everything your mom may need.

---

### Post by amantonas on 2007-07-01
well, the fonts are made by the company. carefree, jodyola,etc. the fonts have weird names.(those are the names of the fonts)

---

### Post by cogadh on 2007-07-01
Oh, in that case, follow HymnTo Life's advice.

---

### Post by amantonas on 2007-07-01
The ONLY THING I need now is where linux keeps the fonts and I can  copy and paste them.

---

### Post by cogadh on 2007-07-01
The system fonts are in /usr/share/fonts, however if you are running this application in Wine, they should go in /home/*username*/.wine/drive_c/windows/system32/fonts.

---

