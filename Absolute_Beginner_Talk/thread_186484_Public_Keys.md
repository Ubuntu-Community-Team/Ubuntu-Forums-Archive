---
title: "Public Keys?"
date: 2006-06-02
forum: Absolute Beginner Talk
---

### Post by Caraethelanea on 2006-06-02
What are they? I recieved this message:

W: GPG error: [http://www.debian-multimedia.org](http://www.debian-multimedia.org) testing Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 07DC563D1F41B907

Thanks, Carae

---

### Post by S{yndrom}e on 2006-06-02
wget [http://www.debian-multimedia.org.key.asc](http://www.debian-multimedia.org.key.asc) -O - | sudo apt-key add -

Try doing that command in terminal, then run

sudo apt-get update 

again and see if that works.

---

### Post by jobezone on 2006-06-02
You should ask it from that repository maintainer ([http://www.debian-multimedia.org)](http://www.debian-multimedia.org)). And, unless you really know what you're doing, you shouldn't be using extra non-ubuntu repositories.

---

### Post by Caraethelanea on 2006-06-02
Thanks for helping me!

~Carae

---

### Post by vidak on 2006-06-02
answering your first question: this is GPG signature to verify the repository.
For further reading:
[https://wiki.ubuntu.com/GPGArchiveSignature](https://wiki.ubuntu.com/GPGArchiveSignature) (not ready yet)
[https://wiki.ubuntu.com/GnuPrivacyGuardHowto](https://wiki.ubuntu.com/GnuPrivacyGuardHowto)

---

