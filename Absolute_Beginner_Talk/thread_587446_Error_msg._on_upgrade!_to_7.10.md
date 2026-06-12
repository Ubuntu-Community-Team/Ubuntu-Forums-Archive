---
title: "Error msg. on upgrade! to 7.10"
date: 2007-10-22
forum: Absolute Beginner Talk
---

### Post by rosswmcgee on 2007-10-22
Failed to fetch [http://archive.canonical.com/ubuntu/dists/feisty-commercial/main/binary-i386/Packages.bz2](http://archive.canonical.com/ubuntu/dists/feisty-commercial/main/binary-i386/Packages.bz2) Sub-process bzip2 returned an error code (2)
Failed to fetch [http://archive.canonical.com/ubuntu/dists/feisty-commercial/main/binary-i386/Packages.bz2](http://archive.canonical.com/ubuntu/dists/feisty-commercial/main/binary-i386/Packages.bz2) Sub-process bzip2 returned an error code (2)
What do I do?

---

### Post by Beggar on 2007-10-22
Did the upgrade complete? Try and run it again.

---

### Post by rosswmcgee on 2007-10-22
I have tried it three times and get the same error message,

---

### Post by Sef on 2007-10-22
Could you paste your sources list here?  Applications > Accessories > Terminal

```
cat /etc/apt/sources.list
```

---

### Post by rosswmcgee on 2007-10-22
deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) feisty main

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) feisty-commercial main

# deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) edgy main

# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) edgy-commercial main

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse #Added by software-properties

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-updates universe multiverse

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-security main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-security main restricted universe multiverse #Added by software-properties

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty universe multiverse
#AUTOMATIX REPOS END

---

### Post by Beggar on 2007-10-23
After you run automatix you can't reasonably expect your computer to upgrade....

Your best bet is going to be a new install, this time dont use automatix, [lesson learned]("http://mjg59.livejournal.com/77440.html")...

---

### Post by rosswmcgee on 2007-10-23
I up graded to Fiesty by xing out some line successfully, I know I have a clean install on another computer, but would like to up grade this one, and I know there is a way, but have been unable to remember how to do it.

---

### Post by rosswmcgee on 2007-10-23
I have succesfully upgraded to Gutsy, by going to computer/software/sources and un marking everything/this allowed the upgrade to go forward and complete. Problem solved by me.

---

