---
title: "Internet"
date: 2007-08-22
forum: Absolute Beginner Talk
---

### Post by Wintu on 2007-08-22
I have a well... serious problem. I´m currently using Windows and I would like to switch to Ubuntu but I don´t know how to connect to the internet there. I´v tried the Live CD. But the problem is that I´m connected to a network so I don´t need to connect every time that I log-in, I just go to the internet. The thing is that I don´t know how to set-up the IP address and the gateway and everything in Ubuntu. Some one help me please.

---

### Post by toidi on 2007-08-22
Goto System>Administration>network select your network card and then click properites.  This will allow you to change the settings you need.

I don't know if these settings will be stored using the live cd, you might have to set it up each time you boot.  They will store on an install though.

---

### Post by deadgobby on 2007-08-22
If the live CD hit the internet. There is nothing to be done. To test it, just have the internet go on search a topic. Of you get no server is found. Then you need to do above.
Gobby

---

### Post by Wintu on 2007-08-22
Did as you said. Inserted the IP address, gateway code and everything. Then I went to the server thing section and inserted the codes for the connection and nothing. I go to Mozilla and insert the URL "www.google.com" and it doesn´t respond. Something I did wrong'

---

### Post by toidi on 2007-08-22
I am still new to linux so not sure if I can help very much on this.
Firstly more information on what kind of network you have, is it wired or wireless?
Do you know the name of the wired/wireless card in your pc?
Do you have to login to a domain in order to get connected to the internet?

Some info on these will help others give you the best advice on what to do next.

---

### Post by Wintu on 2007-08-22
I have a wired DSL connection. I do not need to input a domain. Any and all other information is unknown to me.

---

### Post by diffuze on 2007-08-22
You need to specify a nameserver as well, if you didn't do that already.
What response do you get when you type 'ping google.com' in a console?

---

### Post by Wintu on 2007-08-22
Pardon me if I do not understand, but what console?

---

### Post by splintercellguy on 2007-08-22
System -> Administration -> Terminal, and how exactly are you hooked up to the Internet?

---

### Post by Wintu on 2007-08-22
Oh, the terminal. Yes, I typed that in. There was not a response. I am connected to the internet using a DSL modem hooked up with a server. I insert in the IP address, the gateway and everything else including the server codes and I can´t receive a internet connection. But it works in Windows though.

---

### Post by schorsch on 2007-08-22
Please post the output of the following commands in the terminal:
```
ifconfig -a
netstat -nr
cat /etc/resolv.conf
ping 82.211.81.158
```
.... yes, it is the IP of [www.ubuntu.com](www.ubuntu.com) as there are more than one IP  for [www.google.com](www.google.com) ... I hope [www.ubuntu.com](www.ubuntu.com) has just one IP ;-)

---

