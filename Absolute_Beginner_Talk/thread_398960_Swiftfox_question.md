---
title: "Swiftfox question"
date: 2007-04-01
forum: Absolute Beginner Talk
---

### Post by 67GTA on 2007-04-01
I am using Dapper. I managed to install Firefox 2 and was wanting to reinstall Swiftfox. If I use Automatix to reinstall Swiftfox, will it install it with Firefox 2 or try to install it with Firefox 1.5? I had to leave 1.5 for version 2 to work.

---

### Post by sumguy231 on 2007-04-01
Instead of using Automatix to install Swiftfox, I would just reccomend putting the Swiftfox repository in your /etc/apt/sources.list. I'm using Edgy myself, but it's just a general Debian build so it should work in Dapper too. This way it will update like any other 'regular' program on your system. Add this line to /etc/apt/sources.list:
```
deb [http://getswiftfox.com/builds/debian](http://getswiftfox.com/builds/debian) unstable non-free
```
Then run 'apt-get update' and 'apt-get install swiftfox-<platform> 'to install it. If you don't know the package name for your platform, then do 'aptitude search swiftfox'. An example would be 'swiftfox-athlon-xp' for Athlon XP and Duron processors (Some packages like the Duron package are just virtual packages that point to other packages like the Athlon-XP package).
I hope that wasn't too confusing, I can be bad at wording things sometimes.

---

### Post by 67GTA on 2007-04-01
That worked like a charm. I would rather stuff come from the Synaptic manager. Where can you get specialized repositories like this one? I have installed a couple of other programs that would be easier to update this way.

---

### Post by sumguy231 on 2007-04-02
There are repositories for Ubuntu for various things all over the place, but they all come with the caveat that something is likely to break if you use them. Especially if you use bleeding-edge repositories. Plus, it all depends on what you want provided.

---

