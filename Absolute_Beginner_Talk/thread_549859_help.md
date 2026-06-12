---
title: "help"
date: 2007-09-13
forum: Absolute Beginner Talk
---

### Post by waterspider on 2007-09-13
does anyone know how to fix this problem;-
 GPG error: [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783

---

### Post by hyper_ch on 2007-09-13
(1) Please us a descriptive topic title that has to do with your problem

(2) You didn't add the GPG keys for the medibuntu repo to your list. Have a read at the medibuntu repo to see how to do it.

---

### Post by Spr0k3t on 2007-09-13
**Feisty:**```
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update
```

from this page: [http://medibuntu.sos-sts.com/repository.php](http://medibuntu.sos-sts.com/repository.php)

---

### Post by Maestro23 on 2007-09-13
> **Spr0k3t said:**
> **Feisty:**```
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update
```

from this page: [http://medibuntu.sos-sts.com/repository.php](http://medibuntu.sos-sts.com/repository.php)

Beat me to it. :)

---

