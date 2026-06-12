---
title: "dell 640m wifi"
date: 2007-10-31
forum: Absolute Beginner Talk
---

### Post by muh_ashraf on 2007-10-31
i am using Dell inspiron 640m. My wifi not working if i do following command lspci then i can "0c:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)"

---

### Post by Jaco Du Toit on 2007-10-31
If you run:
lsmod

does it show that you have a module loaded called ipw3945? 

Also, what is the output if you run iwconfig?

---

