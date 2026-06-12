---
title: "Can Wine harm my system"
date: 2008-03-19
forum: Absolute Beginner Talk
---

### Post by sayakb on 2008-03-19
Certain viruses/trojans infect Windows executables. If I execute such WIN32 applications thru Wine, will it harm my system anyhow?

---

### Post by jordanmthomas on 2008-03-19
It certainly can, since wine typically has access to your filesystem (ie, you can save things in your home directory when running programs in wine)

Any file your user has write access to can be affected by a virus run in wine.

---

### Post by misfitpierce on 2008-03-19
I dont think it will necessarily harm your system to the extent of running full on windows but it is possible it could mess up everything in your wine folder... and just maybe mess up something in Ubuntu but i've yet to hear of this.

---

### Post by Tomatz on 2008-03-19
In theory yes. 

Probably no. 

At worst it would probably only be able to infect your wine drive :)

---

### Post by Trail on 2008-03-19
There was a blog somewhere that documented a guy attempting to run windows virii through wine. Neither of those could successfully run completely.

However, it seems possible that a windows virus could infect your system, most likely your .wine folder. This is, provided the virus can slip through ubuntu's layer as well (quite harder to exploit stuff,eh?). I personally think it's a unlikely at the moment.

To be more safe, you can remove the root folder from winecfg so that whatever happens in wine cannot effect anything in your filesystem except where you specifically give access to.

---

### Post by RJ Hythloday on 2008-03-19
good question, I've wondered this also, if os can end up corrupted like it does in m$.

---

### Post by sayakb on 2008-03-19
So that asks for the installation of an antivirus.. Thats really bad.

---

### Post by zvacet on 2008-03-19
Read [this.](http://ubuntuforums.org/showthread.php?t=510812)

---

