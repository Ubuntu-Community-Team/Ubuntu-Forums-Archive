---
title: "Ubuntu Power PC Pakages removed?"
date: 2008-09-16
forum: Apple Hardware Users
---

### Post by crapple on 2008-09-16
The ubuntu pakges for upgrade on power pc are not there any more.  So the update keeps faling to hardy.  I need to do an upgrade and not a fresh install becase I need a copy of my xorg.conf.  How do you change the source?

---

### Post by jtappin on 2008-09-16
You need to use ports.ubuntu.com instead of archive.<cc>.ubuntu.com as the repository. (Where <cc> was your country code -- there are no local ports repositories).

And if I were you I would make a copy of xorg.conf somewhere safe (like a memory stick) as I wouldn't trust the upgrade not to change it, and Hardy has problems configuring X on some Macs and Intrepid is worse (much worse).

---

