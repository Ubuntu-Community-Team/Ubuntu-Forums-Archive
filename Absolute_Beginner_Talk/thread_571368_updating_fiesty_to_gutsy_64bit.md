---
title: "updating fiesty to gutsy 64bit?"
date: 2007-10-09
forum: Absolute Beginner Talk
---

### Post by sayuki288 on 2007-10-09
wanna upate fiesty to gutsy 64bit but dont know how

---

### Post by nest on 2007-10-09
```
sudo update-manager -d
```

---

### Post by FuturePilot on 2007-10-09
> **nest said:**
> ```
sudo update-manager -d
```

No, this will just upgrade. The OP wants to know how to go from Feisty 32bit to Gutsy 64bit. 
But as far as I know this isn't possible. You would have to do a fresh install of Gutsy 64bit.

---

### Post by sayuki288 on 2007-10-09
is that all i have to type?

---

### Post by PmDematagoda on 2007-10-09
No, as FuturePilot said, you cannot upgrade a 32 bit OS to a 32 bit one. The command you are talking about will only upgrade your system to Gutsy 32 bit not Gutsy 64 bit. If you want 64 bit Gutsy you will have to reinstall it.

---

### Post by nest on 2007-10-09
if FuturePilot is right i misunderstood you. im sorry.

i u wanna update feisty 64b to gutsy 64b is like i said before.

---

### Post by philinux on 2007-10-09
If I've got home on a separate partition and copy it to a new pc, athlon 64, then install gutsy 64, will it pick up my prefs?

---

### Post by FuturePilot on 2007-10-09
> **nest said:**
> if FuturePilot is right i misunderstood you. im sorry.

i u wanna update feisty 64b to gutsy 64b is like i said before.

Oh, you're going from 64 to 64. I misunderstood and thought you wanted to go from 32 to 64. If that's the case then that command is what you want.

---

### Post by nest on 2007-10-09
> **FuturePilot said:**
> Oh, you're going from 64 to 64. I misunderstood and thought you wanted to go from 32 to 64. If that's the case then that command is what you want.

now im not sure what sayuki288 **really** wants.

now, **if you wanna update 64b to 64** you just have to type "**update-manager -d**" on a terminal.

if u wanna update **32b to 64b**, i think you cannot do that.

---

### Post by FuturePilot on 2007-10-09
> **nest said:**
> now im not sure what sayuki288 **really** wants.

now, **if you wanna update 64b to 64** you just have to type "**update-manager -d**" on a terminal.

if u wanna update **32b to 64b**, i think you cannot do that.

#-o I thought you were the OP
Now I've confused everyone](*,) I've even got myself confused.:lolflag:
Ok let's try to rectify this
You can upgrade from 32 to 32 and 64 to 64, but **not** 32 to 64

---

