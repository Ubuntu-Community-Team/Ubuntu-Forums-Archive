---
title: "problem uodating packages"
date: 2007-04-21
forum: Absolute Beginner Talk
---

### Post by Benifited on 2007-04-21
when i hit the reload button on the synaptic package manager i get some updates but they all say hit or failed what should  i do

---

### Post by DougieFresh4U on 2007-04-21
Don't worry about that as it means nothing needed. I find the best thing is to go to terminal and **sudo apt-get update** then **sudo apt-get dist-upgrade** then **sudo apt-get -f install** and finally **sudo dpkg --configure -a**

---

