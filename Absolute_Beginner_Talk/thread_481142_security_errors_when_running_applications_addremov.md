---
title: "security errors when running applications add/remove"
date: 2007-06-22
forum: Absolute Beginner Talk
---

### Post by manuleka on 2007-06-22
when i run add/remove software the following warnings come up:
1)
[http://security.ubuntu.com/ubuntu/dists/feisty-security/main/source/Sources.bz2:](http://security.ubuntu.com/ubuntu/dists/feisty-security/main/source/Sources.bz2:) MD5Sum mismatch
2)
W: GPG error: [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) edgy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 58403026387EE263

... i've been trying to install IE4Linux following this guide:
[http://www.tatanka.com.br/ies4linux/page/Installation:Ubuntu](http://www.tatanka.com.br/ies4linux/page/Installation:Ubuntu)

has anyone come across this?

---

### Post by wormser on 2007-06-22
I had a similar error once and it got fix by doing an apt-get update.  Applications> Accessories> Terminal

```
sudo apt-get update
```

It might work.

---

