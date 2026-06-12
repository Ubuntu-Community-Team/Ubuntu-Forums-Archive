---
title: "pub key"
date: 2006-11-08
forum: Absolute Beginner Talk
---

### Post by captgadget on 2006-11-08
I tried to reload Synaptic last night and I got this error message back:
W: GPG error: [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY F120156012B83718
 
Can someone tell me what I need to do to fix the error?

Thanks

---

### Post by Kateikyoushi on 2006-11-08
Copy these commands to terminal and you are set.

```
gpg --keyserver subkeys.pgp.net --recv F120156012B83718
gpg --export --armor F120156012B83718 | sudo apt-key add -

```

---

