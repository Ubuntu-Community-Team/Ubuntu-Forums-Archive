---
title: "how to update only from official repository, excluding 3rd party repository"
date: 2008-01-31
forum: Absolute Beginner Talk
---

### Post by cyneuron on 2008-01-31
hi there

most people add 3rd party repository to install a specific software. for example if i add getdeb.net repository, i may want only a specific software from it, not all.

but when update manager updates the system it also offers to install updates from the 3rd party repository.

Is there any way to make update manager ignore the 3rd party repository, and update only from official or specific repository ?

---

### Post by forestpixie on 2008-01-31
edit your sources.list and comment out what you want it to ignore with #

```
 gksudo gedit /etc/apt/sources.list
```

---

### Post by Seisen on 2008-01-31
You could alway's comment out the line in your /etc/apt/sources,list. by adding this "#" in front of the repository you dont want to download from.

---

### Post by philinux on 2008-01-31
> **cyneuron said:**
> hi there

most people add 3rd party repository to install a specific software. for example if i add getdeb.net repository, i may want only a specific software from it, not all.

but when update manager updates the system it also offers to install updates from the 3rd party repository.

Is there any way to make update manager ignore the 3rd party repository, and update only from official or specific repository ?

Just curious. Why would you not want the latest update to an application even if it is from a 3rd party repo. It could be a security update, bug fix or an advancement.

---

### Post by cyneuron on 2008-02-01
sorry. you got it wrong guys.

i also know to uncomment it in source list. what i meant was that its cumbersome everytime to exclude it from source list.

isn't there any way to make update manager ignore specific repository while simultaeously keeping it enabled it synaptic package manager.

And i want to do this, because i may not want to update my whole system from unofficial repo. i may be just wishing to install one software only from specific repo.

---

### Post by shae on 2008-02-01
[http://jaqque.sbih.org/kplug/apt-pinning.html]("http://jaqque.sbih.org/kplug/apt-pinning.html")

This is written for debian but also applys to Ubuntu.  Just make sure to change the repository names.

---

### Post by Rob_1975au on 2008-02-13
My ISP has announced:

[I][COLOR="Blue"]Ubuntu Repository Updates
Wednesday, 23rd January

Based on user feedback, we've added the Ubuntu sources to our [Ubuntu repository]("http://mirror.gamearena.com.au/")!

Thanks to all those who have taken the time to provide feedback for this new service. We've had a lot of interest in it and we're looking forward to expanding on it as soon as possible.
[/COLOR][/I]

I get uncounted downloads from my ISP this way.
Do I just edit the sources.list to facilitate this?

---

