---
title: "Why are there different versions of Ubuntu anyways?"
date: 2006-04-12
forum: Absolute Beginner Talk
---

### Post by theycallmemorty on 2006-04-12
I'm not sure I understand why there are different versions of Ubuntu.

If I have 5.04 and I upgrade all of my patches shouldn't I now have the same thing installed as someone using version 6.06??

Isn't Ubuntu just a collection of software??

---

### Post by marcos89 on 2006-04-12
Im a total beginner with apt-get  but im answering in gentoo's emerge sort of way..you would have to edit your /etc/sources.list   to point to dapper's repository not breezy's.

---

### Post by aysiu on 2006-04-12
Same reason there's Windows...

3.1
95
98
ME
2000
XP
Vista

---

### Post by mips on 2006-04-12
[QUOTE=theycallmemorty]I'm not sure I understand why there are different versions of Ubuntu.

If I have 5.04 and I upgrade all of my patches shouldn't I now have the same thing installed as someone using version 6.06??

Isn't Ubuntu just a collection of software??[/QUOTE]

1. Product improvements and upgrades.

2. No. In order to get a different version you have to change your sources list to the new version (ie Dapper), do a apt-get update followed by a apt-get dist-upgrade. I myself prefer a fresh install to a upgrade.

3. Yes, you can view it as a collection of software.

---

### Post by KingBahamut on 2006-04-12
[http://doc.gwos.org/index.php/AysEssay](http://doc.gwos.org/index.php/AysEssay)

Compliments of our friend aysiu.

---

### Post by 5-HT on 2006-04-12
For stability purposes, development versions of Ubuntu undergoe a package freeze just prior to release.

After that time, the only updates available are security updates and possibly bug fixes. There are no program updates for upgrading to the newest version of a package. This is why 5.10 will never have all of the same packages as 6.04 (or is it 6.06 now?).

You can, of course, always upgrade to a new release of Ubuntu. 

If you do want the most current versions of a package, you could either:
1) Get them from backports (check out the backports section on these forums for the what/why/how etc..)
2) Compile them yourself*
3) Obtain a binary from the developer*

*Because of the package freeze, you may not be able to install some needed dependencies.

If you insist on a bleeding edge system, Ubuntu may not be the best solution.
It's a great distro, but its philosophy includes a package freeze for each release (which I like).

HTH

---

