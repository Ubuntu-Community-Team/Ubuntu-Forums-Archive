---
title: "How to ID my hardware IN Ubuntu 7.10"
date: 2008-03-20
forum: Absolute Beginner Talk
---

### Post by jmtjet on 2008-03-20
How would I ID the hardware in my desktop computer from the command line. Thanks.

---

### Post by sumguy231 on 2008-03-20
Do this:
```
lshw | less
```
Read the manpage for informmation on how to only display certain information - by default it lists everything.

---

### Post by jmtjet on 2008-03-20
One more question: I have two NIC cards in this computer. I'm trying to find out which one is being used for my connection. Thanks.

---

### Post by louieb on 2008-03-20
A little easier to read
```
sudo lshw -html > ~/hardware_info.html && firefox ~/hardware_info.html
```
> I have two NIC cards in this computer... which one is being used for my connection.

 The listing will contain the IP address if its connected.

---

### Post by jmtjet on 2008-03-20
Thanks louieb, that did the trick. :)

---

