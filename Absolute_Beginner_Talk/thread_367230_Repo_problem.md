---
title: "Repo problem"
date: 2007-02-21
forum: Absolute Beginner Talk
---

### Post by grogger13 on 2007-02-21
W: GPG error: [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) edgy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783

I get this kind of error alot when using update manager and installing new software

---

### Post by Luk0r on 2007-02-21
Try this:

```
wget -q http://medibuntu.sos-sts.com/repo/medibuntu-key.gpg -O- | sudo apt-key add -
sudo apt-get update
```

---

### Post by grogger13 on 2007-02-21
thanks, seems like it worked.

---

