---
title: "Verifying openpgp keys"
date: 2006-11-01
forum: Absolute Beginner Talk
---

### Post by parthbakshi16 on 2006-11-01
Hello,
     I have uploaded my openpgp keys on the ubuntu keyserver for launchpad and it has sent me an email to verify which it has asked me to decrypt how do i decrpy that message .

THanks in advance

---

### Post by Jussi Kukkonen on 2006-11-01
```
gpg --output cleartext.txt --decrypt encrypted_message.txt
```

Although just *gpg filename* probably works too.

---

