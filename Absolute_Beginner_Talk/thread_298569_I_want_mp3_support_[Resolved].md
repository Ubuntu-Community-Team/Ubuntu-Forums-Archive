---
title: "I want mp3 support [Resolved]"
date: 2006-11-12
forum: Absolute Beginner Talk
---

### Post by lordvolo on 2006-11-12
I want mp3 support for Xubuntu i was reading and it said to get this plugin:
libxine-extracodecs  but i dont know the terminal code or how to get it

---

### Post by faraazs on 2006-11-12
> **lordvolo said:**
> I want mp3 support for Xubuntu i was reading and it said to get this plugin:
libxine-extracodecs  but i dont know the terminal code or how to get ittry this:```
sudo apt-get install libxine-extracodecs
```

---

### Post by aysiu on 2006-11-12
You're going to have to [enable extra repositories](http://www.psychocats.net/ubuntu/sources) first.

Then this command will install *libxine-extracodecs*--you can just paste it into [the terminal](http://www.psychocats.net/ubuntu/terminal); no need to retype it: ```
sudo aptitude update && sudo aptitude install libxine-extracodecs
```

---

### Post by lordvolo on 2006-11-13
it worked thanks!

---

