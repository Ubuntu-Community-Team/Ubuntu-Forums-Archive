---
title: "Screen resolution too high, and cant be changed!"
date: 2008-01-11
forum: Absolute Beginner Talk
---

### Post by patrickbway on 2008-01-11
Hi there. Im new to linux and Ubuntu, and I love it!

Anyway, i was fiddling with the screen and graphics setting and I setted the screen to an LG with a different model number to mine. I also changed the resolution to a setting i knew worked. I clicked ok, but it said i needed to log off to see the effects.I did this, and now the screen cannot geta  signal. Unbuntu is working my monitor cannot cope with the new settings!

Is there a way to default the screen settings when you press esc on GRUB?

Thanks

---

### Post by nikoPSK on 2008-01-11
you could reconfigure xorg...
 
```
 
sudo dpkg-reconfigure -phigh xserver-xorg

```

---

### Post by fiddledd on 2008-01-11
Never had to do this but if I remember correctly, sellect Recovery Mode from Grub menu then type "dpkg-reconfigure xserver-xorg" and answer the prompts to setup X again.

---

### Post by fiddledd on 2008-01-11
Not only did I post too late again, it also looks like I was wrong as well :(

---

### Post by nikoPSK on 2008-01-11
> **fiddledd said:**
> Never had to do this but if I remember correctly, sellect Recovery Mode from Grub menu then type "dpkg-reconfigure xserver-xorg" and answer the prompts to setup X again.
 
I told him that. :KS Anywyas, phigh sets better defaults. So try that, Tell me if it works.
 
EDIT: LOL

---

### Post by patrickbway on 2008-01-11
Hi!

Thanks for your help! Worked a treat

---

### Post by nikoPSK on 2008-01-11
No problem. Please mark this thread as "SOLVED" :KS
 
thanks,
nikoPSK

---

