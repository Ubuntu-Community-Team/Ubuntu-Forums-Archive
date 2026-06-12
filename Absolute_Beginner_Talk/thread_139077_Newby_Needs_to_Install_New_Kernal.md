---
title: "Newby Needs to Install New Kernal"
date: 2006-03-03
forum: Absolute Beginner Talk
---

### Post by sony102600 on 2006-03-03
Hi All, I recently install ubuntu on my AsRock 939 Dual Sata II motherboard with built it in ethernet, and that network card doesn't seem to be supported in my version of ubuntu.

After much reading, I found other users having the same issues... apparently the best way to fix the problem is to install the newest kernal build (apparently 2.5 and after works)...

Any help on doing this without having an internet connection (in ubuntu, I have a connection in windows..and an external hard drive I can save stuff to and read in ubuntu.)???

---

### Post by firehead on 2006-03-03
what version of ubuntu did you install?
> apparently the best way to fix the problem is to install the newest kernal build (apparently 2.5 and after works).
afaik (k)ubuntu breezy comes with a 2.6-kernel...is it possible that you installed hoary on your machine?if so, you could just dl the newest breezy-cd and give it a try...

---

### Post by sony102600 on 2006-03-03
how can I check to see what kernel I am currently running?

---

### Post by george_apan on 2006-03-03
Open a terminal window and type
```
uname -r
```

---

### Post by sony102600 on 2006-03-03
NO!!!!!!!!!!!!!!!

I have version 5.6.12 or something, and I am now back to having absolutely no idea how to get my ethernet up and running....

could having the amd 64 version have something to do with it?

---

### Post by george_apan on 2006-03-06
[QUOTE=sony102600]NO!!!!!!!!!!!!!!!

I have version 5.6.12 or something, and I am now back to having absolutely no idea how to get my ethernet up and running....
[/quote]
There is no such kernel. Please check again and post the exact output. Maybe it is 2.6.12-xx-xxx? If it is I then you have the latest (stable) kernel anyway.
[QUOTE=sony102600]could having the amd 64 version have something to do with it?[/QUOTE]
I don't think so.

---

### Post by nixclusive on 2006-03-06
You can also try
```
cat /proc/version
```

and post the output here.

---

