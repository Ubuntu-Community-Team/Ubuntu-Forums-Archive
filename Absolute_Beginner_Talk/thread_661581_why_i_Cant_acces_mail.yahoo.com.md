---
title: "why i Cant acces mail.yahoo.com???"
date: 2008-01-08
forum: Absolute Beginner Talk
---

### Post by ashley18 on 2008-01-08
why i cant access [www.mail.yahoo.com??](www.mail.yahoo.com??)
i have to go to another Pc to check my yahoo mail.. please help me..

---

### Post by hyper_ch on 2008-01-08
can you ping it?
Can you access yahoo.com?

---

### Post by ashley18 on 2008-01-08
yah... i can access yahoo.com
mail.yahoo.com is my problem.. how can i ping???
can u teach  me?? 
im a new user in ubuntu..

---

### Post by Raptor45 on 2008-01-08
Applications>Accessories>Terminal

run:

```
ping mail.yahoo.com
```

---

### Post by ashley18 on 2008-01-08
what next after i ping mail.yahoo.com?
im sory.. im not using my ubuntu right now so i cant test it.. im at my school right now.. by the way thanks for helping me..

---

### Post by Sef on 2008-01-08
1) If you are using Firefox, do you have No Script installed?

2) Have you tried using another browser like Opera?

---

### Post by ashley18 on 2008-01-08
ping: unknown host mail.yahoo.com
..
I'm using firefox right now.. opera browser???
let me try first..

---

### Post by macogw on 2008-01-08
If you can't ping it (you send some little packets at it, and if it gets them, it sends some back to tell you it arrived...if you get no packets back, you're not reaching the url), the browser can't do it.   Are you behind a firewall or proxy?  Can you post the output of ```
cat /etc/resolv.conf
```

---

### Post by ashley18 on 2008-01-08
> **macogw said:**
> If you can't ping it (you send some little packets at it, and if it gets them, it sends some back to tell you it arrived...if you get no packets back, you're not reaching the url), the browser can't do it.   Are you behind a firewall or proxy?  Can you post the output of ```
cat /etc/resolv.conf
```

under  proxy server.. and a fire wall..

---

