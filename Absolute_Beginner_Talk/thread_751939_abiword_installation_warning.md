---
title: "abiword installation warning"
date: 2008-04-11
forum: Absolute Beginner Talk
---

### Post by scientist1971 on 2008-04-11
in synpatic package manager when requesting abiword installation I get the following message:

Warning
You are about to install software that can't be authenticated!  Doing this could allow a malicious individual to damage or take control of your system.

Is this just a windows style over exaggeration of potential danger or is the threat real?
Any help would be appreciated (as always)

---

### Post by tangibleorange on 2008-04-11
> **scientist1971 said:**
> in synpatic package manager when requesting abiword installation I get the following message:

Warning
You are about to install software that can't be authenticated!  Doing this could allow a malicious individual to damage or take control of your system.

Is this just a windows style over exaggeration of potential danger or is the threat real?
Any help would be appreciated (as always)

don't worry! i think it's just saying that Canonical (guys who make Ubuntu) can't be held responsible if the software messes up your system. it's nothing to worry about - you can go ahead and install it without any worries.

---

### Post by erginemr on 2008-04-11
This also happens when you enable extra repositories (such as GetDeb.net) and try to install packages hosted in those repositories. No need to worry again...

---

### Post by kpkeerthi on 2008-04-11
> **scientist1971 said:**
> in synpatic package manager when requesting abiword installation I get the following message:

Warning
You are about to install software that can't be authenticated!  Doing this could allow a malicious individual to damage or take control of your system.

Is this just a windows style over exaggeration of potential danger or is the threat real?
Any help would be appreciated (as always)

Usually, when you add an external repository, you add the GPG public keys (sample [gpg]("http://packages.medibuntu.org/medibuntu-key.gpg") key for [medibuntu]("https://help.ubuntu.com/community/Medibuntu") repository) along with it. So when ubuntu downloads a package from the repository it can authenticate that the package is indeed from that repository by verifying package's digital signature with the public key you already have. 

But not all external repositories provide GPG keys. Ubuntu warns when you attempt to install from such repositories as the packages could not be verified for it authenticity. A non-verified package could possibly be malicious.

---

