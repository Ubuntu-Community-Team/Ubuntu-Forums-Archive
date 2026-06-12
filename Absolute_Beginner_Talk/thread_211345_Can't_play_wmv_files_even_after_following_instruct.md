---
title: "Can't play wmv files even after following instructions on restrictive formats page"
date: 2006-07-08
forum: Absolute Beginner Talk
---

### Post by BlackMambo on 2006-07-08
I installed the codecs as described on [this page]("https://help.ubuntu.com/community/RestrictedFormats#head-6c942d1939d97331f96e42b63774003fde7daed5"): 

but when I play a .wmv file in Totem it says [COLOR="Red"]you do not have a decoder installed to handle this file. You might need to install the necessary plugin.[/COLOR]

!??

---

### Post by Rackerz on 2006-07-08
Do this is console:

```
Sudo apt-get install totem-xine
```

Then try to play the file.

Also make sure you installed w32codecs.

---

### Post by BlackMambo on 2006-07-08
thank you - that worked

---

