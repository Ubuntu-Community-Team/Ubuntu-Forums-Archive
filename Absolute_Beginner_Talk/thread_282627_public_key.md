---
title: "public key"
date: 2006-10-23
forum: Absolute Beginner Talk
---

### Post by rowster27 on 2006-10-23
W: GPG error: [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY F120156012B83718

an error occured when i refreshed synaptic (clicking the check button)

how can i repair this error?:confused:

---

### Post by tommcd on 2006-10-23
See this page:
[http://doc.ubuntu-fr.org/doc/plf](http://doc.ubuntu-fr.org/doc/plf)
Look at "Repository authentication" You need to add that key to APT's 'trusted' database.
You need to be careful with packages from these repos. I seem to remember reading that they  can cause problems. Sorry, can't find specific links at the moment.

---

### Post by Perfect Storm on 2006-10-23
```
gpg --keyserver subkeys.pgp.net --recv F120156012B83718
gpg --export --armor F120156012B83718 | sudo apt-key add -
```

It isn't an error, it's a safty device, because you are adding an un-official source to your sourcelist (which can cause problem for your system).

---

