---
title: "internet connection"
date: 2008-02-02
forum: Absolute Beginner Talk
---

### Post by Soumitra on 2008-02-02
how can i use my nokia5300(gprs via usb) phone as modem in ubuntu 7.10. I installed ubuntu yesterday and i cound not connect to internet pl help

---

### Post by x1a4 on 2008-02-02
Hi, welcome to the forums.

Does your service provider support IPv6?  If not, it's a good chance that that's what is causing the problem.  Open a terminal and run ```
sudo nano /etc/hosts
```, this will open a text editor with the file /etc/hosts in it.  

Comment all lines below the one which reads 'The following lines are desirable for IPv6 capable hosts' by putting a hash mark (#) in front of each line.  It's also a good idea to put the following aliases at the beginning of the file: 
```
127.0.0.1 localhost
127.0.0.1 localhost.localdomain
127.0.0.1 *computer_name*
127.0.1.1 localhost

```

Where *computer_name* put the name of your computer which you set during installation. If you haven't, exclude that particular line.

---

