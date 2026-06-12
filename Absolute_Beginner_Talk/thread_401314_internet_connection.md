---
title: "internet connection"
date: 2007-04-04
forum: Absolute Beginner Talk
---

### Post by Undead on 2007-04-04
Hy, y am Undead from Romania and y am a new user of ubuntu......

On my Win XP y have a pppoe internet connection and y don't know how to connect to the internet on linux...can u help me? ..pls :( 

P.S. pls send me an email at [email]undeadking20@yahoo.com[/email] ..... tx  :) (any solution or link that can help me)

---

### Post by mendingo84 on 2007-04-04
salut. deschizi un terminal si acolo tastezi:
> 
sudo pppoeconf


apoi trebuie doar sa citesti ce scrie acolo ;) . sa iti notezi undeva contul si parola ca sa le poti introduce.
apropos...pe forumul asta ti se va raspunde destul de prompt asa ca nu e nevoie sa ti se trimita mail ;)

---

### Post by zvacet on 2007-04-04
system>administration>network setting>highlight your modem>properties>choose your type of connection(dhcp,static)>chek upper left box>close>DNS tab>replace address you found with your nameserver>close
```
pppoeconf
```

---

