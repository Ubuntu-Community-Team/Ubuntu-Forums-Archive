---
title: "un able to update....."
date: 2007-04-11
forum: Absolute Beginner Talk
---

### Post by JayDeePlus on 2007-04-11
i get this message when my update manager tries to update

W: GPG error: [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) edgy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 3FF0DB166A7476EA


is it finding beryl and not able to load?

---

### Post by o_fortuna on 2007-04-11
> **JayDeePlus said:**
> i get this message when my update manager tries to update

W: GPG error: [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) edgy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 3FF0DB166A7476EA


is it finding beryl and not able to load?
You are missing beryl's gpg key. Do this: Open Applications--Accessories--Terminal and paste in these commands one by one, entering your password where prompted:
```
sudo -s
wget http://ubuntu.beryl-project.org/root@lupine.me.uk.gpg -O- | apt-key add -
exit
```

Then try update-manager again.

---

### Post by JayDeePlus on 2007-04-11
thanks it worked perfectly

---

