---
title: "New kernel released"
date: 2006-06-19
forum: Absolute Beginner Talk
---

### Post by Frank Golden on 2006-06-19
Hi All,
  What does the release of the Linux 2.6.17

[http://linux.slashdot.org/article.pl?sid=06/06/19/0138242&from=rss](http://linux.slashdot.org/article.pl?sid=06/06/19/0138242&from=rss)

mean to us Ubuntu users?

Also I noticed in the repositories the only kernel is 2.6.15 where is 2.6.16?
Just curious
Thanks

---

### Post by neoflight on 2006-06-19
[QUOTE=Frank Golden]Hi All,
  What does the release of the Linux 2.6.17

[http://linux.slashdot.org/article.pl?sid=06/06/19/0138242&from=rss](http://linux.slashdot.org/article.pl?sid=06/06/19/0138242&from=rss)

mean to us Ubuntu users?

Also I noticed in the repositories the only kernel is 2.6.15 where is 2.6.16?
Just curious
Thanks[/QUOTE]

i am still using 15...!!! when will it be available in the repos?

---

### Post by Frank Golden on 2006-06-19
Hi Neoflight,
  Wish I knew. Urmas at other forum gave me a link to how to roll your own
kernel.

[http://www.ubuntuforums.org/showthread.php?t=157560&highlight=2.6.16](http://www.ubuntuforums.org/showthread.php?t=157560&highlight=2.6.16)  

Just might give it a try on my 2nd HDD copy of Ubuntu.

---

### Post by debernardis on 2006-06-19
I am presently using the 2.6.17 kernel - the main reason for me to compile a new kernel is that those last dapper 2.6.15.23 and 2.6.16.25 kernels for k7 were configured for SMP, which broke cpu frequency throttling on my athlon.
So I took 2.6.17 from kernel.org, excluded smp and compiled - all seems to work OK (except ati fglrx indeed, which I hope somebody will fix).

---

### Post by bruce89 on 2006-06-19
[QUOTE=neoflight]i am still using 15...!!! when will it be available in the repos?[/QUOTE]
Never, unless you compile it yourself.

---

### Post by PingunZ on 2006-06-19
Lol @ bruce89 
v 2.6.17 or 18 will be included in edgy
ATM you can download the .16 and soon you can download .17 too :)
You can compile it yourself but that kind of hard :)

Grtz PingunZ

---

### Post by Frank Golden on 2006-06-19
[QUOTE=PingunZ]Lol @ bruce89 
v 2.6.17 or 18 will be included in edgy
ATM you can download the .16 and soon you can download .17 too :)
You can compile it yourself but that kind of hard :)

Grtz PingunZ[/QUOTE]
What do you mean ATM you can download......

---

### Post by uzi09 on 2006-06-19
i don't see 2.6.16 in the repos...u have to d/l it from somewhere??
the latest one i see is 2.6.15-25

---

### Post by oyvindaa on 2006-06-19
[QUOTE=Frank Golden]What do you mean ATM you can download......[/QUOTE]

ATM = At the moment

---

### Post by Dakaru on 2006-06-19
I only upgrade kernels if I need support for somthing that isn't supported by my current kernel. As of now, EVERYTHING is working on my 2.6.15 kernel so I see no reason to update.

---

### Post by debernardis on 2006-06-20
[QUOTE=Dakaru]As of now, EVERYTHING is working on my 2.6.15 kernel so I see no reason to update.[/QUOTE]

Is CPU frequency throttling working on 2.6.15 with your Athlon 64? Mine does not :confused:

---

### Post by FredB on 2006-06-20
[QUOTE=uzi09]i don't see 2.6.16 in the repos...u have to d/l it from somewhere??
the latest one i see is 2.6.15-25[/QUOTE]

It seems that kernel 2.6.16 is already in edgy eft repository. So let's way for a backport for dapper ;)

---

### Post by xXx 0wn3d xXx on 2006-06-20
[QUOTE=FredB]It seems that kernel 2.6.16 is already in edgy eft repository. So let's way for a backport for dapper ;)[/QUOTE]
Do you mean the 2.6.17 kernel ?

---

