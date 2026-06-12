---
title: "Command for upgrading"
date: 2006-12-19
forum: Absolute Beginner Talk
---

### Post by vivin_west on 2006-12-19
How to upgrade the Ubuntu to fix bugs?

---

### Post by PartisanEntity on 2006-12-19
To update but remain in your release: sudo apt-get update

To upgrade to the latest release: sudo apt-get upgrade

---

### Post by Bachstelze on 2006-12-19
> **PartisanEntity said:**
> To update but remain in your release: sudo apt-get update

To upgrade to the latest release: sudo apt-get upgrade

Wrong ! sudo apt-get update won't upgrade anything but just downloas the package list. sudo apt-get upgrade will upgrade all upgradable packages but stay in "the release", unless sources.list was modified to use a new release.

---

### Post by vivin_west on 2006-12-19
Will I lose any existing files or programs if I upgrade?

---

### Post by Bachstelze on 2006-12-19
No. Updated packages will be replaced with new versions but that's all.

---

### Post by LookTJ on 2006-12-19
Have you tried:

```
sudo aptitude update
```

or 

```
sudo aptitude upgrade
```

---

### Post by LookTJ on 2006-12-19
> **PartisanEntity said:**
> To update but remain in your release: sudo apt-get update

To upgrade to the latest release: sudo apt-get upgrade
actually to upgrade to latest release is

```
sudo apt-get dist-upgrade
```

---

### Post by vivin_west on 2006-12-19
Wait I am confused what is the difference between all these?

---

### Post by LookTJ on 2006-12-19
> **vivin_west said:**
> Wait I am confused what is the difference between all these?

The difference between apt-get and aptitude

aptitude: aptitude is another terminal-based front-end to APT, like apt-get. However, aptitude can remember the dependencies installed with a package and remove them if you uninstall

apt-get: APT is the Advanced Package Tool, which together with dpkg forms the basic Ubuntu package management toolkit

---

### Post by Bachstelze on 2006-12-19
> **Taylor said:**
> actually to upgrade to latest release is

```
sudo apt-get dist-upgrade
```

Wrong again, though it is used for upgrading between releases, it can also be used in some other cases.

**vivin_west**, *apt-get update* will download the list of all installable packages in the repos you have in your sources.list. Let's say you have package A installed and there is a newer version of it available in the lists you downloaded with *apt-get update*, running *apt-get upgrade* will install it - *apt-get dist-upgrade* will do the same but it deals differently with "broken" packages. Let's say you have package B and package C and let's say there's a newer version of B available, but which conflicts with C. Since upgrading B would mean removing C, *apt-get upgrade* won't do it and instead tell you B could not been upgraded. If you want to upgrade B, you'll need to run *apt-get dist-upgrade*, which will also remove C.

---

### Post by vivin_west on 2006-12-19
Aptitude appears to be better than apt-get.Is it true?

---

### Post by Bachstelze on 2006-12-19
Aptitude is better in one way, when you install big metapackages and want to remove them later. An example, let's say you want to install *kde*. Of course, not the whole KDE environment is included in one package. Instead, it will install all KDE components, each in its own package. For installing, whether you use apt-get or aptitude doesn't matter. The difference come when - if - you want to remove it. Since *kde* is only a metapackage - contains nothing in itself but instead installs other packages -, removing it alone is like removing nothing, you'll have to remove all the packages it installed one by one. This iswhere aptitude is useful, since it will remember which package it installed, and will remove all of them as well when removing the metapackage.

---

### Post by vivin_west on 2006-12-19
Ok, now I am unable to play Totem-Xine because of a bug which when I reported a forum staffer told me is most probably fixed by now.So how do I proceed. How do I upgrade the OS to fix this bug.

---

### Post by Bachstelze on 2006-12-19
```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by PartisanEntity on 2006-12-19
> **HymnToLife said:**
> Wrong ! sudo apt-get update won't upgrade anything but just downloas the package list. sudo apt-get upgrade will upgrade all upgradable packages but stay in "the release", unless sources.list was modified to use a new release.

Sorry, I stand corrected.

---

