---
title: "Kernel"
date: 2006-12-26
forum: Absolute Beginner Talk
---

### Post by huviduc on 2006-12-26
how can i figure out what kernel version i have? thank you. i am using a compaq presario V2000 if that matters

---

### Post by halitech on 2006-12-26
I want to say open a terminal and type

```

whoami

```

but I'm not on my box at home so not sure if I'm right or not

---

### Post by Regel on 2006-12-26
I would try 
```
uname -r
```
instead of "whoami".

```
regel@potkustartti:~$ whoami
regel
regel@potkustartti:~$ uname -r
2.6.17-10-generic
regel@potkustartti:~$ 

```

---

### Post by halitech on 2006-12-26
thanks Regal, I forgot about the uname command and couldn't remember for sure what whoami would give. guess whoami should have been more self explanatory :(

---

### Post by huviduc on 2006-12-26
ok, so i figured out that this is my kernel, 2.6.15-27-386, but i am tryin to follow these
[http://doc.gwos.org/index.php/BerylXglOnDapper](http://doc.gwos.org/index.php/BerylXglOnDapper) directions and it doesnt seem like what i am looking for. I have an atholon turion 64 processor. It is listed as a K8 athlon/Opteron under my device manager. Should i i be trying to run this command" sudo apt-get install linux-k8"? or something different?

---

