---
title: "automatic updates"
date: 2008-03-07
forum: Absolute Beginner Talk
---

### Post by maxhoward on 2008-03-07
I haven't gotten any updates (security fixes, bug fixes, new features, etc) in several weeks.  I have run System>Admin>Update Manager and it reports that my system is up-to-date.  So is it possible that there really have been no updates for me in the last 3 weeks after getting them at least weekly before that?

---

### Post by Oldsoldier2003 on 2008-03-07
> **maxhoward said:**
> I haven't gotten any updates (security fixes, bug fixes, new features, etc) in several weeks.  I have run System>Admin>Update Manager and it reports that my system is up-to-date.  So is it possible that there really have been no updates for me in the last 3 weeks after getting them at least weekly before that?
possible. but is it true, probably not. run:

```
sudo apt-get update
```

and likely you'll be prompted by update manager shortly thereafter. your package lists probably aren't up to date.

---

### Post by Papa-san on 2008-03-07
This all depends on the programs you have installed on your system...

Yes, It is quite possible to have no updates for a while. I think I went over two months at one point!

If your internet connection works, and you don't receive errors stating that you aren't connecting with the servers, then your system likely IS up to date... :-D

---

### Post by taurus on 2008-03-07
Maybe because you don't have any repos enable in /etc/apt/sources.list so there is nothing to check with.

System -> Administration -> Synaptic Package Manager -> Settings -> Repositories and make sure there is a check mark in front of the first four lines except the last one, Source code, and the Cdrom in the window below.  Close it and click Refresh.  Now, shutdown synaptic and run

Applications -> Accessories -> Terminal
```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by HermanAB on 2008-03-07
Note that sooner or later the automatic updates will cause an automatic screw-up and then you'll have no friggen clue what happened or how to fix it.

Since Linux is extremely stable and robust, automatic updates are actually not a particularly hot idea...

---

### Post by maxhoward on 2008-03-07
Thanks Oldsoldier2003.  That did the job.

---

### Post by Papa-san on 2008-03-08
> **HermanAB said:**
> Note that sooner or later the automatic updates will cause an automatic screw-up and then you'll have no friggen clue what happened or how to fix it.

Since Linux is extremely stable and robust, automatic updates are actually not a particularly hot idea...

Now THIS is TRUTH!

My system was working beautifully for a year and a half when a kernel update required a full re-install... I now have my /homen on it's own partition, but I prolly_ should_ turn off the auto-updater...

Anyways, I'm glad you got it resolved, and it's also taught me some new things!

---

