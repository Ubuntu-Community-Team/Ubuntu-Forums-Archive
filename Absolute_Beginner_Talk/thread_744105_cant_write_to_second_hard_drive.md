---
title: "cant write to second hard drive"
date: 2008-04-03
forum: Absolute Beginner Talk
---

### Post by c0d4041292 on 2008-04-03
hi, i just installed a second harddrive on my comp and i can mount it and i have partioned it to ext3. but whenever i try to put something on it it give me an error of permission denied. i tryed to go into properties and permission but it wont let me change them because i am not owner of this drive???? i was wondering how to change the permissions so i can store stuff on it.

---

### Post by taavikko on 2008-04-03
**sudo chown -R username /mount/point/**
Replace username. or use chmod

---

### Post by c0d4041292 on 2008-04-03
thank you so much

---

