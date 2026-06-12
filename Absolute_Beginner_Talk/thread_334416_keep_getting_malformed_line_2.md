---
title: "keep getting malformed line 2"
date: 2007-01-08
forum: Absolute Beginner Talk
---

### Post by Mirena on 2007-01-08
I am new to Ubuntu I love the OS and all and was happy until I tried to install something, after that i will not update .
this is my   source list. I also tried with the one in ubuntu wiki guide.
I keep getting this 
E: Malformed line 2 in source list /etc/apt/sources.list.d/edgy-multiverse.list (URI parse)
E: Unable to lock the list directory
Please help]:confused: 

# [http://www.ubuntu-nl.org/source-o-matic/](http://www.ubuntu-nl.org/source-o-matic/)
#
# If you get GPG errors with this sources.list, locate the GPG key in this file
# and run these commands (where KEY is replaced with that key)
#
# gpg --keyserver hkp://subkeys.pgp.net --recv-keys KEY
# gpg --export --armor KEY | sudo apt-key add -

# Ubuntu supported packages
# GPG key: 437D05B5
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy restricted main multiverse universe #Added by software-properties
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-updates restricted main multiverse universe #Added by software-properties
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security restricted main multiverse universe #Added by software-properties


# Ubuntu community supported packages
# GPG key: 437D05B5
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy universe multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-updates universe multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe multiverse


# Seveas' Ubuntu Packages
# GPG key: 1135D466
deb [http://mirror.ubuntulinux.nl/](http://mirror.ubuntulinux.nl/) edgy-seveas all

deb-src [http://seveas.imbrandon.com](http://seveas.imbrandon.com) edgy-seveas all

# Ubuntu backports project
# GPG key: 437D05B5
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse #Added by software-properties


# Kubuntu.org bleeding edge KDE
# GPG key: DD4D5088
deb [http://kubuntu.org/packages/kde-latest](http://kubuntu.org/packages/kde-latest) edgy main

deb-src [http://kubuntu.org/packages/kde-latest](http://kubuntu.org/packages/kde-latest) edgy main

# Kubuntu.org bleeding edge Koffice
# GPG key: DD4D5088
deb [http://kubuntu.org/packages/koffice-latest](http://kubuntu.org/packages/koffice-latest) edgy main

deb-src [http://kubuntu.org/packages/koffice-latest](http://kubuntu.org/packages/koffice-latest) edgy main

# Kubuntu.org bleeding edge amaroK
# GPG key: DD4D5088
deb [http://kubuntu.org/packages/amarok-latest](http://kubuntu.org/packages/amarok-latest) edgy main

deb-src [http://kubuntu.org/packages/amarok-latest](http://kubuntu.org/packages/amarok-latest) edgy main

# Upstream Wine
deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) edgy main

deb-src [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) edgy main

# bzr nightly snapshots
deb [http://people.ubuntu.com/~jbailey/snapshot/bzr](http://people.ubuntu.com/~jbailey/snapshot/bzr) ./

deb-src [http://people.ubuntu.com/~jbailey/snapshot/bzr](http://people.ubuntu.com/~jbailey/snapshot/bzr) ./

# Upstream Beryl
# GPG key: ed8a569e
deb [http://www.beerorkid.com/compiz](http://www.beerorkid.com/compiz) edgy main-edgy

deb-src [http://www.beerorkid.com/compiz](http://www.beerorkid.com/compiz) edgy main-edgy

# Medibuntu multimedia packages
# GPG key: 0C5A2783
deb [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) edgy free non-free

deb-src [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) edgy free non-free

# Canonical Commercial packages
# GPG key: 437D05B5
deb [http://archive.canonical.com](http://archive.canonical.com) edgy-commercial main

deb-src [http://archive.canonical.com](http://archive.canonical.com) edgy-commercial main


deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-proposed restricted main multiverse universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-proposed restricted main multiverse universe #Added by software-properties

---

### Post by taurus on 2007-01-08
Is that your /etc/apt/sources.list **or** /etc/apt/sources.list.d/edgy-multiverse.list?  If it is your /etc/apt/sources.list, then can you list /etc/apt/sources.list.d/edgy-multiverse.list here too?

```
cat /etc/apt/sources.list.d/edgy-multiverse.list
```

---

### Post by Mirena on 2007-01-08
Thanks for taking my case

the one I posted is the /etc/apt/sources.list

This one appears with the code you gave me  which I guess is for the other one

logar@Tiamat:~$ cat /etc/apt/sources.list.d/edgy-multiverse.list
# automatically added by gnome-app-install on 2006-12-19 03:56:16.434353
deb None edgy multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security
deb None edgy-updates multiverse

---

### Post by Mirena on 2007-01-08
> **Mirena said:**
> I am new to Ubuntu I love the OS and all and was happy until I tried to install something, after that i will not update .
this is my   source list. I also tried with the one in ubuntu wiki guide.
I keep getting this 
E: Malformed line 2 in source list /etc/apt/sources.list.d/edgy-multiverse.list (URI parse)
E: Unable to lock the list directory
Please help]:confused: 
/etc/apt/sources.list

# [http://www.ubuntu-nl.org/source-o-matic/](http://www.ubuntu-nl.org/source-o-matic/)
#
# If you get GPG errors with this sources.list, locate the GPG key in this file
# and run these commands (where KEY is replaced with that key)
#
# gpg --keyserver hkp://subkeys.pgp.net --recv-keys KEY
# gpg --export --armor KEY | sudo apt-key add -

# Ubuntu supported packages
# GPG key: 437D05B5
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy restricted main multiverse universe #Added by software-properties
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-updates restricted main multiverse universe #Added by software-properties
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security restricted main multiverse universe #Added by software-properties


# Ubuntu community supported packages
# GPG key: 437D05B5
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy universe multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-updates universe multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe multiverse


# Seveas' Ubuntu Packages
# GPG key: 1135D466
deb [http://mirror.ubuntulinux.nl/](http://mirror.ubuntulinux.nl/) edgy-seveas all

deb-src [http://seveas.imbrandon.com](http://seveas.imbrandon.com) edgy-seveas all

# Ubuntu backports project
# GPG key: 437D05B5
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse #Added by software-properties


# Kubuntu.org bleeding edge KDE
# GPG key: DD4D5088
deb [http://kubuntu.org/packages/kde-latest](http://kubuntu.org/packages/kde-latest) edgy main

deb-src [http://kubuntu.org/packages/kde-latest](http://kubuntu.org/packages/kde-latest) edgy main

# Kubuntu.org bleeding edge Koffice
# GPG key: DD4D5088
deb [http://kubuntu.org/packages/koffice-latest](http://kubuntu.org/packages/koffice-latest) edgy main

deb-src [http://kubuntu.org/packages/koffice-latest](http://kubuntu.org/packages/koffice-latest) edgy main

# Kubuntu.org bleeding edge amaroK
# GPG key: DD4D5088
deb [http://kubuntu.org/packages/amarok-latest](http://kubuntu.org/packages/amarok-latest) edgy main

deb-src [http://kubuntu.org/packages/amarok-latest](http://kubuntu.org/packages/amarok-latest) edgy main

# Upstream Wine
deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) edgy main

deb-src [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) edgy main

# bzr nightly snapshots
deb [http://people.ubuntu.com/~jbailey/snapshot/bzr](http://people.ubuntu.com/~jbailey/snapshot/bzr) ./

deb-src [http://people.ubuntu.com/~jbailey/snapshot/bzr](http://people.ubuntu.com/~jbailey/snapshot/bzr) ./

# Upstream Beryl
# GPG key: ed8a569e
deb [http://www.beerorkid.com/compiz](http://www.beerorkid.com/compiz) edgy main-edgy

deb-src [http://www.beerorkid.com/compiz](http://www.beerorkid.com/compiz) edgy main-edgy

# Medibuntu multimedia packages
# GPG key: 0C5A2783
deb [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) edgy free non-free

deb-src [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) edgy free non-free

# Canonical Commercial packages
# GPG key: 437D05B5
deb [http://archive.canonical.com](http://archive.canonical.com) edgy-commercial main

deb-src [http://archive.canonical.com](http://archive.canonical.com) edgy-commercial main


deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-proposed restricted main multiverse universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-proposed restricted main multiverse universe #Added by software-properties

logar@Tiamat:~$ cat /etc/apt/sources.list.d/edgy-multiverse.list
# automatically added by gnome-app-install on 2006-12-19 03:56:16.434353
deb None edgy multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security
deb None edgy-updates multiverse

---

### Post by Mirena on 2007-01-10
I solved it helped by Taurus, so I am posting it if someone has a similar problem
this is what I did I remove the source.list.d, I still do not know how it was created but it worked

Terminal 

sudo rm /etc/apt/sources.list.d/*
(hit y for each question...)
sudo aptitude update
sudo aptitude upgrade

---

