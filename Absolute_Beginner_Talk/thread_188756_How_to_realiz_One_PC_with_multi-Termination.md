---
title: "How to realiz One PC with multi-Termination"
date: 2006-06-04
forum: Absolute Beginner Talk
---

### Post by hycris on 2006-06-04
I've installed Ubuntu 6.06 into my pc. With upgrading, I've 3 keyboard, 3 mouse with 2 LCD. One is in my laptop, there other can plug into the video port. My ATI graphic support multi-screen. At least in windows, I can make it.

I've heard that Ssh can make my laptop as 2 termination. Is that sure? How could I do? Would someone give some advise?

Thank you.:p

---

### Post by cyracks on 2006-06-04
[quote=hycris]
I've heard that Ssh can make my laptop as 2 termination.
[/quote] Don't know what exactly you mean by termination but if you want to run programs from computer A on computer B you should write something like

```

ssh -X root@IPA 'synaptic'

``` where root is the login name, IPA is the IP address of computer you are connecting to and 'synaptic' is the command you want to execute.

btw: you need only one monitor :)

---

