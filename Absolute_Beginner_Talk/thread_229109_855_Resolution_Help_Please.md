---
title: "855 Resolution Help Please"
date: 2006-08-04
forum: Absolute Beginner Talk
---

### Post by likeawalrus55 on 2006-08-04
I am new to ubuntu, and linux in general.  I have been running ubuntu for about two weeks.  I have a widescreen laptop which should be running 1280x800 resolution.  After much painstaking research and many failed attempts, i believe that installing 855 resolution by Alain Poirier ([http://perso.orange.fr/apoirier/)](http://perso.orange.fr/apoirier/)).  After i downloaded and extracted it, the readme told me i should: "
$ make
$ su
# make install"

I am unsure how exactly i am to install this.  Neither the command "make" or "make install" under any directories produced anything beyond a bad command.  I am at my wits ends, and though I love the versatility of Ubuntu, this is the first time i am seriously considering reverting to *shudders* Windows.  Please help me!!!

---

### Post by Jagot on 2006-08-04
The updated version of this package, 915resolution, is in the universe repo.  Enable it using either of these methods:

[http://psychocats.net/ubuntu/sources.php](http://psychocats.net/ubuntu/sources.php)
[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

Now, from Terminal:

```
sudo aptitude update
sudo aptitude install 915resolution
```

---

### Post by likeawalrus55 on 2006-08-04
Thank you for the information.  When i went to update it, i recieved this warning: 

Errors were encountered while processing:
 clvm
 redhat-cluster-suite
 system-config-cluster

I did not notice any difference in the resolution, even after a reboot.  I am still very confused :?

---

