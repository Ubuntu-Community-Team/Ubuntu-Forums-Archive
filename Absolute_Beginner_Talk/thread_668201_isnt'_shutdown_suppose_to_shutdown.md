---
title: "isnt' shutdown suppose to shutdown"
date: 2008-01-15
forum: Absolute Beginner Talk
---

### Post by rishav on 2008-01-15
Isn't shutdown command suppose to shutdown the computer.

I enter sudo shutdown 180 and goto sleep. The next morning I find my computer saying Press CTRL+D or supply root password. Why is it not shutting down??

---

### Post by carverj on 2008-01-15
Just needs you to enter the root password by the looks
have fun 
;)

---

### Post by lswest on 2008-01-15
to shutdown you have to add shutdown -h for halt, or just use the alias "halt" to shutdown the computer.
man is always useful in figuring this stuff out^^ and i'm not sure if it's -h or -s, and i'm on a windows computer atm, so i cant check.

---

### Post by Paul820 on 2008-01-15
It should ask you for the root pasword before it enters the shutdown timer. So after you enter > sudo shutdown 180
It should ask for your password and then start the timer. If you need more info, in the terminal
> man shutdown

---

