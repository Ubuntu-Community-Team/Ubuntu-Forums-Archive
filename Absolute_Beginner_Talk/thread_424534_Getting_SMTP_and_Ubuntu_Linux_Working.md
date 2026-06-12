---
title: "Getting SMTP and Ubuntu Linux Working"
date: 2007-04-26
forum: Absolute Beginner Talk
---

### Post by JJNova on 2007-04-26
After carrying on discussion with other members in the IRC Channel, and doing numerous searches through both Google and Yahoo, we have found an answer to the problems associated with receiving emails through an SMTP server. In my case, I was having a problem connecting to both HotPOP and my websites server. 

After testing the connection using
```
telnet mail.gamecootie.com 25
```

We found that some of us could connect, and others couldn't. The results? SBC users were being blocked. The problem is with SBC, SBC Global, and Yahoo SBC Global having port 25 blocked. The problem was easily fixed by just contacting their live support website, chatting with a tech, and requesting the port be unblocked for the account. A simple solution, but one that's not readily available online. 

Hopefully this will help anyone that's searching for ' SMTP block port 25 Feisty Ubuntu '.... such as I was.

Much thanks goes to Linxer, eck, thingy,and numerous other people from IRC for problem shooting with me. 
I'm not sure if this should of been posted in 'General Help', 'Servers & Security', or here in 'Absolute Beginners', but as long as someone uses the search function, I suppose it doesn't matter.

---

