---
title: "Fully uninstalling Wine"
date: 2006-12-21
forum: Absolute Beginner Talk
---

### Post by LIJI on 2006-12-21
Hey,
After installing wine I couldn't remember where does it put my files that Wine programs installed on c:\ (..\drive_c on winecfg) so I edited the drives settings to put it on home/user/wine/.
But after this, most of Wine programs stoped working, even after I restored the settings.
I had the same situation before, uninstalling and reinstalling Wine didn't restore the settings and it kept not working. I solved it by reinstalling Ubuntu, which I don't want to do again.
So my question is - How do I fully uninstall Wine, Including setting and everything, so I will be able to reinstall it and it will run fine? (Or any other way fixing it)

Thanking in advance,
-LIJI

---

### Post by ukch on 2006-12-21
You can remove all of your WINE settings by removing the .wine directory in your home. You can do this by opening a terminal and typing:
```
rm -rf ~/.wine
```
That will not uninstall WINE, but will restore your settings to their defaults (you will need to do this on a per-user basis).

---

### Post by LIJI on 2006-12-21
Ok, Thanks :)

---

