---
title: "Uninstalling in Ubuntu"
date: 2006-08-19
forum: Absolute Beginner Talk
---

### Post by pteri498 on 2006-08-19
I'm just starting with ubuntu, and I'd like to cover my bases, since I'm quite sure I'm going to do something very wrong in Ubuntu that's going to cause undesirable operation.

For example, if I install RealPlayer and soon find out I don't want it, what can I do to uninstall it?

---

### Post by hopstah on 2006-08-19
install everything using the command 'aptitude' instead of 'apt-get'.  this will make uninstalling things more thorough.  but to uninstall something, it's easy. ```
sudo aptitude remove packagename
```

---

### Post by pteri498 on 2006-08-19
> **hopstah said:**
> install everything using the command 'aptitude' instead of 'apt-get'.  this will make uninstalling things more thorough.  but to uninstall something, it's easy.

Ahhh I see. So if using 'aptitude', I would still grab the .deb file and install from command line using that command, rather than using the debian installer interface that Ubuntu provides me?

---

### Post by user1397 on 2006-08-19
> **pteri498 said:**
> Ahhh I see. So if using 'aptitude', I would still grab the .deb file and install from command line using that command, rather than using the debian installer interface that Ubuntu provides me?the command grabs the .deb package for you and installs/removes it for you.  aptitude remembers a package's dependencies better than apt-get, that's why it's recommended.

---

### Post by pteri498 on 2006-08-19
> **erik1397 said:**
> the command grabs the .deb package for you and installs/removes it for you.  aptitude remembers a package's dependencies better than apt-get, that's why it's recommended.

Really? That's quite interesting. Would make my life easier. Just for the record, though, what type of command would I use to install that RealPlayer I was talking about earlier, assuming I hadn't already downloaded the deb file?

---

### Post by user1397 on 2006-08-19
well i wouldn't know the realplayer package name by default, but if you go here: [https://help.ubuntu.com/community/RealplayerInstallationMethods](https://help.ubuntu.com/community/RealplayerInstallationMethods), 
it tells you exactly how to do it.

btw, always search that website (help.ubuntu.com/community) before asking something here.  you'll find that a lot of answers are there already.

---

