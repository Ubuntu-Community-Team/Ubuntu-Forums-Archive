---
title: "internet connection"
date: 2006-12-21
forum: Absolute Beginner Talk
---

### Post by tanmay666 on 2006-12-21
can ne one give the exact syntax for configuring internet connection. also i have sify internet connection which is DSL

---

### Post by jhenager on 2006-12-21
Assuming your network device is recognized by Ubuntu, you should be able to go through Administration>Networking and verify that Eth0 is active. If it isn't, then you highlight it and click the button to activate the interface.
From the terminal, the command is sudo ifup Eth0.

To check from the terminal, sudo ifconfig -a

---

### Post by EminNew on 2006-12-21
I used:

```
pppoeconf
```

Answered all questions with "yes" (except username, password and "automatic connect on boot" - this caused problems for me, but may not for you).

Then you can use:

To connect
```
pon dsl-provider
```   

To check connection
```
plog
```

To disconnect 
```
poff
```

---

