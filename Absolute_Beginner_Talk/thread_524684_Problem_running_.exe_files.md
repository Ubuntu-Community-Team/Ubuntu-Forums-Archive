---
title: "Problem running .exe files"
date: 2007-08-13
forum: Absolute Beginner Talk
---

### Post by pkj on 2007-08-13
I have installed WINE...

However, on trying to open the files from my CDROM, i am getting the following error

Cannot open /media/cdrom0/help.exe: No application suitable for automatic installation is available for handling this kind of file.

same error with other .exe files also

This CD otherwise runs well on Windows

Suggestions !!!!!!!!!!!!!!!!

pkj

---

### Post by LaRoza on 2007-08-13
Are you using Wine to run them? Right click, and use custom command "wine".

---

### Post by Ek0nomik on 2007-08-13
You need to run the *.exe through Wine.

Accessories/Terminal:

```
wine /media/cdrom0/help.exe
```

---

