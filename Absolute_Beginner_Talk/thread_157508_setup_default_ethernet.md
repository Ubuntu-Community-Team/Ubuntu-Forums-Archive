---
title: "setup default ethernet"
date: 2006-04-09
forum: Absolute Beginner Talk
---

### Post by malavar on 2006-04-09
hey guys im back, i need help configuring ethernet cards on a linux pc. it has 2 cards, but i dont know which one is set as the default. it doesnt connect to the internet either, when i run ifconfig none of the cards show up. i tyle lspci and i see the cards and their names so i dont think its a driver issue. thanks

---

### Post by ubernoob on 2006-04-09
You can do that from the menu in gnome. System --Preferences --> Networking
or from command line: network-admin
and change the default gateway device

---

### Post by malavar on 2006-04-09
ok, thank you!

---

### Post by xwing on 2006-04-09
[quote=malavar]hey guys im back, i need help configuring ethernet cards on a linux pc. it has 2 cards, but i dont know which one is set as the default. it doesnt connect to the internet either, when i run ifconfig none of the cards show up. i tyle lspci and i see the cards and their names so i dont think its a driver issue. thanks[/quote]

Here's what you could try:
1. Post the output of the lspci command here

2. $ cat /etc/networking/interfaces - this file contains a list of interfaces on your system. Do the 2 cards you mentioned show up there?

---

