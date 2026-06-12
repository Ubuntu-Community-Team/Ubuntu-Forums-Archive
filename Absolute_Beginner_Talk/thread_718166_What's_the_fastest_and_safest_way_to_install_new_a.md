---
title: "What's the fastest and safest way to install new apps?"
date: 2008-03-07
forum: Absolute Beginner Talk
---

### Post by uchihaitachi on 2008-03-07
It takes a little time for the newest releases to reach the official repositories so I was wondering what was the fastest and safest way to get the latest apps. This is the order I worked out so please correct me where you think I've made a mistake.

1) Try Gusty Backports
2) Use Hardy Repositories
3) Use 3rd party repositories
4) Look for debian packages for ubuntu (getdeb.com)
5) Look for debian packagages
6) Package from source
7) Convert from another package to deb

What do you think of the order above?

---

### Post by bodhi.zazen on 2008-03-07
You should NOT mix repos unless you KNOW what you are doing. You need to use pinning.

[http://www.debian.org/doc/manuals/apt-howto/ch-apt-get.en.html#s-default-version](http://www.debian.org/doc/manuals/apt-howto/ch-apt-get.en.html#s-default-version)

		[http://jaqque.sbih.org/kplug/apt-pinning.html](http://jaqque.sbih.org/kplug/apt-pinning.html)

 Debian Thread : [http://forums.debian.net/viewtopic.php?t=15612](http://forums.debian.net/viewtopic.php?t=15612)

Even then, mixed repos can lead to a broken system.


If it is not in the repos I advise compiling from source and installing with checkinstall.

Just because it is a .deb does not mean it will work on Ubuntu (see my comment of pinning) and importing with Alien is also risky.

---

