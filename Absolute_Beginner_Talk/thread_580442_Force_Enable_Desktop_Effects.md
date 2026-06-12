---
title: "Force Enable Desktop Effects"
date: 2007-10-18
forum: Absolute Beginner Talk
---

### Post by Duffasaurus on 2007-10-18
Can I force enable the dektop effects? I click normal, and it's just like "Failed to enable dektop effects" but I know my card can run them, because it ran desktop effetcs before this 7.10 business...

---

### Post by Duffasaurus on 2007-10-18
come on?

---

### Post by Zibeb on 2007-10-18
alright. I had this same problem too when I switched to Gutsy. Try typing 
```

compiz --replace SKIPCHECKS=YES

``` 
in a terminal.

---

### Post by Zibeb on 2007-10-18
It turns out that some video cards were blacklisted. Right now, as a workaround, I'm using the Compiz Fusion Icon. If you hold on for a sec, I can grab a link.

---

### Post by Zibeb on 2007-10-18
this gives a link to a deb file:

[Compiz Fusion Tray Icon]("http://tombuntu.com/index.php/2007/08/26/compiz-fusion-tray-icon/")

---

### Post by Duffasaurus on 2007-10-18
I think I'm getting hte hang of linux-I tried to run compiz in ubuntu, it was missing gtk, so I sunaptic'd gtk and it worked :D

---

### Post by lazyart on 2007-10-19
I went into the compiz script and commented out the texture size check.  Now I have 1400x1050 and desktop effects all from a 32MB Radeon 7500.  With my hardware (1.6 Pentium M, 512MB RAM) I doubt I could even complete a Vista installation.

---

