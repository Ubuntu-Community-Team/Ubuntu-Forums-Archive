---
title: "Kubuntu xampp"
date: 2007-03-03
forum: Absolute Beginner Talk
---

### Post by staf on 2007-03-03
How can i start xampp on bootup in Kubuntu Edgy Eft?

Thanks for your help.

---

### Post by energiya on 2007-03-04
add to your /etc/rc.local file the line /opt/lampp/lampp start and the server should start before rhe graphical interface. Be warned: this will add the seconds needed to start the xampp server to your boot time. If you have a fast PC you could try adding a "&" after the line in rc.local.

---

