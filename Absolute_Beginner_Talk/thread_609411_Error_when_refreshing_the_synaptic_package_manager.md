---
title: "Error when refreshing the synaptic package manager."
date: 2007-11-10
forum: Absolute Beginner Talk
---

### Post by Kuroda_Shun on 2007-11-10
I get this error durring refresh. Is this why I can't install any software?

W: GPG error: [http://www.getautomatix.com](http://www.getautomatix.com) edgy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY CC919A31E23C5FC3

---

### Post by matthewcraig on 2007-11-10
Automatix is not recommended, supported or needed.
See [http://mjg59.livejournal.com/77440.html](http://mjg59.livejournal.com/77440.html)

---

### Post by taurus on 2007-11-10
Why not just edit your /etc/apt/sources.list

```
gksudo gedit /etc/apt/sources.list
```
and remove the automatix repo from it.  Then, save it and run

```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by Kuroda_Shun on 2007-11-10
Thanks, Good to know, I was told to install with automatrix. How do I get rid of the error?
Thanks for your help. I can't install any flash player (can't watch video)

*edit. Thanks taurus, that did the job..

---

### Post by taurus on 2007-11-10
[https://help.ubuntu.com/community/RestrictedFormats/Flash](https://help.ubuntu.com/community/RestrictedFormats/Flash)

---

