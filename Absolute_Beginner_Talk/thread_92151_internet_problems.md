---
title: "internet problems"
date: 2005-11-18
forum: Absolute Beginner Talk
---

### Post by richieboy on 2005-11-18
i'm using dsl on an ethernet card.  i can get on to some pages, this one for example, but yahoo, google, and others don't work.  it just says connecting and never connects.  does anyone have any ideas?  please help.  i really like ubuntu.
thanks,
rich

---

### Post by adwait on 2005-11-19
Try turning off ipv6.
> 
The latest version of Mozilla includes support for "IPv6" a new form of addressing things on the Internet.

The problem is: Mozilla tries to use IPv6 before it uses IPv4 (IPv4 is the old version). When your Internet connection doesn't support IPv6, Mozilla fails to connect on the first try. In the current version of Mozilla, you can't change this, because of a bug.

To fix this issue follow these steps:
1. sudo nano /etc/modutils/aliases

Look for this line:
# alias net-pf-10 off # IPv6

Change the line to: (remove the #)
alias net-pf-10 off # IPv6

2. sudo update-modules


---

### Post by richieboy on 2005-11-21
THANK YOU, ADWAIT!!!!!!!!!!!!!

i don't have an aliases file in my /etc/modutils/ but i found the turnoff line for ipv6 in /etc/modprobe.d/aliases, i changed the line to off and IT WORKS!!!!!!!!!!!!!!
thanks,
rich

---

