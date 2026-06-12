---
title: "can't configure my network"
date: 2005-11-04
forum: Absolute Beginner Talk
---

### Post by thefreak on 2005-11-04
i've instaled linux ubuntu and manualy setup the network as i had it in windows xp (ip,subnet mask, gateway,dns)
it seems that i'm able to do updates but i cant't acces web pages and i can't see other computers from the network
pls help
10x

also the other computers uses windows xp

---

### Post by LHZ on 2005-11-04
I'm not sure what's wrong with your network. Have you tried pinging various websites? You can do so by typing

> ping -c10 [www.google.com](www.google.com)

into a terminal. ping tells you how long it took to get response from a certain website or computer (in this case google.com), and it'll also tell you if it can't find website or computer. (-c10 means you do 10 attempts, and average).

Also to connect Winodws and Linux computers to each other, the Linux computer will need to run SAMBA. See here:

[http://www.ubuntuguide.org/#sambaserver](http://www.ubuntuguide.org/#sambaserver)

---

### Post by thefreak on 2005-11-04
yes my network computers reply to ping but from websites i get no answer
i also shared a folder using samba

---

