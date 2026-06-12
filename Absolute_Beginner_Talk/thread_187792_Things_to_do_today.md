---
title: "Things to do today"
date: 2006-06-03
forum: Absolute Beginner Talk
---

### Post by bobpur on 2006-06-03
I got Dapper installed after some iso/cd burning issues were corrected. Some things that need fixed are;

 1). Sound-- No surprise there as I read on the Creative Labs site that X-Fi cards weren't expected to be supported until sometime in the second quarter of 2007. I do have an Audigy 4 soundcard I want to use. Does anyone know if it'll work? I did not see anything about it on the HCL.

2). Enabling the multiverse and universe-- How do you do that in Dapper? I found out how to do it in Breezy but didn't save the info.

Thanks

---

### Post by bluevoodoo1 on 2006-06-03
I don't know anything about sound cards, but here's for your repo question... [https://wiki.ubuntu.com/AddingRepositoriesHowto](https://wiki.ubuntu.com/AddingRepositoriesHowto)

---

### Post by bobpur on 2006-06-03
bluevoodoo1,
Thanks for the response but that method didn't work. From System>administration>Synaptic Package manager>settings>repositories>?
No User Interface dialog box. It goes straight to the Synaptic dialog box and there is no settings button at the bottom.

---

### Post by confused57 on 2006-06-03
[QUOTE=bobpur]bluevoodoo1,
Thanks for the response but that method didn't work. From System>administration>Synaptic Package manager>settings>repositories>?
No User Interface dialog box. It goes straight to the Synaptic dialog box and there is no settings button at the bottom.[/QUOTE]

Try clicking the "Add" button at the top right after doing the above, then 
add multiverse and universe for each(there are 3) manually by checking them & add each individually...if that makes any sense.  It's the same method as in the FAQ for Breezy, which does not seem to be working "Not Found".

Manually:

```
sudo etc/apt/sources.list
```
sorry, it's:
```
sudo gedit /etc/apt/sources.list
```
and uncomment  the repositories.

---

