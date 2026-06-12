---
title: "Hamachi connection"
date: 2006-04-27
forum: Absolute Beginner Talk
---

### Post by jer4202 on 2006-04-27
My windows box runs a server called something like "my server" and the password is "password" (for example purposes). Well when I boot into Ubuntu and try to connect to the "my server" network, it says that it doesnt exist. Could this be because "my server" is 2 words?
     The command to connect to a Hamachi server in linux is something like 
Hamachi join existing NETWORK PASSWORD .... I assume that network is the name of the network, space, password. But since my network name is 2 different words, is it able to connect.
     Thx for any info

---

### Post by NetOS on 2006-05-19
Yes Jer4202, Hamachi probably gets the first word for the network and uses the second for the password, wich will obviously not work :D

try it that way:
hamachi join "my network" password

the two " should stop hamachi from separating the network name.

Hope it helps.
Cheers

---

### Post by it.henrik on 2006-05-19
ghamachi is a gui for hamachi .. :)

---

