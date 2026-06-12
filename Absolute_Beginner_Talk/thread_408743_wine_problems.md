---
title: "wine problems"
date: 2007-04-13
forum: Absolute Beginner Talk
---

### Post by sewercake on 2007-04-13
HI

This is my problem, When I go to synaptic, I download the wine and wine -dev packages. Then, when I go to the console, type in wine PROGRAM, it comes up with this error 
> Warning: the specified Windows directory L"c:\\windows" is not accessible.
Warning: the specified System directory L"c:\\windows\\system32" is not accessible.
Warning: could not find DOS drive for current working directory '/home/sam', starting in the Windows directory.
wine: could not load L"c:\\windows\\system32\\program.exe": Module not found


So, can any of you help?
thanks!



-Sewercake

---

### Post by freebird54 on 2007-04-13
Been a while - but I seem to remember a **wineseupk ** (or similar name) that needed to be run the first time - it setup the virtual c_drive and so on under the .wine directory in your /home/<username> space.

Surely there are HowTos (or even instructions?) with the package?  Seaching the forums here will surely turn up something :)

Sorry not to be more specific - but I don't the wine stuff as much as I thought I would...

---

### Post by david_kt on 2007-04-13
> **sewercake said:**
> HI
Then, when I go to the console, type in wine PROGRAM, it comes up with this error 




Make sure you have PROGRAM.EXE in your home folder (I doubt it). You must have real program to run with wine, not just imaginary program.

DK

---

### Post by themunkee on 2007-04-16
Try this:

```
cd ~
rm -rf .wine
winecfg
```

Just press OK. Hopefully in the terminal it will say something like: 'wine: '/home/user/.wine' created successfully.'

```
wine PROGRAM
```

---

### Post by fktt on 2007-05-16
umm... what they mean is for an example(you can try this:) "wine notepad.exe"

---

