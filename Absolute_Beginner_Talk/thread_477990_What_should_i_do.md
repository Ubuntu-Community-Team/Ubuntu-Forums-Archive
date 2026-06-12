---
title: "What should i do?"
date: 2007-06-18
forum: Absolute Beginner Talk
---

### Post by uthturn on 2007-06-18
i get this error when i try to apt -get update E: Could not open lock file /var/lib/apt/lists/lock - open (13 Permission denied)
 E: Unable to lock the list directory
 tj@tj-desktop:~$ apt -get update
 The program 'apt' can be found in the following packages:
  * sun-java5-jdk
  * sun-java6-jdk
 Try: sudo apt-get install <selected package>
 Make sure you have the 'multiverse' component enabled
 can anyone tell me how to fix it
 i have multiverse enabled

---

### Post by Clay_Banger on 2007-06-18
post what this outputs please:
```
sudo apt-get update
```

---

### Post by RedSquirrel on 2007-06-18
Indeed, you need sudo to run that command. 

Also, it is "apt-get" _not_ "apt[SPACE]-get". ;)

---

### Post by uthturn on 2007-06-18
i get this error W: GPG error: [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783
W: You may want to run apt-get update to correct these problems when i do that

---

### Post by Clay_Banger on 2007-06-18
> **uthturn said:**
> i get this error W: GPG error: [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783
W: You may want to run apt-get update to correct these problems when i do that
well there doesnt appear to be much wrong apart from the public key thing, im not sure how to fix that, but it is only a nuisance and wont stop you from doing anything.

---

### Post by zvacet on 2007-06-19
[B]gpg --keyserver hkp://subkeys.pgp.net --recv-keys KEY
gpg --export --armor KEY | sudo apt-key ad[/B]d -



gpg --keyserver hkp://subkeys.pgp.net --recv-keys 2EBC26B60C5A2783
gpg --export --armor 2EBC26B60C5A2783  | sudo apt-key add -

---

