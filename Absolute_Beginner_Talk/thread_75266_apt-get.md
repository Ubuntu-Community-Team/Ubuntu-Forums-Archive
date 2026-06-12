---
title: "apt-get"
date: 2005-10-13
forum: Absolute Beginner Talk
---

### Post by ~J~ on 2005-10-13
Are there any good tutorials aimed for the totally beginner on how to use the apt-get command?

As a simple task, I want to install PyGame, and I've learned so far that if I see a DEB package, then I can use the apt-get command to installed it.

But what I don't yet understand is what I use after the apt-get.  For example, PyGame is on version 1.7.1; I've tried...

apt-get pygame1.7.1
apt-get pygame171
apt-get pygame-1.7.1.deb

etc, etc, etc.

Is there some kind of standardised system for downloading the packages, for example 'packagename'-'version'.deb, maybe a list somewhere of all the packages available or do you need to visit each site and find out what the package name is called?

---

### Post by Freddie.Ruddick on 2005-10-13
You don't have to use apt-get. System | Administration | Synaptic Package Manager OR Applications | Add Applications (Breezy only). Both of these have a search function. I think, although Ubuntu is Debian-based, Debian and Ubuntu packages are not interchangable.

---

### Post by ~J~ on 2005-10-13
Thanks for the reply Freddie, didn't realise that the DEB packages were not 100% Ubuntu.

I'll certainly have a look at the add/remove programs you mentioned though.

---

### Post by DJ_Max on 2005-10-13
If there isn't a package called pygame1.7.1 in the repo, you can't install it. The package is called python-pygame, and it will install the latest version in the repository.

You also don't denote .deb in APT.

---

