---
title: "apt-get upgrade"
date: 2006-04-15
forum: Absolute Beginner Talk
---

### Post by podollb on 2006-04-15
After running apt-get update, I then try to run the apt-get upgrade and I get this:

Reading package lists... Done
Building dependency tree... Done
The following packages have been kept back:
  linux-image-386 linux-restricted-modules-386 update-manager
0 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.

Why are the 3 things not upgraded? And how do you go about doing that?

---

### Post by sYs^ on 2006-04-15
Try: ```
sudo apt-get dist-upgrade
```

---

### Post by aysiu on 2006-04-15
The kept back packages usually happen when you have conflicting repositories.

Try a fresh repositories list:
[http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)

---

### Post by podollb on 2006-04-15
So what are the consecuences for doing that dist-upgrade? Will it possibly break the system?

---

### Post by aysiu on 2006-04-15
[QUOTE=podollb]So what are the consecuences for doing that dist-upgrade? Will it possibly break the system?[/QUOTE] From what I've been told, the difference between ```
sudo apt-get upgrade
``` and ```
sudo apt-get dist-upgrade
``` is that *upgrade* will simply make sure all the programs you have installed are the latest version that's available, and *dist-upgrade* will actually remove programs and replace them with "better" ones, depending on how the developers have decide to work things out.

So, yes, it's possible that *dist-upgrade* could break your system.

Generally, though, when you're doing *apt-get* stuff, you'll be warned if something is going to be removed, held back, installed, etc. You can force a particular package to be installed, but that forcing may be more likely to break your system than the *dist-upgrade*.

---

### Post by Sef on 2006-04-15
> So what are the consecuences for doing that dist-upgrade? Will it possibly break the system?

Yes, it is possible you could break the system.   If you did dist-upgrade, you will be upgrading to Dapper, which is still in alpha testing.  If you have older hardware like me, it is more likely to work, but you could still experience problems.   I would not do a dist-upgrade, if you are fairly new to Linux/GNU.   The tweaks often involve the command line and changing things that can mess up your system if done wrong.

---

### Post by aysiu on 2006-04-15
[QUOTE=Sef]Yes, it is possible you could break the system.   If you did dist-upgrade, you will be upgrading to Dapper, which is still in alpha testing.[/QUOTE] That's only if you change your sources.list to point to Dapper repositories. As long as you're still using Breezy repositories, *dist-upgrade* won't upgrade you to Dapper.

---

