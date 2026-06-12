---
title: "Gateway ip not pinging"
date: 2006-10-09
forum: Absolute Beginner Talk
---

### Post by sunilsivan on 2006-10-09
i am having a pc of AMD 3000+ and installed both win xp and ubuntu 6.06.  I am unable to ping my gateway address of my router 192.168.1.1.  I am configured my lan card static ip as
ip address - 192.168.1.55
gateway - 192.168.1.1.  
Gateway is pinging on win xp os.
Self ping is possible on ubuntu, but not pinging the gateway ip.
I am a new commer on linux os.  please help

---

### Post by staaka on 2006-10-09
My fist guess, is that your network hasn't been enabled. what is the output when you type "ifconfig" in a terminal? 

At any rate, go to applications>system>networking. and try enabling your network card. One more question, are you able to ping, let's say google.com or any public address?

---

### Post by sunilsivan on 2006-10-09
my lan card is enabled and i am getting ping to my lan card, but unable to ping the gateway address.

---

