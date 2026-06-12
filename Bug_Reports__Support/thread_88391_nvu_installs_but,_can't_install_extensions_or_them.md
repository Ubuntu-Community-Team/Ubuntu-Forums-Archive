---
title: "nvu installs but, can't install extensions or themes..."
date: 2005-11-10
forum: Bug Reports / Support
---

### Post by monway on 2005-11-10
](*,)
Annoying, nvu wysiwyg editor cannot install extentions. Any suggestions?
I've rebuilt and installed still no go. a bug?[-o<

---

### Post by mxa055 on 2006-02-02
I have the same problem. extensions and themes do not get installed in NVU. Any ideas?

---

### Post by hav0x on 2006-02-02
permissions?

---

### Post by mxa055 on 2006-02-02
[QUOTE=hav0x]permissions?[/QUOTE]
permissions of what? (installed through apt btw)

---

### Post by kaamos on 2006-02-13
```
sudo nvu
```
install extension.
then back to
```
nvu
```

---

### Post by seashell11 on 2006-03-13
I installed nvu through apt, and had to do a kdesu nvu, then install an extension and a theme, and then just go back to the regular nvu and I could always install themes and extensions in just the normal nvu after that.

---

### Post by coffee-beans on 2006-06-17
seashell11's fix worked for me. 1) Install with apt-get 2) gksudo /usr/bin/nvu 3) install extension 4) exit nvu 5) run nvu as native user 6) install extension

---

