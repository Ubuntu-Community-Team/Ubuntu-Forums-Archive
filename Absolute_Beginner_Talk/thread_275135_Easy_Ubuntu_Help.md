---
title: "Easy Ubuntu Help"
date: 2006-10-10
forum: Absolute Beginner Talk
---

### Post by Hillbilly Tilley on 2006-10-10
I downloaded and installed Easy Ubuntu, then I opened it and checked the repositories.  Now I get this error

W: GPG error: [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY F120156012B83718

I have tried to check other stuff to install and I get the same error.

Any suggestions?

---

### Post by jordanmthomas on 2006-10-10
[http://www.ubuntuforums.org/showthread.php?t=274699](http://www.ubuntuforums.org/showthread.php?t=274699)

---

### Post by Hillbilly Tilley on 2006-10-10
I copied and pasted the lines in the terminal it asked for the password then it said ok.

Tried easy ubuntu again and I get the same error.

---

### Post by jordanmthomas on 2006-10-10
hmmm...that is strange.
Open up Synaptic
Go to Settings --> Repositories

go to the authentification tab and make sure one like this is listed (probably the bottom one)
```
12B83718   Lionel Le Folgoc (mr_pouit) <lionel.lefolgoc@free.fr>
```

---

