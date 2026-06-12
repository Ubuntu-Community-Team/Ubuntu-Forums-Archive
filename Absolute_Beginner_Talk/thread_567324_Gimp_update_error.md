---
title: "Gimp update error"
date: 2007-10-04
forum: Absolute Beginner Talk
---

### Post by AnimateDeath on 2007-10-04
My update manager popped up and told me I had updates to install, so I did. Everything went fine except for Gimp.. it keeps returning this error "E: /var/cache/apt/archives/gimp_2.4.0~rc3-1ubuntu5_i386.deb: trying to overwrite `/usr/share/doc/libgimp2.0/README', which is also in package libgimp2.0"

I tried restarting and it still gave me the error. I tried logging in as root, and did the update, but still the same error.  Any ideas????

---

### Post by notwen on 2007-10-04
Try this command out in a terminal:

```
sudo dpkg -i --force-all /var/cache/apt/archives/gimp_2.4.0~rc3-1ubuntu5_i386.deb
```

People were having similar issues on this [thread]("http://ubuntuforums.org/showthread.php?t=567185").  Hope it helps. =]

---

### Post by Paul820 on 2007-10-04
Are you running gutsy beta? If you are there is a fix in this thread [http://ubuntuforums.org/showthread.php?t=567185]("http://ubuntuforums.org/showthread.php?t=567185")

If you are not running gutsy beta, try it anyway, it's for the same package :)

Edit: Or just type what notwen put.

---

### Post by AnimateDeath on 2007-10-04
Well that fixed it...   And once again i post a problem without searching fo it first.. bad me, BAD!!!! i gotta break myself of doing that :)

---

