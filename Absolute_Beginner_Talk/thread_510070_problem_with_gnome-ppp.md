---
title: "problem with gnome-ppp"
date: 2007-07-26
forum: Absolute Beginner Talk
---

### Post by wilzad on 2007-07-26
Hi,
I am having a problem with gnome-ppp, it takes a few tries to initialise phone, only after 7 or 8 tries i am able to connect.
the log seems like this,
 
initialising modem
sending ATZ
ATQ
OK
initialising modem
sending ATZ
OK
ATQ
OK
 
 
again this loop continues,
after canselling and connecting again and again i may hit luck and it will connect,
please let me know why it is like this

---

### Post by Mark_in_Hollywood on 2007-08-02
Post the output of /etc/wvdial.conf

by 

sudo gedit /etc/wvdial.conf

ctrl-a

ctrl-c

open a "new" in the gedit, ctrl-v and save the output to your desktop as conf-wvdial. 

Post that here.

---

