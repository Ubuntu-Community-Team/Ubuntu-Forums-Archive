---
title: "PuTTY Escape Chars in XP-&gt;Ubuntu"
date: 2006-11-16
forum: Absolute Beginner Talk
---

### Post by marx2k on 2006-11-16
I am compiling C++ code on my Ubuntu laptop from my XP box via SSH through PuTTY

I get escape characters in my output text such as:
myprog.cpp:13: error: expected `;' before âcoutâ

(note the last word) 

in gnome-terminal under ubuntu this isn't a problem.

Does anyone know what setting under PuTTY it is to fix this or is this a fixable problem? I can live with it, but would rather see it fixed.

---

### Post by Old Pink on 2006-11-16
Wouldn't you be better off asking this on a PuTTY forum? :)

---

### Post by Naan Yaar on 2006-11-16
If you do:
```

export LANG=C

```
in the putty window before launching your app, it will set your locale to "C". Strings will then be displayed correctly in putty. The default locale assumes that your terminal application can handle UTF-8, which is causing the problem in putty.

---

### Post by marx2k on 2006-11-16
> **Naan Yaar said:**
> If you do:
```

export LANG=C

```
in the putty window before launching your app, it will set your locale to "C". Strings will then be displayed correctly in putty. The default locale assumes that your terminal application can handle UTF-8, which is causing the problem in putty.

That did it. Thank you for the help.

And yes, this probably SHOULD be in a PuTTY forum, but this forum seems to be a sort of catch-all for noob problems like these.

---

