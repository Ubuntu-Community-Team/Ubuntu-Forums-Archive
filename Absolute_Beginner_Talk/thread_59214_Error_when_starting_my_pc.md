---
title: "Error when starting my pc"
date: 2005-08-23
forum: Absolute Beginner Talk
---

### Post by evansa4 on 2005-08-23
Hi guys do u know when u turn on tur pc and all them things come and it says starting linuxs and it says ok, ok well i am haveing some errors it has been saying fail and if i restart my pc 3 times if works fine any answers

---

### Post by adwait on 2005-08-23
On which step does it exactly say failed?

---

### Post by Jussi Kukkonen on 2005-08-23
I don't think you'll get any useful answers unless you tell us what the (exact) error message is...

---

### Post by evansa4 on 2005-08-23
well i think its is my slave drive it saying soming about errors on it 

is there any way i can format it that might fix it

---

### Post by adwait on 2005-08-23
Well, if there are errors on the file system, they could be fixed by umounting it and then running fsck. However, formatting that drive will also solve the problem...........if the problem is indeed with the file system, and not something else.

---

### Post by Jussi Kukkonen on 2005-08-23
[QUOTE=evansa4]well i think its is my slave drive it saying soming about errors on it 

is there any way i can format it that might fix it[/QUOTE]
 Please, the exact error message... so far you've said the equivalent of *"my car stopped, there's a red light blinking. What's wrong?"*. 

If you can't read it because it flashes past the screen on boot, look for it in the output of **dmesg** (from the command line).

---

