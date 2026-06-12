---
title: "Possibly the stupidest help question i will ever: SMTP question really?"
date: 2005-05-20
forum: Absolute Beginner Talk
---

### Post by steve k on 2005-05-20
so:
i'm sure this is going to make me look sooo stupid.  soo stupid...
i'll just get it over with: i use thunderbird to read my mail so, when i installed ubuntu on this computer it was one of the first things i set up on here as well.

i copied over all my folders and set up all my accounts just as i had them set up on my other two plain old debian systems.

this worked fine for a while, and then maybe two days ago i stopped being able to reach my isp's smtp server through thunderbird.  i get the standard 'this server might be down or not accepting connections' etc. thing.

but when i turn 10degrees to my left and try this out on my other laptop with thunderbird configured exactly the same, it works just fine.  the server is reached and  the settings, ports etc. are all the same.  

i'm just totally baffled about what this could be.  it's not the ports it's not the smpt server or the network, they're all using the same ports, everything is set up exactly the same...

is there some sort of ubuntu default setting that's blocking those ports? some thing that might have come in with a security update?

i'm just totally puzzled.

---

### Post by ape on 2005-05-20
You didn't install firestarter or set up iptables at all did you?

---

### Post by steve k on 2005-05-20
no.
i never have either (at least no knowingly).  will installing those things help?  what do they do?

---

### Post by ape on 2005-05-20
Firestarter is an application to help you set up iptables firewall rules on your machine.  I was wondering if you had installed this, as when I tested Firestarter out it blocked access to my entire net. 

Can you traceroute to your SMTP server IP?

---

