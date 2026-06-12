---
title: "kernel version"
date: 2008-03-08
forum: Absolute Beginner Talk
---

### Post by johnwen on 2008-03-08
:oops:

I'm embarrassed to ask this BUT how do I tell which kernel version I have installed.  I have Ubuntu Feisty 7.04 with all current updates and am trying to get pvrusb2 driver setup via Mike Isely's site.
Thanks 
John

:guitar:

---

### Post by kayvortex on 2008-03-08
enter:
```
uname -r
```

---

### Post by johnwen on 2008-03-08
:)
Thank you, thank you.

---

### Post by kayvortex on 2008-03-08
That's ok! "uname" will give you other bits of info, and you can also peruse the contents of the /proc directory. For example, you could have also entered:
```
cat /prov/version
```
(Note: the files in proc should be read with cat for reasons I won't go into).

---

### Post by blastus on 2008-03-08
You can also get the kernel version by going to System->Administration->System Monitor and selecting the System tab.

Edit: I should have read that you were using Feisty. The above may work in Feisty but it works for sure in Gutsy.

---

