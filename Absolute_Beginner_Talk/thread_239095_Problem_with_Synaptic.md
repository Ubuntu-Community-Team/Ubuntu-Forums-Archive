---
title: "Problem with Synaptic"
date: 2006-08-18
forum: Absolute Beginner Talk
---

### Post by minipars on 2006-08-18
hi
When i try to open the synaptic...
I get This error:

```
pedro@h4x0r:~$ synaptic
synaptic: error while loading shared libraries: libvte.so.4: cannot open shared object file: No such file or directory
pedro@h4x0r:~$ 

```
any idea?:sad:

---

### Post by minipars on 2006-08-18
```
sudo ln -s /usr/lib/libvte.so.9 /usr/lib/libvte.so.4
```

& Synaptic is back...[IMG]http://ubuntuforums.org/images/icons/icon10.gif[/IMG]

---

### Post by apocalypso on 2006-08-18
I was having the same issue today, so thanks a lot for this fix... I love Ubuntu Forums!!! :-D

---

### Post by teethdood on 2006-08-18
I had the same problem and this fixed it. Anyone know why this happened in the first place?

---

### Post by nedkelly on 2006-08-23
Thanx for the solution.

This [topic ]("http://ubuntuforums.org/showthread.php?t=241666&highlight=libvte.so.4") says something about an Edgy lib got install because of Compiz. That might be the problem

---

### Post by everdred on 2006-08-23
Was having this problem, myself. Thanks, people!

---

### Post by jstroot on 2006-08-25
Thanks all. I love these forums!!!

---

