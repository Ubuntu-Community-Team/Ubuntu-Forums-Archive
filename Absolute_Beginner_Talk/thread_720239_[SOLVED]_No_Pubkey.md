---
title: "[SOLVED] No Pubkey"
date: 2008-03-10
forum: Absolute Beginner Talk
---

### Post by ellalan on 2008-03-10
Hi
When I try to reload the Synaptic Package Manager I get an error message:
w:GPG error@ [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy Release: The following signatures couldn't be verified because the publickey is not available:NO_PUBKEY 2EBC 26 B60CSA2783.

Could someone help me to overcome this problem please. Thank you.

---

### Post by kesman on 2008-03-10
wget -q [http://packages.medibuntu.org/medibuntu-key.gpg](http://packages.medibuntu.org/medibuntu-key.gpg) -O- | sudo apt-key add -

did you do this after you added the source to sources.list ?

---

### Post by zvacet on 2008-03-10
Follow **kesman** advice and after that refresh your sourcew list with

```
sudo apt-get update
```

---

### Post by ellalan on 2008-03-10
Thank you Guys, everything is fine.


Happiness eez Ubuntu.

---

### Post by jmr230 on 2008-04-27
Same problem, fix worked.  Thanks.

---

