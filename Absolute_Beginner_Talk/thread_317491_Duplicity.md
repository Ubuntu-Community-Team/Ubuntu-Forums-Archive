---
title: "Duplicity"
date: 2006-12-12
forum: Absolute Beginner Talk
---

### Post by linuxbun on 2006-12-12
Everytime I backup manually I have a error coming up that says "message was not integrity protected" What does that mean?

I might add that I add the password each time (I haven't got a gpg key set)

---

### Post by jtc on 2007-01-16
I could be wrong, but this sounds like an error from your gpg and not directly from duplicity. It would then have to do with gpg not using a MDC (modification detection code).

Did you install gpg in any speciall way? Compiled it yourself?

---

