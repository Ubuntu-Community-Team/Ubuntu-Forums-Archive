---
title: "Annoying synaptic error - no_pubkey"
date: 2007-04-08
forum: Absolute Beginner Talk
---

### Post by toscy on 2007-04-08
Every time I use synaptic or apt-get update in the console I get this error. It doesn't noticeably do anything but I'd like to get rid of it now.

I click reload to download new packages and I get this:

> W: GPG error: [http://mirror.ubuntulinux.nl](http://mirror.ubuntulinux.nl) edgy-seveas Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 49A120FD1135D466
W: GPG error: [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) edgy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 3FF0DB166A7476EA
W: GPG error: [http://archive.czessi.net](http://archive.czessi.net) breezy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A714EB87D1B1F415

I click close and everything is fine.

I know this is something I did after following a guide on the Internet. It said I had to register some kind of key or something.

Thanks for the help!

---

### Post by r00tintheb0x on 2007-04-08
Packages is this repository can be gpg authenticated. The key that is being used for signing the packages is [email]root@lupine.me.uk[/email]. You can enter this key into the APT trusted keys database with the following command:
wget [http://ubuntu.beryl-project.org/root@lupine.me.uk.gpg](http://ubuntu.beryl-project.org/root@lupine.me.uk.gpg) -O- | sudo apt-key add -

---

### Post by toscy on 2007-04-08
> **r00tintheb0x said:**
> Packages is this repository can be gpg authenticated. The key that is being used for signing the packages is [email]root@lupine.me.uk[/email]. You can enter this key into the APT trusted keys database with the following command:
wget [http://ubuntu.beryl-project.org/root@lupine.me.uk.gpg](http://ubuntu.beryl-project.org/root@lupine.me.uk.gpg) -O- | sudo apt-key add -

Thanks for the help.

I don't really understand what you said but I copied that into the terminal and it appeared to do that successfully. However the errors are still showing :confused:

---

### Post by zvacet on 2007-04-08
```
gpg --keyserver hkp://subkeys.pgp.net --recv-keys KEY
 gpg --export --armor KEY | sudo apt-key add -
```


gpg --keyserver hkp://subkeys.pgp.net --recv-keys 49A120FD1135D466
 gpg --export --armor 49A120FD1135D466  | sudo apt-key add -


Do the same with all keys

---

### Post by mikewhatever on 2007-04-08
That's not an error. It is just saying that those repositories are not recognized as standard Canonical ones, therefore, no signature could be verified. Nothing is broken, and you can contact them OK, so leave it as is.

---

### Post by toscy on 2007-04-09
Thanks a lot zvacet, problem solved. :)

---

