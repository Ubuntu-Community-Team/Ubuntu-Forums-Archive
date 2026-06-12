---
title: "Website Programs"
date: 2006-08-05
forum: Absolute Beginner Talk
---

### Post by NeoGreen on 2006-08-05
What program can I use for Linux to create web pages?  You know, microsoft has Front Page and Dreamweaver, but what does Linux have?

---

### Post by spin2cool on 2006-08-05
You're probably looking for Nvu.  

sudo apt-get install nvu

---

### Post by user1397 on 2006-08-05
yep nvu is the one.  

i'd type in the terminal: ```
sudo aptitude update && sudo aptitude install nvu
```to install it, but thats just me...(i like aptitude!)

nvu is actually cross-platform: meaning it works on windows, mac, and linux, just so you know.

---

### Post by abowman on 2006-08-05
[Quanta Plus]("http://quanta.kdewebdev.org/") looks good.

```
sudo apt-get install quanta
```

---

### Post by NeoGreen on 2006-09-16
Nvu is awesome, and to think I was about to spend 300.00 on a copy of Dreamweaver, thanks.:D

---

### Post by geovino on 2006-10-07
> **abowman said:**
> [Quanta Plus]("http://quanta.kdewebdev.org/") looks good.

```
sudo apt-get install quanta
```

Thanks, I wish others apps were this easy to install.

---

### Post by Sef on 2006-10-07
> Thanks, I wish others apps were this easy to install.

If you have enabled Universe and Multiverse, then the apps in those repositories are just as easy to install.  (The other repositories are on by default and install just as easy.)

---

### Post by geovino on 2006-10-07
> **Sef said:**
> If you have enabled Universe and Multiverse, then the apps in those repositories are just as easy to install.  (The other repositories are on by default and install just as easy.)

How do I set that up?

---

### Post by Marsolin on 2006-10-08
Open [Synaptic]("http://linuxappfinder.com/package/synaptic") and select Repositories from the Settings menu. You will see a list of repositories, some of which are grayed out. Look for any that start with deb (deb-src is for source files only) and mention either universe or multiverse in the Sections column. Check those entries, hit Ok, Reload and you'll have access to all of the extra software.

---

