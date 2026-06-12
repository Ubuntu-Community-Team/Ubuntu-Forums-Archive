---
title: "[SOLVED] Synaptic Package mang will not open"
date: 2008-04-11
forum: Absolute Beginner Talk
---

### Post by timetoballj on 2008-04-11
this is the message i get E: Type '--02:23:17--' is not known on line 1 in source list /etc/apt/sources.list.d/medibuntu.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.

---

### Post by Saint Angeles on 2008-04-11
can you disable your medibuntu repository in 'software sources" ?

---

### Post by timetoballj on 2008-04-11
yes

---

### Post by timetoballj on 2008-04-11
i need some serous help with i will hate to reinstall

---

### Post by Oldsoldier2003 on 2008-04-11
> **timetoballj said:**
> this is the message i get E: Type '--02:23:17--' is not known on line 1 in source list /etc/apt/sources.list.d/medibuntu.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.
System>administration>software sources:
enable the repos on the first tab. then:

```
sudo rm /etc/apt/sources.list.d/medibuntu.list
sudo apt-get update
sudo apt-get upgrade
```
you added the medibuntu repo incorrectly, if you look at the actual file referenced you'll probably see that its a html page that used to be the medibuntu repo directory. There are quite a few old tutorials out there that cause this issue

---

### Post by timetoballj on 2008-04-11
thanks that worked

---

