---
title: "question about installing and about the live CD"
date: 2006-12-01
forum: Absolute Beginner Talk
---

### Post by I_have_seen_the_light on 2006-12-01
Hi 

Got a question. I loaded the live CD ona P3 600 mhz PC with 196 mb Ram  the live disk works fine.  installed it, the installation was ok.  but when I tried to boot on the newly installed system, all I get is a Garbled screen flashing. why is that? and an fix for it.  btw, I ran edubuntu 6.06 on it and it ran well. currently I am running Xubuntu on it and it runs great.

---

### Post by Bachstelze on 2006-12-01
What kind of graphics card does it have ?

---

### Post by I_have_seen_the_light on 2006-12-01
Sorry, I dont know, its intergrated in the board. the computer is a second hand unit from Korea I think

---

### Post by Bachstelze on 2006-12-01
all right, please paste the output of

```
lspci
```

---

### Post by az on 2006-12-01
> **I_have_seen_the_light said:**
> Hi 

Got a question. I loaded the live CD ona P3 600 mhz PC with 196 mb Ram  the live disk works fine.  installed it, the installation was ok.  but when I tried to boot on the newly installed system, all I get is a Garbled screen flashing. why is that? and an fix for it.  btw, I ran edubuntu 6.06 on it and it ran well. currently I am running Xubuntu on it and it runs great.

The installer needs 256 megs of ram to run from the live cd.  It may have crashed silently during the install.  Try the alternate cd - it installs in text mode and needs a lot less ram.

---

