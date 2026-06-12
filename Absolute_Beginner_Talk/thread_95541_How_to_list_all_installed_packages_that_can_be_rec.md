---
title: "How to list all installed packages that can be reconfigured with dpkg-reconfigure?"
date: 2005-11-26
forum: Absolute Beginner Talk
---

### Post by Akhran on 2005-11-26
Any commandline option that can be used with dpkg, aptitude or such to display the list of packages that can be reconfigured with dpkg-reconfigure?

Thanks :)

---

### Post by cwaldbieser on 2005-11-26
[QUOTE=Akhran]Any commandline option that can be used with dpkg, aptitude or such to display the list of packages that can be reconfigured with dpkg-reconfigure?

Thanks :)[/QUOTE]
Well, assuming that any installed package can be reconfigured, you could do "dpkg -l *".  The status flags on the left would have an "i" status for installed packages.  Maybe that could be piped through grep or sed or awk to filter down the list a little.

---

### Post by Deus42 on 2006-11-13
I doesn't look like dpkg-reconfigure can take input from a pipe, but if you run dpkg-reconfigure -a

that will reconfigure all packages. When I did this, I also added a -p high so that I would be asked a ton of questions.

---

