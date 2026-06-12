---
title: "Uggh.. how do I remove something that's not working?"
date: 2008-02-01
forum: Absolute Beginner Talk
---

### Post by Liv on 2008-02-01
Hey, I downloaded and installed Tee Wars, but I think I may have installed the wrong one.  I installed the 32 bit when I should've dloaded the 64 bit.  And now I can't find it in the add/remove softwear application.. I searched for it and everything.  It's still in the games but isn't working right and I would just like to get rid of it but I don't know the command,
Egad....
Liv

---

### Post by jan quark on 2008-02-01
did you search in the synaptic package manager?

just mark to uninstall it there and click apply

---

### Post by iansane on 2008-02-01
Did you search for it in System>Administration>Synaptic Package Manager?

---

### Post by LowSky on 2008-02-01
did you install it from add/remove? im guessing not, so your going to have to remove it by hand

BTW its based off a game called Wormux ... which has an opensource version on synaptic

---

### Post by Liv on 2008-02-01
I searched for tee wars and it didn't show up and I updated and now my visual effects don't work either... I think I f'd something up :S

---

### Post by spiderbatdad on 2008-02-01
for packages I got from synaptic, I use```
sudo apt-get remove --purge package
```
for packages i've downloaded, i use ```
sudo dpkg -r package
```

---

### Post by Liv on 2008-02-01
> **iansane said:**
> Did you search for it in System>Administration>Synaptic Package Manager?

Thank you, that got rid of it.  However now that I have done that I can't get my cube screen to have 4 sides like it use to now it only has 2 screens...
any quick fix?

---

### Post by emarkd on 2008-02-01
In CCSM on the General Options section, Click the Desktop Size tab and slide the Horizontal Virtual Size to 4 (or whatever)

---

