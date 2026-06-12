---
title: "how to downgrade from Hardy to Gutsy ?"
date: 2008-04-09
forum: Absolute Beginner Talk
---

### Post by bred on 2008-04-09
[COLOR="Navy"]Hi everybody,
I would like to know how to downgrade from hardy to gutsy without a coplete format?
I have multiples errors on Hardy, sometimes it just freezes from nothing...I understand is a beta version...any suggestions pls?[/COLOR]

---

### Post by philinux on 2008-04-09
I'm afraid the only way to do that is reinstall.

However if you stick with it the updates should fix things. 

Help is available here to get your errors sorted.

[http://ubuntuforums.org/forumdisplay.php?f=305](http://ubuntuforums.org/forumdisplay.php?f=305)

---

### Post by forestpixie on 2008-04-09
you'll need to reinstall it I believe -

Edit - the beta gets frozen in 4 days - so hopefully most will be ready, as philinuz says search the forum - good luck

---

### Post by Cypher on 2008-04-09
As the others have suggested, downgrading isn't easy..and random problems are on par for Beta software..so it is usually not adviced to upgrade to a Beta on your regular computer, or if you're not capable of dealing/working through the errors..

---

### Post by bred on 2008-04-09
thx for answers guys

---

### Post by bodhi.zazen on 2008-04-09
You *may* be able to downgrade, however it may be easier to re-install.

1. manually add the gutsy repos back into /etc/apt/sources list.

2. Edit /etc/apt/preferences to :

> Package: *
Pin: release a=gutsy
Pin-Priority: 1001

Package: *
Pin: release a=hardy
Pin-Priority: 50

3. Now try it :

```
sudo apt-get update
sudo apt-get update
```

I would not be surprised if it failed. You will have to manually downgrade each package that fails, probably by downloading the appropriate .deb and uninstalling and re-installing manually.

Note: Try this at your own risk, be prepared for total system failure (ie back up your data first).

Note: I personally have not run a so called mixed system (ie pinning) in a few years, so it may not work as I outlined.

References on pinning :

[http://www.debian.org/doc/manuals/apt-howto/ch-apt-get.en.html#s-default-version](http://www.debian.org/doc/manuals/apt-howto/ch-apt-get.en.html#s-default-version)

[http://jaqque.sbih.org/kplug/apt-pinning.html](http://jaqque.sbih.org/kplug/apt-pinning.html)

---

