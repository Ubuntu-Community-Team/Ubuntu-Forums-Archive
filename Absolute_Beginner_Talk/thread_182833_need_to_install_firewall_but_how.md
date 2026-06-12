---
title: "need to install firewall but how?"
date: 2006-05-26
forum: Absolute Beginner Talk
---

### Post by pegasus on 2006-05-26
hi, new to linux, have installed ubuntu 5.10, therefore firestarter is first priority. but how?have got as far as question: how do i uncomment? ie i can understand that i need to alter the code on my machine... ? is it that i rewrite it...  could someone walk me threough this. etc etc

---

### Post by Sef on 2006-05-26
> firestarter is first priority

First follow these directions for adding repositories:

[AddingRepositoriesHowto]("https://wiki.ubuntu.com/AddingRepositoriesHowto")

then

System > Administration > Synaptic Package Manager

Do a search > type in firestarter > Highlight Firestarter > Click apply

or

Applications > Accessories > Terminal

sudo apt-get update

sudo aptitude install firestarter

---

### Post by aysiu on 2006-05-26
[Try not to double-post](http://www.ubuntuforums.org/showthread.php?p=1056822). Thanks.

---

