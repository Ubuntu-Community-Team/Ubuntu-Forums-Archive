---
title: "My version of Ubuntu?"
date: 2007-03-24
forum: Absolute Beginner Talk
---

### Post by nicdal on 2007-03-24
What bash command will give me my version of Ubuntu ?:confused:

---

### Post by SpikeyB on 2007-03-24
I'm sorry I don't know the answer to your question.  However, if it's of any use, I found my version by clicking Menu/Start button>System>About Ubuntu

---

### Post by HereInOz on 2007-03-24
If you want to know the version of the Kernel which you are running, try:

uname -r

---

### Post by scxtt on 2007-03-24
i don't believe there is a CLI command that will give you something like "you're using {breezy/dapper/edgy}" ... the best you can really do is get your kernel version and narrow it down from there ... also, this is kinda helpful: **cat /proc/version** but i'm using Kubuntu Edgy 6.10 - i doubt i'll find that specifically anywhere, aside from what SpikeyB mentions ...

---

### Post by zvacet on 2007-03-24
system>about ubuntu

---

### Post by 23meg on 2007-03-24
[QUOTE=scxtt]i don't believe there is a CLI command that will give you something like "you're using {breezy/dapper/edgy}"[/QUOTE]

There is:

```
lsb_release -a
```

---

### Post by nicdal on 2007-03-24
> **23meg said:**
> There is:

```
lsb_release -a
```

Many thanks 23meg, it works nicely.

---

### Post by Paul_world10 on 2007-03-24
[HTML]uname -a[/HTML]  might be an option for you to try.

---

### Post by scxtt on 2007-03-24
> **23meg said:**
> There is:
```
lsb_release -a
```cool, good info ... :)

---

