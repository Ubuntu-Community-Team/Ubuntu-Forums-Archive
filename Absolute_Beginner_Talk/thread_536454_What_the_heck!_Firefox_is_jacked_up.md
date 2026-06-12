---
title: "What the heck?! Firefox is jacked up"
date: 2007-08-27
forum: Absolute Beginner Talk
---

### Post by downgrade on 2007-08-27
All my buttons in firefox are gone, nothing appears, no text no pictures, the buttons are there but very thin and i dont know which is which. I went into prefferences but it shows nothing but a help and done button... why is everything missing? Why does my computer get messed up every day... this makes no sense

cntrl alt backspaced and now the menus (file, edit, view) and my toolbar books marks are all gone too... in both firefox64 and 32

---

### Post by por100pre1 on 2007-08-27
Maybe you Firefox profile is damaged. Try renaming it:

```
mv /home/your-user-name/.mozilla/firefox /home/your-user-name/.mozilla/firefox_backup
```

and restart Firefox.

EDIT: be sure to replace "your-user-name" with your actual user name

---

### Post by por100pre1 on 2007-08-27
If that doesn't work, put it all back together

```
mv /home/your-user-name/.mozilla/firefox_backup /home/your-user-name/.mozilla/firefox
```

and try this:

```
firefox -safe-mode
```

---

