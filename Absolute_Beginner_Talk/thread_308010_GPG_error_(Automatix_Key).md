---
title: "GPG error (Automatix Key)"
date: 2006-11-27
forum: Absolute Beginner Talk
---

### Post by usersock on 2006-11-27
When running Update Manager (Ubuntu 10) I get:

[I]W: GPG error: [http://www.getautomatix.com](http://www.getautomatix.com) edgy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 18B52FE3521A9C7C
W: You may want to run apt-get update to correct these problems[/I]

I have re-run it several times and am still receiving the same error.

---

### Post by ThrobbingBrain66 on 2006-11-27
open a terminal and use this compound command to get the key, replacing the x's with the last 8 digits of that long number (521A9C7C)
```

gpg --keyserver subkeys.pgp.net --recv xxxxxxxx && gpg --export --armor xxxxxxxx | apt-key add -
```

---

