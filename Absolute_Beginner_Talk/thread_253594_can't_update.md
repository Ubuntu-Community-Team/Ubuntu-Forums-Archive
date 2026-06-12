---
title: "can't update"
date: 2006-09-08
forum: Absolute Beginner Talk
---

### Post by Devile on 2006-09-08
there's one update available but it won't work:

E: /var/cache/apt/archives/vim_2%3a0.20060517T160422_i386.deb: trying to overwrite `/usr/bin/xxd', which is also in package vim-common

---

### Post by Kobalt on 2006-09-08
Hello,

Have you tried launching Synaptic and selecting "Repair broken packages" in the "Edition" menu ? 
If it's not working you can try this, in command line : 
```
sudo aptitude update -f
```

Cheers !

---

### Post by Devile on 2006-09-08
tried both terminal said fix problem and the other one said problems fixed...  and still don't work
still same error

---

