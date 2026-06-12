---
title: "coonect to the internet help"
date: 2007-03-05
forum: Absolute Beginner Talk
---

### Post by fanny on 2007-03-05
im trying to connect to the internet and i did all the "sudo pppoeconf" and i finish the process . after that i opened the terminal again and wrote on dsl-provider.
i get a message: "so. loaded".
i open the mozilla and i dont see it works what should i do?

*one more thing. now im in xp. usually when im restart i do the next stupid process: open device manager see my lan card is with "!" im disable it and that enable it . and only then i can coonect.

---

### Post by fanny on 2007-03-05
...?

---

### Post by jamyskis on 2007-03-05
Patience is a virtue. It could be that it takes more than an hour to get answer :mrgreen:

[LIST]
[*]Are you using a router?
[*]Are you using AOL?
[*]Can you ping 72.14.207.99?
[/LIST]

---

### Post by cvmostert on 2007-03-05
if you want, you can go to the irc #ubuntu channel... sometimes you get helped there quicker...
i use xchat to do that. sudo apt-get install xchat
i have a cable connection so i can not help you here...

---

### Post by fanny on 2007-03-05
sorry... i was asking the same question yesterday few times and find no answer. 
anyway im using a adsl modem ( tnn 600e) connect to the LAN . 
i dont know how to ping... maybe you can explain

---

### Post by jamyskis on 2007-03-05
> **fanny said:**
> sorry... i was asking the same question yesterday few times and find no answer.

That's fine, but the general rule is that if noone answers, noone knows. It could also be that you've not given much info as to your problem and nobody can be bothered to ask you for more.

> anyway im using a adsl modem ( tnn 600e) connect to the LAN . 
i dont know how to ping... maybe you can explain

Sure - from the terminal (Applications/Accessories/Terminal) type "ping 72.14.207.99" (minus quotes). This is the IP of one of Google's webservers. Alternatively you can just enter 72.14.207.99 into Firefox and see if you get the Google webpage. If you do see Google, or if the Google server returns your ping, then your connection is fine, and you just need to configure some DNS servers so that stuff like [www.google.com](www.google.com) can be translated into IP addresses. We'll cross that hurdle if it comes to it.

If you don't get a return on entering the IP address above, then it may well be that you entered the wrong access details. How do you use your connection under Windows? Does your provider give you a specific program to connect with? It could be that you have to add something to your connection details to get them to work with anything except the provider's own connection client, usually @providerdomain.com (as an example). I don't with Arcor (I'm in Germany), but when I was with T-Online, I did have to add @t-online.de to the end.

The fact that you got to enter your account details suggests to me that the ADSL modem works fine in Ubuntu, otherwise it would have returned an error that no access concentrator points could be found.

---

### Post by fanny on 2007-03-05
hi. i entered the ping "72.14.207.99" and it give me the next message :"from 10.0.0.138 icmp_ seq=1 destination net unreachable."

---

