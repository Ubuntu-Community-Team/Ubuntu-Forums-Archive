---
title: "Synaptic Package Manager Error"
date: 2007-08-14
forum: Apple Intel Users
---

### Post by churchill614 on 2007-08-14
Please help.

I tried to install Amarok in Gnome and my MacBook, not realising it was built for KDE.  It would not install properly, and no, when I try to use Synaptic Package Manager, I get the following error:

E: Type ‘Usage:’ is not known on line 40 in source list /etc/apt/sources.list
E: The list of sources could not be read.
Go to the repository dialogue to correct the problem.
E: _cache->open() failed, please report.


Help would very much be appreciated.


Thanks, from a confused newbie.

---

### Post by kostkon on 2007-08-14
First of all, you can use KDE applications in Gnome and the opposite. They are all Linux applications, after all.

Now, about your problem. Have you, at any time, used Automatix?

Anyway, could you open a terminal, type this
```
gedit /etc/apt/sources.list
```

and paste the contents of your sources list here, in order to see what the problem is.

---

### Post by churchill614 on 2007-08-14
Thanks, I found the answer, and have sorted the problem - deleted sources.list, pasted in a new version and ran update.

However, how do I install amarok without it screwing up my system again?

---

### Post by cyberdork33 on 2007-08-14
> **churchill614 said:**
> Thanks, I found the answer, and have sorted the problem - deleted sources.list, pasted in a new version and ran update.

However, how do I install amarok without it screwing up my system again?

You shouldn't have to do anything special. It will install all the KDE dependencies by itself. I don't know what happened the last time you tried.

---

