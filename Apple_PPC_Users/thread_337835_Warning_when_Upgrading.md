---
title: "Warning when Upgrading"
date: 2007-01-13
forum: Apple PPC Users
---

### Post by bmbeeman on 2007-01-13
I wanted to upgrade my Dapper installation to Edgy and I went to the [Ubuntu Guide Upgrading Section]("http://ubuntuguide.org/wiki/Ubuntu_Edgy#Upgrading_Ubuntu") and followed the official upgrading process and I get a warning when I put the final command into the console:

```
bmbeeman@bmbeeman-desktop:~$ gksudo "update-manager -c -d"
/usr/lib/python2.4/site-packages/apt/__init__.py:17: FutureWarning: apt API notstable yet

```

Will this cause a problem if I upgrade?  If so, what exactly is the warning asking me to fix?

Thanks.

---

### Post by ssam on 2007-01-14
you dont need to worry about it.

it is basically warning the developers of update-manager that the may need to make changes to their code in the future if the libraries they use get updated.

in python if a feature is being removed in for example version 2.5, then version 2.4 will give FutureWarnings when you use it.

---

### Post by bmbeeman on 2007-01-14
Thanks for the information, it's really put my mind at ease about upgrading.

---

