---
title: "Quick command line question. (Between Distros)"
date: 2012-09-05
forum: Any Other OS
---

### Post by linuxvstheworld on 2012-09-05
I know there are differences in programs and look of Linux distributions, but aren't all practically the same looking from the command line perspective? :-|

---

### Post by linuxvstheworld on 2012-09-05
I know how different Linux distros are different in appearance and programs it can run, but are they basically the same looking from the command line perspective but just tweaked? :|

---

### Post by Shepherd of Wolves on 2012-09-05
If you're talking about Gnome and KDE the only difference is the name of  the command line (terminal and konsole). But between Ubuntu and, let's say Fedora,  there's a few differences. For example, "apt-get" on Ubuntu would be "yum" on fedora.

---

### Post by Shepherd of Wolves on 2012-09-05
Yeah, I suppose they're just tweaked. But it's still a whole new set of commands to get used to...

---

### Post by linuxvstheworld on 2012-09-05
I was wondering if they were COMPLETELY different, but I guess not, some could be tweaked to an exclusive feature like if Mint has an exclusive feature it'll be on there. Thanks for the help!

---

### Post by spjackson on 2012-09-05
For most purposes there are very few differences. bash, ls, gzip, tar etc. are the same no matter what the distro. There may be distros where bash is not the default shell, but it will still be installable.

The activities for which the differences are greatest are those which involve installing software and other system administration tasks.

---

### Post by qyot27 on 2012-09-05
Also, I suppose it's not as much of a concern in Linux distros, but sometimes the particular branch of a utility or program can differ between members of the greater Unix family.  Linux distros usually rely on the GNU userland, whereas you could have functional differences in the same utilities in their BSD versions (sed for one, but there are others I'm sure).

Software versioning of other programs is usually just a matter of what comes stock in the repositories (if they exist) and what the distro's stance on stable/beta/bleeding edge software is.  Sometimes it gets more into politics inside of the software projects themselves and the distros picking sides, such as with the schism between FFmpeg and the libav fork.  In most of these cases, the user can usually find a PPA with the version they want, or can compile it themselves to get it.



But in essence, a distro that aims to be POSIX-compliant (or LSB-compliant on top of that) will have a shared set of utilities and functions with all the others that are compliant.  If a user knows how to use one, they'll know how to use the others with only a relatively minimal amount of difference in their actual use - setting the system up or package management could be wildly different though, as mentioned above.

---

