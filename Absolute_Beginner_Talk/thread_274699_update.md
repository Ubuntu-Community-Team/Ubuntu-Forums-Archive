---
title: "update"
date: 2006-10-10
forum: Absolute Beginner Talk
---

### Post by LookTJ on 2006-10-10
When I open Software Updates, click Check. 

Then when it's done,

W: GPG error: [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY F120156012B83718


How do I fix it?

Thanks in advance.

---

### Post by jordanmthomas on 2006-10-10
```
gpg --keyserver subkeys.pgp.net --recv F120156012B83718
gpg --export --armor F120156012B83718 | sudo apt-key add -
```

Try importing the key.

---

### Post by LookTJ on 2006-10-10
> **jordanmthomas said:**
> ```
gpg --keyserver subkeys.pgp.net --recv F120156012B83718
gpg --export --armor F120156012B83718 | sudo apt-key add -
```

Try importing the key.Thanks that fixed it.

Taylor

---

