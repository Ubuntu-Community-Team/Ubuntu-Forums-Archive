---
title: "apt-get WARNING"
date: 2007-09-26
forum: Absolute Beginner Talk
---

### Post by larry Gaminde on 2007-09-26
Everything I try to install today says this Why

WARNING: The following packages cannot be authenticated!
  firestarter
Install these packages without verification [y/N]? y

---

### Post by Linux_Man on 2007-09-26
Chances are your on a weak (or rouge) connection and it only "knows" that your on a connection but can't connect. Happend to me when I was on a live-CD messing around. I would say no to it and check out your connection. It could be a "pay to go online" wi-fi spot or somthing similar. Open up your favorite web browser and try to connect to a site, if it goes to the correct site, try reinstalling it, if not, then connect to a different connection.

---

### Post by mcduck on 2007-09-26
> **larry Gaminde said:**
> Everything I try to install today says this Why

WARNING: The following packages cannot be authenticated!
  firestarter
Install these packages without verification [y/N]? y

Have you added some extra repositories? It seems that you are missing authentication key to some repository..

It's not any serious problem, if you trust maintainers of all repositories you are using you can just ignore that warning.

(And no, that has absolutely nothing to do with the quality of your network connection :))

---

### Post by Pumalite on 2007-09-26
I agree; those are probable new repos added to sources.lst.

---

