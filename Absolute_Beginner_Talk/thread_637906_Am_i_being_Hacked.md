---
title: "Am i being Hacked???"
date: 2007-12-11
forum: Absolute Beginner Talk
---

### Post by someoneouthere on 2007-12-11
while i was surfing on the internet and listening radio the music suddenly stopped and i heared the modem on my laptop dialing somewhere!!!(although i'm on dsl)
i haven't installed any programms except the repositories and i dont use p2p.....
any ideas?

---

### Post by PhoenixP3K on 2007-12-11
I never heard of malware on Linux (too small of an audience to attack?), but I would suggest disabling your modem from the Network Settings, of course you can also not have the phone line connected if your using DSL (unless you have it connected for fax?)

---

### Post by omegamike3 on 2007-12-11
Keeping it off the phone line, if that is the case, would definitely be a good idea.

---

### Post by someoneouthere on 2007-12-11
ok understood but how someone is able to do that when i don't take "risks"?

---

### Post by Rocket2DMn on 2007-12-11
I wouldn't imagine that somebody is trying to hack your computer and dial out on a modem.  It's possible that some program on your computer running in the background looks to the modem network interface rather than your DSL, so when it activates it tried to dial in to establish a connection.

---

### Post by someoneouthere on 2007-12-11
so how can i check it out?

---

### Post by Rocket2DMn on 2007-12-11
Honestly, I don't really know, I guess you would just have to use some intuition.  You could start by checking logs in the /var/log directory, like the syslog file.  Otherwise if you don't use your modem, you could disable it by going to System->Administration->Network, clicking Properties on the modem and unchecking the enable box.

EDIT: You can also check logs from System->Administration->System Log

---

### Post by OffAxis on 2007-12-12
you can check the access log on your router.

the next time it happens you can use 
```
top
```

to see what processes are running.

Your router's firewall should be blocking ports sufficiently (you do have a router/firewall in place, right?) that someone can't get in uninvited, so like Rocket2DMn suggested, it's probably a program that thinks it should use the modem to connect (particularly if it dropped your dsl connection to do so).

---

