---
title: "Where to see the MAC adress?"
date: 2007-09-03
forum: Absolute Beginner Talk
---

### Post by Somenoob on 2007-09-03
with ifconfig I see on Eth1: 
"UNSPEC Hwaddr 00-03.." followed by some other numbers that obsoiuly isin't a MAC adrees since it's to long. Any other ways to see it? I have tried arp -a command, doesn't return anything. 

Thanks in advance.

---

### Post by tyggna1 on 2007-09-03
hwaddr *is* the mac address--but it's exactly twice the length of a normal one that you see in windows.  Linux designed it's mac addresses like that to be more secure and capable of handling more in the future.
For the windows equivalent to a mac address, just use the first 12 or so characters.

If you're trying to do mac filtering, though, I've heard that it can be rather difficult--just rumors, though.

---

### Post by Harpoon on 2007-09-03
sounds strange.  1) did you try "ifconfig" without any options?; 2) a second quick check is to apt-get install macchanger, and then run "sudo macchanger eth0 -s".  This is a small app, eth0 or eth1 is the card you are interested in, and -s says show the macaddress and exit.  macchanger --help will give you other commands.

BTW, if you change anything using this utility, they are not permanent and everything will reset when you next boot.

Another question is, does the card work?

---

