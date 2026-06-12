---
title: "how would i remove lampp, apache2, php5, mysql 5, phpmyadmin"
date: 2006-12-20
forum: Absolute Beginner Talk
---

### Post by zetsumei on 2006-12-20
how would i remove each of these items b/c i'm afraid they are messing up the configs of each other and i wanted to start fresh at seting up a local web server to test on.

items i want to remove:

lampp
apache2
php5
mysql 5
phpmyadmin

---

### Post by GuitarFingers on 2006-12-20
You can use synaptic and do a search for each of the items you want to remove and right click on them and choose "Mark For Complete Removal" This removes the files and any configuration files as well.  Be careful with what else it tells you it will remove though, you may end up removing something that is important and needed by other programs on your system.

On a side note, lamp stands for Linux-Apache-MySQL-PHP and doesn't have a corresponding package, its the acronym used to described a typical web server setup using those tools.  Also, its unusual that the configuration files are messing with each other, if you have just those items installed there shouldn't be a problem like that but I suppose stranger things have happened.

Hope that helps,

GuitarFingers

---

### Post by zetsumei on 2006-12-20
well i installed apache2 and i thought i had removed it before i installled lampp

---

### Post by nucrebain on 2007-01-06
I was confused about how to start synaptic. I figured it out though, I should have known better. 
(This is for other Newbs like me)

1.  Start the terminal: Applications --> Accessories --> Terminal

2.  Once in terminal type: "synaptic"

This will bring up the synaptic manager

-Patrick Kelly

---

