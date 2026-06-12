---
title: "internet probs"
date: 2005-07-08
forum: Absolute Beginner Talk
---

### Post by volleyfoc24 on 2005-07-08
I am installing the unbuntu OS onto a comp that is connected via comcast cable connection
I pulled a stupid and made up an address when it asked for a network address, I think this is why the comp will not get on the internet, can anyone tell me what to do

---

### Post by Kvark on 2005-07-08
Open the network tools (under system tools in the menu). Select your cable connection under the units tab and click configure. Change the configuration to DHCP.

(translated the names from swedish so some words may be different for you)

---

### Post by volleyfoc24 on 2005-07-09
how do u change from swedish the linux is in english
i activated the ethernet card and did that still nothing

---

### Post by drummer on 2005-07-09
[QUOTE=volleyfoc24]how do u change from swedish the linux is in english
i activated the ethernet card and did that still nothing[/QUOTE]
 Kvark would have Ubuntu in Swedish (I think the language can be selected right at the start of installation) and is translating what he sees (Swedish) on his screen to English.

---

### Post by drummer on 2005-07-09
[QUOTE=volleyfoc24]how do u change from swedish the linux is in english
i activated the ethernet card and did that still nothing[/QUOTE]
 To edable DHCP --> click the ethernet card, then the properties button to the right, then next to connections select DHCP from the drop-down menu. After that click activate and it should work *fingers crossed*

---

### Post by volleyfoc24 on 2005-07-09
i have already enable dhcp but the prob may be the ethcard is plugged into a d-link cable modem
is there a way to fix it

---

### Post by drummer on 2005-07-09
Sorry, I don't really know about connecting directly to a cable modem, but try in a shell: ```
sudo ifup eth0
``` (this is the command to configure/activate network interfaces, if it's already configured, run "sudo ifdown eth0" first so you can se the output of ifup) and have a look at the output to see whether DHCP is successfully resolving an IP for you. 

Also, is the address you initially set for the ethernet card? or for the modem, when you were setting that up?

---

