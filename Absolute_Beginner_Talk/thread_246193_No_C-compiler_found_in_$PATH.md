---
title: "No C-compiler found in $PATH"
date: 2006-08-28
forum: Absolute Beginner Talk
---

### Post by Yumi on 2006-08-28
I downloaded an unpacked tar -zxvf openq-0.3.2.tar.gz. Then ./configure is checking various files and finally says "no acceptable C compiler found in $PATH". I have gcc-4 installed. What is the right syntax?

Have an AMD64 and Dapper.

Michael

---

### Post by Omnios on 2006-08-28
DO you have build-essential installed. Its all the basic compilers and stuff

---

### Post by Yumi on 2006-08-28
Not that I know of. How would I install those?
Michael

---

### Post by bodhi.zazen on 2006-08-29
In a terminal:
```
apt-get install build-essential
```

---

### Post by Yumi on 2006-08-29
Thanks, is  working now. I had to install from a downloaded alternativ CD as the Live CD would not install. This obviously does not install "everything"

Michael

---

