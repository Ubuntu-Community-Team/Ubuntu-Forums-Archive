---
title: "[SOLVED] How to install this font?"
date: 2008-04-17
forum: Absolute Beginner Talk
---

### Post by sharks on 2008-04-17
How to install this font?

---

### Post by chewearn on 2008-04-17
Copy the font file into /usr/share/fonts/; like this:

```
sudo cp Bloodrac.TTF /usr/share/fonts/bloodrac.ttf
```

---

### Post by joshrobinson on 2008-04-17
extract the zip file to your desktop, so you see the Bloodrac.TTF file

go to your desktop in the terminal
```
sudo cp Bloodrac.TTF /usr/local/share/fonts
```
```
sudo fc-cache -f -v
```

---

### Post by sharks on 2008-04-17
Ok thanks. Now how do we use that font?

---

### Post by sharks on 2008-04-17
Ok just found that i can use that font in Text Editor.

---

### Post by joshrobinson on 2008-04-17
yeah you can use it in text editors, open office etc
but to use it as a font for your desktop/titlesbars/icons
go to
system > preferences > appearance 
then use the font tab to set it

---

