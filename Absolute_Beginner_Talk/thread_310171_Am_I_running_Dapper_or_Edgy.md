---
title: "Am I running Dapper or Edgy?"
date: 2006-11-30
forum: Absolute Beginner Talk
---

### Post by thelocust on 2006-11-30
**[SIZE="2"]How do I find out if I am running Dapper or Edgy with out checking my repositories. I installed Ubuntu under the impression it was Dapper and I copied my old repositories over with out thinking twice. Now I have a widget on my desktop that says I am running Edgy. So I just want to double check so that I can fix my repositories. Thanks. [/SIZE]**8)

---

### Post by Epperly on 2006-11-30
System>About Ubuntu

---

### Post by thelocust on 2006-11-30
**[SIZE="2"]Sorry I forgot to say I am running kubuntu.[/SIZE]**

---

### Post by LLRNR on 2006-11-30
In a terminal:
```
uname -a
```

LLRNR

---

### Post by thelocust on 2006-11-30
```
uname -a
```

This didnt work all I got was:

```
Linux mybox 2.6.15-27-386 #1 PREEMPT Sat Sep 16 01:51:59 UTC 2006 i686 GNU/Linux
```
:confused:

---

### Post by LLRNR on 2006-11-30
Whoops!! :D Sorry I messed up a little - I was rather thinking of the kernel release you use, which is displayed with uname -a (or better with **uname -r**)... 

Sorry, anyway you can find out if you're running Dapper or Edgy, for example, by viewing your sources.list file: **cat /etc/apt/sources.list**, and if you see there more "edgy"s then "dapper"s then it's most likely you're running Edgy rather than Dapper and viceversa :D

LLRNR

---

### Post by thelocust on 2006-11-30
> **thelocust said:**
> How do I find out if I am running Dapper or Edgy with out checking my repositories (source.list). I installed Ubuntu under the impression it was Dapper and I copied my old repositories over with out thinking twice.

I replaced my source.list already with my old one.

---

### Post by speedman on 2006-11-30
cat /etc/issue


Regards,

SM

---

### Post by d3v1ant_0n3 on 2006-11-30
Jugding from your kernel version, I'd * guess* that you're running dapper. Edgy ships with 2.6.17, no?

A quick way to check would be by switching to a virtual terminal (CTRL+Alt+F1)- the name of the release will be above the prompt. You can switch back with CTRL+ALT+F7

---

### Post by thelocust on 2006-11-30
[SIZE="2"]**Thanks, I'm running Dapper. I had to reboot but I got the answer I was looking for. Thanks d3v1ant_0n3 and LLRNR for the help.**[/SIZE]:mrgreen:

---

