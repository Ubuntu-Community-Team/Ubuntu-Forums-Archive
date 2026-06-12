---
title: "[SOLVED] How to upgrade 7.04 -&amp;gt; 7.10"
date: 2008-03-28
forum: Absolute Beginner Talk
---

### Post by Anders J on 2008-03-28
It is now time to upgrade my laptop from Feisty to Gutsy.

All descriptions tell me that this should be done via System/Administration/Update Manager, which should prompt me with the notification that 7.10 is available.

But this is not the case.

How do I invoke this manually?

---

### Post by NightwishFan on 2008-03-28
I believe you can try:
```
update-manager -d
```

---

### Post by Anders J on 2008-03-28
Nope, all switches only produces the same result that my system is already up to date.

---

### Post by kpkeerthi on 2008-03-28
See [http://www.howtogeek.com/howto/linux/upgrade-ubuntu-from-feisty-to-gutsy/](http://www.howtogeek.com/howto/linux/upgrade-ubuntu-from-feisty-to-gutsy/)

If it doesn't help, manually change to gutsy repositories and upgrade per instructions [here]("http://ubuntuguide.org/wiki/Ubuntu:Gutsy#Manual_Method_for_Adding_Repositories")

And then do 
```
sudo aptitude update && sudo aptitude dist-upgrade
```

---

### Post by Anders J on 2008-03-28
Ended up doing it manually and I made also a  mistake since I didn't know how to resolve a terminal dialogue correctly.  it took a dpkg and some time to get it all resolved. But it is still hard to understand the sometimes very distinct difference between the documented behaviour and reality!

So now the notebook is up and running Gutsy and I still have the dual head VGA, WiFi and sound running.

Had some trouble to find a better driver  to take care of the 3G network PC card since  vwdial disappeared, and I still need to downgrade Audacity since the new version is inferior, but those were small problems.

---

