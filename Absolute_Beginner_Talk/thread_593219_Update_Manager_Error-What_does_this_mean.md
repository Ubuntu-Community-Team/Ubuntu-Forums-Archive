---
title: "Update Manager Error-What does this mean?"
date: 2007-10-26
forum: Absolute Beginner Talk
---

### Post by jazz1 on 2007-10-26
W: GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783

---

### Post by taurus on 2007-10-27
Open a terminal and run this command at the prompt.

```
wget -q http://medibuntu.sos-sts.com/repo/medibuntu-key.gpg -O- | sudo apt-key add -
```

---

### Post by stevensonfire on 2008-01-22
ok so i put that code in the terminal then i got
gpg: no valid OpenPGP data found.
i

---

