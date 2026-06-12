---
title: "Login problem"
date: 2007-01-02
forum: Absolute Beginner Talk
---

### Post by Geir102 on 2007-01-02
Hi just installd ubuntu. But when I log in and the system is starting, suddently it just jumps back to the login screen. Some times i get "panel allredy running, exiting" or somthing like that. I had to use OEM to install had the same problem there.

Any one know whats wrong?

---

### Post by bapoumba on 2007-01-02
Hi,
do you have enough free space on your partitions ?
When on GDM loggin screen > CTRL+ALT+F1 will get you to a tty, login, then **df -H** will show you all yours partitions and free space. Check root (/) and /home if on a different partition.
**sudo apt-get clean** will make some room on /.

---

### Post by Geir102 on 2007-01-02
Tanks for a quick answer:) 
I have 4gb of space for ubuntu and a 256 swap. When it jumps back to the login screen it loks like the screen changes reselution, it jups a bit if you know what i mean. Some times i can stay logd in but when im trying to use firefox i logsout.

---

### Post by bapoumba on 2007-01-02
Okay, not sure I actually know what you mean by "jumps" ;)
4 Go is **free** space, am I correct ?

---

### Post by Geir102 on 2007-01-02
No thats the full partisjon. I am not at ubuntu computer right now so cant chek. I mean it jumps like it dose when you change the resulution. Like it gets turn of and the back.

---

### Post by bapoumba on 2007-01-02
So just check with **df -H** when you get back to your ubuntu computer. If not enough free space is available, your session usually ends up and brings you back to GDM screen with no error message.

---

### Post by Geir102 on 2007-01-02
I had a freind check 1,2 gb so that shoud be ok?

---

### Post by bapoumba on 2007-01-02
Yes, that should be OK.
Have to find some other explanation ;)

---

### Post by Geir102 on 2007-01-02
Ye im realy new to this so need all the help i can get. Tanks alot so far

---

### Post by Geir102 on 2007-01-02
Dont anyone know?   Im ](*,)

---

