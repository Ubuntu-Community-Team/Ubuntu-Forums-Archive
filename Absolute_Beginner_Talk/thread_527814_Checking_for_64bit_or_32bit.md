---
title: "Checking for 64bit or 32bit"
date: 2007-08-17
forum: Absolute Beginner Talk
---

### Post by anothrguitarist on 2007-08-17
Alright this is a silly question, but I cannot find the answer. My computer is AMD64, but I am not sure what architecture ubuntu is using. How do I check whether my ubuntu is 32bit or 64bit.

Thanks

---

### Post by RomeReactor on 2007-08-17
Hi. Open a terminal (Applications->Accessories->Terminal) and enter the following:
```
uname -m
```
if the result is 386 (I don't know if this is around anymore) or 686, then it's 32 bit; if the output is x86_64, then it's 64 bit.

---

### Post by anothrguitarist on 2007-08-17
Thank you :)

---

