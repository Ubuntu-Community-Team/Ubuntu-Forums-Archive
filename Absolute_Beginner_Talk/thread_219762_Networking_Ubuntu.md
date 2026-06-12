---
title: "Networking Ubuntu"
date: 2006-07-20
forum: Absolute Beginner Talk
---

### Post by Alien260 on 2006-07-20
hello, 

my Linux Pc is situated in a network with aother PC they are all runnung windows Xp Sp2. when i try and browser to them i can see then on the network, but when i try to open them i get a message saying 

The folder contents could not be displayed.

Sorry, couldn't display all the contents of "Windows Network: PC_001".

why do i get this message, how can i get to these Pc

thanks

---

### Post by PriceChild on 2006-07-20
```
sudo aptitude install samba
``` 
Should help.

(if you haven't got aptitude, i advise you get it, else replace with "apt-get")

---

### Post by shanepardue on 2006-07-20
why do you prefer aptitude and does it remove through synaptic or just command "aptitude remove"?

---

### Post by PriceChild on 2006-07-20
Explanation of aptitude:
[http://www.psychocats.net/ubuntu/aptitude.php](http://www.psychocats.net/ubuntu/aptitude.php)

---

