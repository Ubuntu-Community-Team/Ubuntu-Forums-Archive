---
title: "Hp Pavillion dv6130us webcam."
date: 2008-02-08
forum: Absolute Beginner Talk
---

### Post by rachel10123@msn.com on 2008-02-08
I have a HP Pavilion dv6130,and I am running Ubuntu 7.10,is there a driver that I could download to use my webcam?:(

---

### Post by cwbar_1 on 2008-02-08
Go to Applications>Accessories>Terminal.  Type lsusb .  (that first letter is a small L)
If the results include a line > Bus 001 Device 002: ID 0c45:62c0 Microdia,  you can download and install Cheese. ([http://www.gnome.org/projects/cheese/download.html](http://www.gnome.org/projects/cheese/download.html)) Picture taking program.
Ekiga Softphone will also work.  I don't use the webcam for anything besides taking wacky pictures for/of my grandson, so I can't advise on whether it would work for anything else.

---

### Post by rachel10123@msn.com on 2008-02-08
Thanks,but this didnt work

---

### Post by cwbar_1 on 2008-02-08
type the lsusb command and post the results.  There are several projects going on with webcam drivers.

---

### Post by rachel10123@msn.com on 2008-02-09
rae@Rae:~$ lsusb
Bus 005 Device 002: ID 05ca:1870 Ricoh Co., Ltd 
Bus 005 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
rae@Rae:~$

---

