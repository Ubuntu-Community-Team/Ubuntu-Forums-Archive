---
title: "Updating in general"
date: 2007-12-19
forum: Absolute Beginner Talk
---

### Post by kernel tom on 2007-12-19
Hey all,

So i've been noticing that a few of my packages and applications are a few releases behind in updates.  I keep track of updating my box by myself, but somehow not everything is getting updated.  I've used the update manager as well as just using "apt-get update" then "apt-get upgrade", and it works for most applications but not all.

The applications I'm updating are in the ubuntu repositories, and I have installed them all with apt or dpkg.

Does ubuntu wait till a certain version gets realeased in order to for it to come up in updates?  Or is there any option I can change somewhere such that apt will realize if a newer version is available?

Thanks,
Tom

---

### Post by reckless2k2 on 2007-12-19
where is the source for your info on a package being updated? I mean if you are talking about a source site versus ubuntu packaging then there will sometimes be a slight lag unless you compile from the source.

---

### Post by kernel tom on 2007-12-19
the sources are from the repositories, not an actual tarball or deb package.

will ubuntu's repositories not upgrade you from say buku.v2.0 to buku.v.2.3?  that's the type of issue i am running into.

thanks

---

### Post by bump_ on 2007-12-19
It will upgrade you from baku2.0 to baku 2.3 if baku has been upgraded in the repos. Sometimes there is a lag between when a new version is released and when it is update in the repos. Sometimes it is never updated in the repos and you have to get the source or a .deb package manually to upgrade it yourself.

---

### Post by kernel tom on 2007-12-19
oh ok,

thanks for the info, kinda sad tho that ubuntu won't upgrade some important applications (SSH) to their newest most secure versions on its own.

---

### Post by Hospadar on 2007-12-19
The thing is a lot of packages are handled by third-party maintainers, and building a rock-solid .deb can take a litte while to debug, and also to make sure the new version plays nice with ubuntu.

---

