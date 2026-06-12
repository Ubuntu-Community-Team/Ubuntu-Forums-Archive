---
title: "scim + aMSN"
date: 2008-11-06
forum: Arch and derivatives
---

### Post by zephyrus17 on 2008-11-06
So, scim works everywhere except with chat messages in aMSN. Does anyone know how let me type Chinese in aMSN?

---

### Post by zephyrus17 on 2008-11-06
I solved it.

```
# EDITOR /etc/scim/global
```

Then change the locale after ```
/SupportedUnicodeLocale = 
``` to your locale. If you want to have more than one locale, seperate them with a comma.

(Could a Mod change the title to [solved] or something, so others can benefit as well?)

---

### Post by elliah on 2008-11-22
i tried what you did but scim still doesn't work with aMSN...it works with everything else on my computer though...what packages for scim do you have installed?

---

### Post by zephyrus17 on 2008-11-23
Well, I just followed the instructions on Arch wiki for scim

---

