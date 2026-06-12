---
title: "installing Ubuntu server LTS"
date: 2007-06-20
forum: Absolute Beginner Talk
---

### Post by winsane on 2007-06-20
Hello..
Just installed ubuntu server and it boots about halfway and chokes when running local boot scripts (/etc/rc.local)... How do I troubleshoot this or what is goin on?

Thanks

---

### Post by lamalex on 2007-06-20
try just hitting enter or control+alt+f2. Mine does this too, it's not that it actually chokes just for some reason the console output stops. control+alt+f2 will let you log in and work.

---

### Post by winsane on 2007-06-20
Thanks. That did get me logged in. Shouldn't startx bring up a GUI of some sort? This is the first time I have ever used Ubuntu Server.

---

### Post by txgeek on 2007-06-20
Ubuntu server doesn't install X by default

---

### Post by juantao on 2007-06-20
You could add X by doing

sudo apt-get install ubuntu-desktop 

or

sudo apt-get install xubuntu-desktop 

for the smaller xfce desktop

---

