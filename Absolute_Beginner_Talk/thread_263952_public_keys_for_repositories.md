---
title: "public keys for repositories"
date: 2006-09-23
forum: Absolute Beginner Talk
---

### Post by k9brand on 2006-09-23
Hi,

I am trying to add to my sources.list so I can get musicbrainz

deb [http://users.musicbrainz.org/~luks/ubuntu](http://users.musicbrainz.org/~luks/ubuntu) dapper main

But I get the following:

```
W: GPG error: http://users.musicbrainz.org dapper Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 3A39A02A92132F7B

```

I've gotten a key before for something else, but can someone tell me how (for this one) and why?

---

### Post by jordanmthomas on 2006-09-24
```
gpg --keyserver subkeys.pgp.net --recv 3A39A02A92132F7B
gpg --export --armor  3A39A02A92132F7B | sudo apt-key add -
```

In general,
```
# gpg --keyserver subkeys.pgp.net --recv KEY
# gpg --export --armor KEY | sudo apt-key add -
```

Then try updating.  A public key just ensures that you are getting the files meant to be sent to you by the author.

---

