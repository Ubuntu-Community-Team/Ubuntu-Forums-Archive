---
title: "Hey Guys..I am a newbie.. need your help.."
date: 2006-01-24
forum: Absolute Beginner Talk
---

### Post by harry_griet on 2006-01-24
Hi everyone....

This is hari...
I have recently installed Kubuntu 5.10.... I have problems configuring the network setting....I hae tried it for a week but But i get the error cannot connect to the port in the web browser...I tried to connect to the link provided by the ISP.. Because its from where i can get my log in client...

SO please guys can anyone help me out..please brief me with what should be entered at what place in configuring the network settings....[-o< 

Waiting for your help guys!!!!!!!!!!!!!! BYE

---

### Post by Mustard on 2006-01-24
What details can you give on the type of connection you have, the type of network card, what ISP you are with?

---

### Post by chimera on 2006-01-25
If you have a broadband connection, just open a terminal(applications>accesories>terminal) and type
```
sudo pppoeconf
```
after that, you will be prompted for your user password(the one you selected when you installed ubuntu). Enter it, and keep clicking yes. When you get the first textbox, enter the username you use to connect to the internet, and when you get the second one, enter your password, then continue clicking yes. After the new yesno windows stop appearing, you should be connected.

---

### Post by harry_griet on 2006-01-26
[QUOTE=Mustard]What details can you give on the type of connection you have, the type of network card, what ISP you are with?[/QUOTE]

Actually..I am from India I am using a shared broadband connection..SIFY..And about the network card.i Think its "ETH0".......

---

### Post by qwazert on 2006-01-26
I also have a broadband connection and even though I've never been prompted for any account information, I have been able to connect to the Internet.

Does it make a difference that I had the cable-modem connected during the install?

---

### Post by cotcot on 2006-01-26
Is your network card activated ? (see > system > administration > network) . There you can also see the number of your card (probably eth0)

---

### Post by depu on 2006-02-18
Hey Hari i use sify too, and i tried the client that they had put up it runs fine but asks for an upgrade and then logs me out.apparently sify needs to upgrade the client to version 3 the one they have there is 1.3. so i simply log into windows and log in from there and then remove the lan cable from behind and reboot into Ubuntu and reattch the cable and surf thru there coz sify doesnt think that i have logged out  ;) :)  real dumb way around it but thats all i cud come up with .....

---

