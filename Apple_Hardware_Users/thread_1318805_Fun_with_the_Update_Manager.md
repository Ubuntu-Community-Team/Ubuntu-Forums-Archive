---
title: "Fun with the Update Manager"
date: 2009-11-07
forum: Apple Hardware Users
---

### Post by moocow1452 on 2009-11-07
Hey all,

With my computer being a 8 year old G3 iBook (PowerPC, remember that now,) with the latest software from Canonical, I don't expect everything to run perfectly. But this latest distro has gotten a bit irritating in that repositories that should be running fine are firing blanks and I don't know why. 

My question is, these repos look important, and I am not intrested in turning off updates entirely,  so what do I do to make that red "!" circle go away? 

Error as follows:
```
GPG error: http://packages.medibuntu.org karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783
Failed to fetch http://ports.ubuntu.com/dists/karmic/Release  Unable to find expected entry  partner/binary-powerpc/Packages in Meta-index file (malformed Release file?)
Failed to fetch http://ports.ubuntu.com/dists/karmic-security/Release  Unable to find expected entry  partner/binary-powerpc/Packages in Meta-index file (malformed Release file?)
Failed to fetch http://ports.ubuntu.com/dists/karmic-updates/Release  Unable to find expected entry  partner/binary-powerpc/Packages in Meta-index file (malformed Release file?)
Failed to fetch http://ports.ubuntu.com/dists/karmic-proposed/Release  Unable to find expected entry  partner/binary-powerpc/Packages in Meta-index file (malformed Release file?)
Failed to fetch http://packages.medibuntu.org/dists/karmic/free/binary-powerpc/Packages.gz  404  Not Found [IP: 88.191.79.39 80]
Failed to fetch http://packages.medibuntu.org/dists/karmic/non-free/binary-powerpc/Packages.gz  404  Not Found [IP: 88.191.79.39 80]
Failed to fetch http://ports.ubuntu.com/dists/karmic-backports/Release  Unable to find expected entry  partner/binary-powerpc/Packages in Meta-index file (malformed Release file?)
Some index files failed to download, they have been ignored, or old ones used instead.
```

Bonus Question: Tomboy is acting up, and it's latest update package was corrupted, or something. Now everytime I update, Tomboy wants to reinstall, but fails, and goes back in line for the next round. I tried synaptic, command line, and add/remove, nothing on all counts. Anyway I can cure this Update Constipation?

---

### Post by natgab on 2009-11-08
It seems that Koala 9.10 is still pretty buggy.  

I have Jaunty 9.04 on my Power Mac, work really well.  I don't think that I will update the version until 10.4. Even then, I would probably wait at least a month to make sure.

Maybe someone with more experience can tell you if you can downgrade back to 9.04?  That may be a better solution.

---

### Post by moocow1452 on 2009-11-08
Ok, any other opinions?

---

### Post by MelDJ on 2009-11-08
the gpg error comes up because you dont have the gpg key for medibuntu.
add it by following this: _[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)_[]("http://packages.medibuntu.org/medibuntu-key.gpg")

---

