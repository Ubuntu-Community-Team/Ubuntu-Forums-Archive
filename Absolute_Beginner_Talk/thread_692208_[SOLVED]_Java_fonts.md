---
title: "[SOLVED] Java fonts"
date: 2008-02-09
forum: Absolute Beginner Talk
---

### Post by Tranquilo on 2008-02-09
Hello folks!
My netbaking system was just "upgraded" and it has resulted in me not being able to log on to my bank anymore while using Ubuntu.
My bank doesn't support Linux (surprise, surprise!), but sent me a mail suggesting that it is because Java can't acces one of the following 3 fonts: Verdana, Ariel or Helvetica.
How do I go about enabling these fonts for Java?
Any suggestions are much appreciated, as i am totally blank on where to start! :(

---

### Post by jan quark on 2008-02-09
perhaps this helps install the following packages
with this terminal command

```
sudo apt-get install msttcorefonts gsfonts gsfonts-x11
```

---

### Post by Tranquilo on 2008-02-09
You're a genius! :)
It worked.
Many thanks!!!!!

---

### Post by jan quark on 2008-02-09
you are welcome :)

---

