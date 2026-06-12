---
title: "apt-get install HELP"
date: 2006-09-29
forum: Absolute Beginner Talk
---

### Post by red van man on 2006-09-29
First time I've connected to broadband and it works a treat, zero setup required.  Except, that is, for apt (or Adept).  It keeps spitting out the following:

Reading package lists... Done
Building dependency tree... Done
gimp is already the newest version.
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  libg2c0: Depends: gcc-3.4-base (= 3.4.6-1ubuntu2) but it is not installable
  libgtk2.0-0: Depends: libgtk2.0-common (>= 2.8.17-1ubuntu5) but it is not installable
               Depends: libgtk2.0-bin (>= 2.8.17-1ubuntu5) but it is not installable
  libpango1.0-0: Depends: libpango1.0-common (>= 1.12.2-0ubuntu3) but it is not installable
  libsdl1.2debian: Depends: libsdl1.2debian-alsa (= 1.2.9-0.0ubuntu2) but it is not installable or
                            libsdl1.2debian-all (= 1.2.9-0.0ubuntu2) but it is not installable or...
   

...you get the idea. (I tried installing libpango, gcc and friends manually but got sick of playing dependency-go-round.)  Adept lists only the packages I already have, or shows packages I don't, like Firefox, greyed out.  Any ideas?  Kubuntu user BTW, but the Kubuntu forum isn't half as active!

---

### Post by aysiu on 2006-09-29
Dependency errors usually stem from conflicting repositories.

1. Get a fresh sources.list
[http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)

2. Try again ```
sudo aptitude update
```

---

### Post by red van man on 2006-09-29
Hmmm, thanks aysiu but that hasn't done it.  Now apt-get install gimp gives me:

```
The following packages have unmet dependencies:
  libg2c0: Depends: gcc-3.4-base (= 3.4.6-1ubuntu2) but it is not going to be installed
  libgtk2.0-0: Depends: libgtk2.0-common (>= 2.8.17-1ubuntu5) but it is not going to be installed
               Depends: libgtk2.0-bin (>= 2.8.17-1ubuntu5) but it is not going to be installed
  libpango1.0-0: Depends: libpango1.0-common (>= 1.12.2-0ubuntu3) but it is not going to be installed
  libsdl1.2debian: Depends: libsdl1.2debian-alsa (= 1.2.9-0.0ubuntu2) but it is not going to be installed or
                            libsdl1.2debian-all (= 1.2.9-0.0ubuntu2) but it is not going to be installed or
                            libsdl1.2debian-esd (= 1.2.9-0.0ubuntu2) but it is not going to be installed or
                            libsdl1.2debian-arts (= 1.2.9-0.0ubuntu2) but it is not going to be installed or
                            libsdl1.2debian-oss (= 1.2.9-0.0ubuntu2) but it is not going to be installed or
                            libsdl1.2debian-nas (= 1.2.9-0.0ubuntu2) but it is not going to be installed
  libwxgtk2.4-1: Depends: libglib1.2 (>= 1.2.0) but it is not going to be installed
                 Depends: libgtk1.2 (>= 1.2.10-4) but it is not going to be installed
  r-recommended: Depends: r-cran-cluster (>= 1.9.6-2) but it is not going to be installed
                 Depends: r-cran-foreign (>= 0.7-2) but it is not going to be installed
```

---

### Post by aysiu on 2006-09-29
Can you post the entire output of these commands? ```
cat /etc/apt/sources.list
sudo aptitude update
sudo aptitude install gimp
```

---

### Post by picpak on 2006-09-29
Where'd the gimp come from?

---

### Post by morphodone on 2006-09-29
> **picpak said:**
> Where'd the gimp come from?

I think the problem is we don't know what you are trying to install.

What command are you running to get that error?

apt-get upgrade?
apt-get install packagename?
apt-get dist-upgarde?

---

### Post by Linux Lover on 2006-09-29
You please look for the solution posts above and stick to `aptitude' instead of `apt-get'. Somewhere in ununtu help section I have read that `aptitude' handles dependency well than `apt-get'.

---

### Post by morphodone on 2006-09-29
> **Linux Lover said:**
> You please look for the solution posts above and stick to `aptitude' instead of `apt-get'. Somewhere in ununtu help section I have read that `aptitude' handles dependency well than `apt-get'.

Well I don't use aptitude so I can't very well comment on it...

---

### Post by aysiu on 2006-09-29
*aptitude* doesn't always handle dependencies "better" than *apt-get*. It really varies based on the situation (sometimes *aptitude* will hold back some packages for no apparent reason).

In this situation, though, I think *aptitude* is worth a shot.

---

