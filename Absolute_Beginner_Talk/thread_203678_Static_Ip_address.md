---
title: "Static Ip address"
date: 2006-06-25
forum: Absolute Beginner Talk
---

### Post by cconk01 on 2006-06-25
currtently my ubuntu lamp server gets its ip address dynamicaly. How can i change it to a static ip address? i dont have any gui installed so i will need to do this threw the console i guess.... Thank you in advance!

---

### Post by IYY on 2006-06-25
Something like this...

sudo ifconfig eth0 192.168.0.142

---

### Post by cconk01 on 2006-06-25
That was it. Thank you

---

