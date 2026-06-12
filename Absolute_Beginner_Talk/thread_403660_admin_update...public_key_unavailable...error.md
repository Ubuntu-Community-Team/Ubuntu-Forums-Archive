---
title: "admin update...public key unavailable...error"
date: 2007-04-07
forum: Absolute Beginner Talk
---

### Post by lg3 on 2007-04-07
Hello,
what does this mean:
"W: GPG error: [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) edgy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783"

Is  it a problem with my source list or something else?

Thanks.

---

### Post by zvacet on 2007-04-07
```
gpg --keyserver hkp://subkeys.pgp.net --recv-keys KEY
 gpg --export --armor KEY | sudo apt-key add -
```



gpg --keyserver hkp://subkeys.pgp.net --recv-keys 2EBC26B60C5A2783
 gpg --export --armor 2EBC26B60C5A2783  | sudo apt-key add -

---

### Post by Dropknee on 2007-04-07
nice that was fast :-) thx

---

### Post by lg3 on 2007-04-07
thank you. that remedied the problem. can you explain what that did so in the future I could sniff it out on my own? I appreciate the time.

---

### Post by eldragon on 2007-04-19
hmm, have exact same problem here...same key.....same server....same everything.

yet i cant retrieve the key:

:~$ gpg --keyserver hkp://subkeys.pgp.net --recv-keys 2EBC26B60C5A2783
gpg: requesting key 0C5A2783 from hkp server subkeys.pgp.net
gpg: keyserver timed out
gpg: keyserver receive failed: keyserver error


any clue?

---

### Post by Seisen on 2007-04-19
I think their servers acting up, because I have noticed sometimes that I have slow dowloads from them and I have had the same problem you have had. I just kept trying to get it work and it finally did.

---

