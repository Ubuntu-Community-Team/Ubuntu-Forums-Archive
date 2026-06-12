---
title: "Why no FF 2.0 in Dapper repos?"
date: 2007-03-19
forum: Absolute Beginner Talk
---

### Post by ricardisimo on 2007-03-19
I'm on Dapper here at home for the next month, so it's no big deal either way, just waiting a bit, but updating Firefox is one of the few things making me consider Edgy in the meantime.

Furthermore, what happens if I comment out the Dapper repos and momentarily enter Edgy's for the purposes of loading FF 2.x? Thanks in advance.

---

### Post by diskotek on 2007-03-19
edit: yes there is a better way as Obor mentioned:
[https://help.ubuntu.com/community/FirefoxNewVersion](https://help.ubuntu.com/community/FirefoxNewVersion)

---

### Post by Obor on 2007-03-19
[This thread]("http://ubuntuforums.org/showthread.php?t=330386") might help.

---

### Post by alienexplorers on 2007-03-19
I just went to the Mozilla website, downloaded Firefox 2.0.0.2 and loaded it into my home directory.  I used "firefox -ProfileManager" to setup a new profile.  I am also running firefox 3.0a3 by downloading it setting it up in my home directory.

---

### Post by ricardisimo on 2007-03-20
Someone mentioned FF 3.x a few months ago, and I couldn't even find it mentioned in Google or Yahoo searches, much less download it to try it out. What's up with that? Where would I find it?

Finally, is it actually _unsafe_ for me to temporarily use the Edgy repos to get FF 2? If I have to choose a method, that's what I would fell most comfortable doing, for whatever reason. I suppose the other question is if it would even work; was FF 2.0 an upgrade along with Edgy, or was 1.5 removed and replaced utterly?

Thanks again.

---

### Post by mcduck on 2007-03-20
> **ricardisimo said:**
> Someone mentioned FF 3.x a few months ago, and I couldn't even find it mentioned in Google or Yahoo searches, much less download it to try it out. What's up with that? Where would I find it?

Finally, is it actually _unsafe_ for me to temporarily use the Edgy repos to get FF 2? If I have to choose a method, that's what I would fell most comfortable doing, for whatever reason. I suppose the other question is if it would even work; was FF 2.0 an upgrade along with Edgy, or was 1.5 removed and replaced utterly?

Thanks again.

Most likely you'd break your system by installing Firefox from Edgy's repositories. Many other applications depend on Firefox, that's the reason why FF 2.0 is not available in Dapper repositories. Upgrading from FF1.5 to FF2.0 would be too complex thing to do, requiring you to also upgrade undefined amount of other packages as well. You'd better just do it like everybody else does, installing FF2.0 as extra package instead of upgrading 1.5 to 2.0.

---

