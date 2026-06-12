---
title: "Does Linux Mint use ubuntu repositories?"
date: 2012-09-18
forum: Any Other OS
---

### Post by linuxvstheworld on 2012-09-18
Let's say in Ubuntu, I wanted to get gnome-tweak. I'd obviously do
```
sudo apt-get install gnome-tweak
``` and BAM! Installed....
What if I was on Mint? Mint is based off of Ubuntu so wouldn't that mean I'd do sudo apt-get as well? Or does Mint do their own thing when it comes to packages?

---

### Post by vasa1 on 2012-09-18
Here is the place to get first-hand information on Mint: [http://forums.linuxmint.com/](http://forums.linuxmint.com/) because
> this is not the best place to receive tech support for these OS's/Distro's and users should look for official support channels for those systems.

---

### Post by linuxvstheworld on 2012-09-18
Yeah I don't use Mint but I was just wondering between the possible similarities between the two... just a curious question.

---

### Post by kurok on 2012-09-18
Yes mint uses the ububtu repoes as well as some of their own and the sudo commands work as you would expect on an ububtu based distro.

---

### Post by linuxvstheworld on 2012-09-18
> **kurok said:**
> Yes mint uses the ububtu repoes as well as some of their own and the sudo commands work as you would expect on an ububtu based distro.

That's great! Thanks so much!

---

### Post by MG&amp;TL on 2012-09-18
> **linuxvstheworld said:**
> Yeah I don't use Mint but I was just wondering between the possible similarities between the two... just a curious question.

Yup.

Mint -> Ubuntu -> Debian

All of these use APT (and dpkg) as a package manager. Whether they use each other's repositories...

1. Debian packages most stuff from upstream, and sticks it on their package servers, updating almost continuously.

2. Ubuntu 'syncs' Debian packages from the Debian servers, roughly once every six months. Ubuntu also adds its own patches (e.g. Unity integration) and some packages that Debian declares unsuitable for its repositories.

3. Mint grabs Ubuntu's packages and syncs/patches some of them. Others, however, it simply relies upon Ubuntu's servers for packages.


If you're interested, take a look at "Software Sources" sometime: press Alt+F2, type "software-properties-gtk" and press return.

---

### Post by wheeze on 2012-09-18
There are two strains of Mint, the main editions based on Ubuntu, and one edition based directly on Debian, called LMDE (Linux Mint Debian Edition).

Don't try any Ubuntu stuff on LMDE. It does not use the Ubuntu repos, and PPAs should not be used.

---

### Post by linuxvstheworld on 2012-09-18
> **wheeze said:**
> There are two strains of Mint, the main editions based on Ubuntu, and one edition based directly on Debian, called LMDE (Linux Mint Debian Edition).

Don't try any Ubuntu stuff on LMDE. It does not use the Ubuntu repos, and PPAs should not be used.

What are the advantages to the Debian edition of Mint?

---

### Post by black veils on 2012-09-19
> **linuxvstheworld said:**
> What are the advantages to the Debian edition of Mint?

possibly speed and stability for regular debian alone. but for LMDE i cant remember, i think they use the unstable debian for it.

---

