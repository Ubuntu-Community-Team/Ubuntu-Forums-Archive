---
title: "wireless not working! HP slimeline s3200 AMD athlon 64 x2"
date: 2008-04-17
forum: Absolute Beginner Talk
---

### Post by khaku2 on 2008-04-17
the wireless was working but now it has failed to start multiple times after restart.
please help, my computer is not able to connect without the wireless Internet.
I am running ubuntu 7.10 gutsy gibbon with no other OS I ditched vista for ubuntu. 
Please help me, I have basic knowledge with the terminal app and that's about it.

---

### Post by wolfen69 on 2008-04-17
what kind of wireless is it?

---

### Post by meborc on 2008-04-17
you had your wireless working? what did you do to make it stop? did you install something? did you change some conf files?

what is your wireless card mark and model? have you upgraded your machine recently?

type this in terminal to find out the mark of wifi card:
```
lspci
```

sorry for all the questions, but it is difficult to help without knowing some background info :)

---

### Post by khaku2 on 2008-04-17
> **wolfen69 said:**
> what kind of wireless is it?

It is built in on the motherboard
its not a card

---

### Post by khaku2 on 2008-04-17
> **meborc said:**
> you had your wireless working? what did you do to make it stop? did you install something? did you change some conf files?

what is your wireless card mark and model? have you upgraded your machine recently?

type this in terminal to find out the mark of wifi card:
```
lspci
```

sorry for all the questions, but it is difficult to help without knowing some background info :)

I just installed my restricted driver for the nvidia card I have, works fine

I am at school so I will check it out to find the adapter for the wifi

---

### Post by khaku2 on 2008-04-17
Ok I ran ran lscpi and I could not see anything that resembled wireless Internet at all...

---

### Post by khaku2 on 2008-04-17
ok solved it. I went to network interfaces and deleted everything except the "lo" entries

Wireless is up and running

---

### Post by khaku2 on 2008-04-17
ok not solved it started for just a little while and It eventually ceased
I tried a full restart and still not starting wireless

---

