---
title: "NO_PUBKEY 3E231AC7F4ECF181   what is again happened"
date: 2007-12-21
forum: Absolute Beginner Talk
---

### Post by Heaf on 2007-12-21
W: GPG error: [http://download.tuxfamily.org](http://download.tuxfamily.org) gutsy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 3E231AC7F4ECF181

---

### Post by zvacet on 2007-12-21
[B]gpg --keyserver hkp://subkeys.pgp.net --recv-keys KEY
 gpg --export --armor KEY | sudo apt-key add -[/B]


So,you will type in terminal

gpg --keyserver hkp://subkeys.pgp.net --recv-keys 3E231AC7F4ECF181
 gpg --export --armor 3E231AC7F4ECF181  | sudo apt-key add -

---

