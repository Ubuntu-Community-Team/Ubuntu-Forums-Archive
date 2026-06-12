---
title: "unable to access administration tools"
date: 2006-09-10
forum: Absolute Beginner Talk
---

### Post by psylocat on 2006-09-10
Howdy...I've just installed ubuntu on my leNovo laptop, and when I turned it on today, I was unable to access any of the tools in the administration menu. When I select them, nothing at all appears to happen. Everything outside the administration menu is still accessable, though.

Any suggestions would be greatly appreciated!

---

### Post by taurus on 2006-09-10
What groups do you belong to?  You need to be on both adm & admin in /etc/group!!!

```
id
```

---

### Post by Najand on 2006-09-10
Hmm, have you edit the hostname file  or something similar? 
If not, can you just test the gksudo with something like command synaptic:
```
$ gksudo synaptic
```
and send us the error message?

---

