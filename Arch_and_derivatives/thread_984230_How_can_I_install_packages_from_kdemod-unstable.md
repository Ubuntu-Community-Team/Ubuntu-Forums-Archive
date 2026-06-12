---
title: "How can I install packages from kdemod-unstable?"
date: 2008-11-16
forum: Arch and derivatives
---

### Post by benerivo on 2008-11-16
I have the repository enabled, but pacman -Syu doesn't upgrade my kde4.1.3 packages to the kde4.1.7 versions. I can mark them for upgrade individually using Shaman, but there's lots and i don't want to break the system that way.

Is this similar to debian experimental where you have to specify that you want to include upgrades from that repository with```
apt-get -t experimental install foobar
```

EDIT - I really meant 'upgrade' rather than 'install' in the title.

---

### Post by fwojciec on 2008-11-16
> **benerivo said:**
> I have the repository enabled, but pacman -Syu doesn't upgrade my kde4.1.3 packages to the kde4.1.7 versions. I can mark them for upgrade individually using Shaman, but there's lots and i don't want to break the system that way.

Is this similar to debian experimental where you have to specify that you want to include upgrades from that repository with```
apt-get -t experimental install foobar
```

EDIT - I really meant 'upgrade' rather than 'install' in the title.

Pacman prefers repos according to the order they are listed in pacman.conf.  So if you have the kdemod-unstable repo at the bottom of the list pacman will only install packages from it if the same packages don't exist in the repos that are earlier on the list.  It is possible to install individual packages from a specific repo using:
```
pacman -S repo_name/package_name
```
But in your case this might be impractical, since you're dealing with a lot of packages.  What you could do, however, is to temporarily change the order of repositories in pacman.conf and install what you need that way.  You can restore the original order afterwards.

---

### Post by mips on 2008-11-16
As far as I know it is not as simple as upgrading, there was one major change which means it will not work.

See my instructions here, [http://ubuntuforums.org/showpost.php?p=6190797&postcount=130](http://ubuntuforums.org/showpost.php?p=6190797&postcount=130)

WARNING: You are installing Alpha software which can have bugs & has no support!

---

### Post by benerivo on 2008-11-16
Thanks guys. That worked from the point of view that it tried to do what i asked, but i had a couple of error messages. From memory, one was about a file existing in two separate places, and the other was about a corrupt qt4 download. I checked that i had disabled the kdemod-core repository, did pacman -Q | grep kde (and qt), and also ran pacman -Scc and tried to download the qt4 package again, but still got both error messages again. I'm happily going to go back to 4.1.3 on a fresh install, and just wait.

---

