---
title: "Can't get 3D Windows to work with compiz using Gusty"
date: 2007-10-31
forum: Absolute Beginner Talk
---

### Post by jhyatt7823 on 2007-10-31
So I just upgraded to 7.10 and I have been messing around with compiz.  One annoying problem I have noticed is that every time I try and enable 3D windows compiz crashes and retruns to the normal window manager.  In order to get compiz running again I turn off the 3D window plug in go to system>prefrences>appearence and turn it back on.  Anyone know how to get my 3D windows up and running thanks

---

### Post by 1337455 10534 on 2007-10-31
heh.
when reconfigging Compiz, try Alt+F2 and "ccsm". It'll get you there faster...

---

### Post by jhyatt7823 on 2007-10-31
Hey sorry but I dont think I understand your post

---

### Post by llamakc on 2007-10-31
Is that plugin working yet? Perhaps you have an old plugin left over from earlier?

---

### Post by jhyatt7823 on 2007-10-31
That may be true, can you tell me how to get the new plug in

---

### Post by Jose Catre-Vandis on 2007-10-31
So where is the 3D Windows plugin? Can't find it on my system (ccsm)

---

### Post by jhyatt7823 on 2007-10-31
It is under "effects" on mine

---

### Post by 1337455 10534 on 2007-10-31
Press Alt, hold it down, and then press F2. Enter in "ccsm" in the dialog box.

Gets you there faster than that menu you use.

Perhaps try: (in the terminal/console) (app -> accesories)
```

sudo apt-get remove //plugin-name
sudo apt-get update
sudo apt-get install //plugin-name
sudo apt-get upgrade

```
The upgrade just because.
If you dont know the name of the plugin... Umm, find it in Synaptic. (sys -> admin -> Package Manager)

---

### Post by llamakc on 2007-10-31
It doesn't work with Compiz-Fusion shipped with Gutsy.

---

### Post by jhyatt7823 on 2007-10-31
Haha, well I got the updated plugins from synaptic and now ccsm doesnt even have a 3D windows option.  Apparently this isn't a feature of the new compiz?

---

### Post by llamakc on 2007-10-31
> **llamakc said:**
> It doesn't work with Compiz-Fusion shipped with Gutsy.

Exactly. I'm sure it will make an appearance back in the plugins soon though.

---

### Post by Jose Catre-Vandis on 2007-11-01
Aah, thought so

---

### Post by mc4man on 2007-11-01
[http://ubuntuforums.org/showthread.php?t=585491](http://ubuntuforums.org/showthread.php?t=585491)
works fine

---

