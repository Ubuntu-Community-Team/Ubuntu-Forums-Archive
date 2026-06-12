---
title: "[SOLVED] How to change the password encryption method in Ubuntu Gutsy?"
date: 2008-03-23
forum: Absolute Beginner Talk
---

### Post by Madman6510 on 2008-03-23
I want to change how the user login passwords are encrypted in Ubuntu Gutsy. I assume it can be done (OpenSUSE gives you an option), but I can't find the option in the settings, or find any instructions on Google. Also, what is the default encryption method in Ubuntu, and which is the most secure available?

---

### Post by RealPSL on 2008-03-23
Looks like /etc/login.def is the place to change this. I would have thought it would have been MD5 by default but this does not appear to be the case as the MD5_CRYPT_ENAB no. To use MD5 switch that to yes based on the comments in the file.

MD5 allows long passwords so I would choose it.

---

