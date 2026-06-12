---
title: "Apt-get install?"
date: 2007-10-30
forum: Absolute Beginner Talk
---

### Post by kurisutofuaa on 2007-10-30
When I do a apt-get install "Package" most of the time a get a list of recommended packages, I was wondering how do I set it up so that it will install all the recommended packages every time a install a "Package" with apt-get install?

---

### Post by rudeboyskunk on 2007-10-30
I'm not sure if there's an easier way, but the way I've always done it is to answer "n" when it asks me if I am sure I want to install.  I then retype apt-get install whatever, typing in the recommended packages as well.

---

### Post by Seisen on 2007-10-30
Use aptitude instead it will pull of the dependencies for a package.

```
sudo aptitude install packagename
```

---

### Post by maybeway36 on 2007-10-30
I thought it did anyway. Strange.
I think appending --with-recommends will do the trick.

---

### Post by Maestro23 on 2007-10-30
Apt-Get vs. Aptitude: [http://www.psychocats.net/ubuntu/aptitude](http://www.psychocats.net/ubuntu/aptitude)

---

### Post by oldos2er on 2007-10-30
Using Synaptic Package Manager, go to Settings, Preferences, and tick the box next to 'Consider recommended packages as dependencies.'

 I believe this only works in Synaptic, not using apt-get in a terminal.

---

