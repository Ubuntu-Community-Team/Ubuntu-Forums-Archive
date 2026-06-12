---
title: "access my computer remotly through ssh"
date: 2006-12-26
forum: Absolute Beginner Talk
---

### Post by Mazen on 2006-12-26
does anyone know a HowTo that can lead me to access my computer remotly through ssh, i created a domain but what is the deamon i have to run on my ubuntu sop i can access it remotly, say from a PuTTy?
thanks

---

### Post by bmathis on 2006-12-26
make sure that you installed openssh and you should be able to login after that

```
sudo aptitude install openssh-server openssh-client
```

i know from a windows machine using putty there is a couple of settings that need to be tweaked but i dont know of the top of my head which ones they are and im not in front of a windows machine.

---

