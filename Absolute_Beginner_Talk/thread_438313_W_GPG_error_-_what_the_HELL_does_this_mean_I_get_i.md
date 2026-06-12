---
title: "W: GPG error - what the HELL does this mean? I get it when I do update manager check"
date: 2007-05-09
forum: Absolute Beginner Talk
---

### Post by hamishw on 2007-05-09
W: GPG error: [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783

this is the message I get when I tell update manager in Feisty to check for updates.... please help, can I fix it?
thanks
Hamish

---

### Post by benanzo on 2007-05-09
you need to get the GPG key in order to access their repository.  This is for your security so you can rely on their packages that they came from them.

do this is a terminal
```
wget -q http://medibuntu.sos-sts.com/repo/medibuntu-key.gpg -O- | sudo apt-key add -
```

then

```
sudo apt-get update
```

[http://medibuntu.sos-sts.com/repository.php](http://medibuntu.sos-sts.com/repository.php)

---

### Post by mazirian on 2007-05-09
YOu need to add that public key to your keyring so apt may ensure that the packages are signed.

Something like this, I think:

```

gpg --keyserver subkeys.pgp.net --recv 2EBC26B60C5A2783
gpg --export --armor 2EBC26B60C5A2783 | sudo apt-key add -

```

If this isn't quite right, the answer is certainly already on the forums somewhere.  it was a common question a while back.

---

### Post by hamishw on 2007-05-09
thanks, done it.
Hamish

---

