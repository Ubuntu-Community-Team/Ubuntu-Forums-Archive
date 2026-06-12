---
title: "New to Ubuntu keep getting this error"
date: 2007-09-09
forum: Absolute Beginner Talk
---

### Post by big_tiger on 2007-09-09
> W: GPG error: [http://apt.cerkinfo.be](http://apt.cerkinfo.be) unstable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A35A4E6EF00175CA
W: You may want to run apt-get update to correct these problems


I ran sudo apt-get update and I get ^^^that error message at the end.  Is that something I should be worried about?

---

### Post by mendingo84 on 2007-09-09
not really ;)

---

### Post by FuturePilot on 2007-09-09
It's not really a big deal. It just means that you don't have the gpg key for a third party repo that you added.
Try this
```
gpg --keyserver hkp://wwwkeys.eu.pgp.net --recv-keys F00175CA
```
```
gpg --armor --export F00175CA | sudo apt-key add -
```
```
sudo apt-get update
```
It should go away after that.

---

### Post by big_tiger on 2007-09-09
Thanks FuturePilot, that worked!

---

