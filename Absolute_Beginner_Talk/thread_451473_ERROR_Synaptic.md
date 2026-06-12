---
title: "ERROR Synaptic"
date: 2007-05-22
forum: Absolute Beginner Talk
---

### Post by burt_57 on 2007-05-22
Why do I get this error in Synaptic

W: GPG error: [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783

---

### Post by Sparkster185 on 2007-05-22
Some repositories/packages require you to get a GPG key first.  The installation instructions should have included code for how to get the key and then how to add it to Synaptic.

---

### Post by taurus on 2007-05-22
Applications -> Accessories -> Terminal
```
wget -q http://medibuntu.sos-sts.com/repo/medibuntu-key.gpg -O- | sudo apt-key add -
sudo aptitude update
sudo aptitude upgrade
```

---

