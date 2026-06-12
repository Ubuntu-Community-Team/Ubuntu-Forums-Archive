---
title: "KDE in ubuntu"
date: 2006-01-08
forum: Absolute Beginner Talk
---

### Post by wolfmaniac on 2006-01-08
can we install kde in UBUNTU???????????

---

### Post by Alpha_toxic on 2006-01-08
Yes, just install [COLOR="Red"]kubuntu-desktop[/COLOR] package
```

sudo apt-get kubuntu-desktop

```
You might have to enable the [universe/multiverse repositories]("http://help.ubuntu.com/starterguide/C/faqguide-all.html").
After the installtaion, at login you'll have the option to choose your session (Gnome, KDE, and whatever else you have installed).
Before installation you might add these lines
```

# kubuntu.org packages for KDE 3.5 (packages, GPG key: DD4D5088)
deb http://kubuntu.org/packages/kde35 breezy main

# kubuntu.org packages for KDE 3.5 (sources, GPG key: DD4D5088)
deb-src http://kubuntu.org/packages/kde35 breezy main

```
to you repository list in [COLOR="Red"]/etc/apt/sources.list[/COLOR]
Actually I'm not sure if these lines are not there by default, so better check that first.
Good luck. :)

---

### Post by Alpha_toxic on 2006-01-08
Yes, just install [COLOR="Red"]kubuntu-desktop[/COLOR] package
```

sudo apt-get kubuntu-desktop

```
You might have to enable the [universe/multiverse repositories]("http://help.ubuntu.com/starterguide/C/faqguide-all.html").
After the installtaion, at login you'll have the option to choose your session (Gnome, KDE, and whatever else you have installed).
Before installation you might add these lines
```

# KDE 3.5
deb http://kubuntu.org/packages/kde35 breezy main
deb-src http://kubuntu.org/packages/kde35 breezy main

```
to you repository list in [COLOR="Red"]/etc/apt/sources.list[/COLOR]
Actually I'm not sure if these lines are not there by default, so better check that first.
Good luck. :)

oooooooooops, sorry for the double posting, sth got buggy :(

---

### Post by Norberg on 2006-01-08
Yes you can with sudo apt-get install kde or if you want Kubuntu apt-get install kubuntu-desktop

---

### Post by Thirsteh on 2006-01-08
sudo apt-get install kubuntu-desktop, simply.

---

### Post by tassoman on 2006-01-09
[QUOTE=Alpha_toxic]Yes, just install [COLOR="Red"]kubuntu-desktop[/COLOR] package
```

sudo apt-get kubuntu-desktop

```
You might have to enable the [universe/multiverse repositories]("http://help.ubuntu.com/starterguide/C/faqguide-all.html").
After the installtaion, at login you'll have the option to choose your session (Gnome, KDE, and whatever else you have installed).
Before installation you might add these lines
```

# kubuntu.org packages for KDE 3.5 (packages, GPG key: DD4D5088)
deb http://kubuntu.org/packages/kde35 breezy main

# kubuntu.org packages for KDE 3.5 (sources, GPG key: DD4D5088)
deb-src http://kubuntu.org/packages/kde35 breezy main

```
to you repository list in [COLOR="Red"]/etc/apt/sources.list[/COLOR]
Actually I'm not sure if these lines are not there by default, so better check that first.
Good luck. :)[/QUOTE]
How to get its gpg key?

---

### Post by xMetaRidley on 2006-01-09
[QUOTE=tassoman]How to get its gpg key?[/QUOTE]
```

 wget http://people.ubuntu.com/~jriddell/kubuntu-packages-jriddell-key.gpg
 sudo apt-key add kubuntu-packages-jriddell-key.gpg

```

---

