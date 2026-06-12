---
title: "Stopping X"
date: 2006-06-04
forum: Absolute Beginner Talk
---

### Post by JNowka on 2006-06-04
I am trying to install some new drivers and they are telling me that I need to exit X.  I was wondering how i would do that?

---

### Post by cromestant on 2006-06-04
Just control + alt + f1, login to the terminal then type
sudo /etc/init.d/gdm stop

hope it helps

Then to restart it,  /etc/init.d/gdm start

---

### Post by JNowka on 2006-06-04
It worked, thank you.

---

### Post by cromestant on 2006-06-04
No pb

---

