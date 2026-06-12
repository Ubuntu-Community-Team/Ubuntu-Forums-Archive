---
title: "new Ubuntu install can't connect to internet"
date: 2007-04-07
forum: Absolute Beginner Talk
---

### Post by dinosoup on 2007-04-07
I just formatted my other WinXP computer and installed Ubuntu 6.10 Desktop Edition. After install was complete, I configured the network settings (static ip, subnet and gateway). It's connected to a router.

Now I can't connect to the internet. But when I tried connecting to my main computer's web server by directly typing its network address it worked.

I don't know what's wrong, I double checked the settings.

Any ideas?

---

### Post by zvacet on 2007-04-07
After choosing type of connection(static in your case)>close.DNS tab>put your nameserver
```
pppoeconf
```

---

