---
title: "yet another WINE problem (game:cs)"
date: 2007-01-24
forum: Absolute Beginner Talk
---

### Post by caltabellotta on 2007-01-24
i am trying to configure wine so i can play counter-strike (yeah im addicted:( ).   When I set up, wine does not create a /home/USERNAME/.wine/ folder (or at least not that I can see).  I thus cannot install my tahoma fonts.  this is what happens with $wine cfg:
```
~$ wine cfg
wine: could not load L"c:\\windows\\system32\\cfg.exe": Module not found

```

I think I did a sudo apt-get install wine correctly, but I am not sure since wine setup or wine cfg does not work.

Please help!

---

### Post by YokoZar on 2007-01-25
winecfg is one word, meaning to launch the winecfg program
wine cfg will try and use wine to load a file named "cfg", but it can't find it.

---

### Post by caltabellotta on 2007-01-25
still same errors, now I receive this:
```
c:\\windows\\system32 is not accesible
```

---

### Post by YokoZar on 2007-01-26
Could you post what happens after running the following?

rm -rf ~/.wine
winecfg

This will clear whatever you have in your wine configuration and start from scratch.

---

