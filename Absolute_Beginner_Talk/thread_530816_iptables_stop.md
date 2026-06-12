---
title: "iptables stop"
date: 2007-08-20
forum: Absolute Beginner Talk
---

### Post by gishaust on 2007-08-20
hi 

I have just installed iptables using webmin and have locked myself out with my rules.  I need the command to halt iptables at the server so that i can fix it using webmin. Can anyone help me I am using iptables 1.3.6

---

### Post by gishaust on 2007-08-20
hi

how do I stop iptables in ubuntu server 7.04 
iptables version 1.3.6

I have read the tuorial and I wont work

---

### Post by bodhi.zazen on 2007-08-21
Threads merged as they are the same basic question.

Please read the stickies, the tutorials section is NOT for support questions.

========

I am not sure what you have done exactly. Reboot. If that does not work, please be more specific, what did you change exactly ?

---

### Post by gishaust on 2007-09-02
thank you for the response

Sorry for the late reply i have been on holidays.

What I did is blocked the port the webmin works on. in Ip tables and locked myself out. so I went to the server and  iptables -f that gets me back to the original state of iptables which for me lets everything through. then I configured Ip tables to let webmin in and out of the firewall.

works great

---

