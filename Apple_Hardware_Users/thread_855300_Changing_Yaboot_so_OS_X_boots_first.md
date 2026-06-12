---
title: "Changing Yaboot so OS X boots first"
date: 2008-07-10
forum: Apple Hardware Users
---

### Post by linuxuser28 on 2008-07-10
How can I change Yaboot so that OS X is the default OS to boot to instead of Linux?
Thanks.

---

### Post by tiresia on 2008-07-10
You must edit your /etc/yaboot.conf
Open a Terminal and do:

```
sudo nano /etc/yaboot.conf
```

Add in that file:

```
defaultos=macosx
```

Exit (^X) and Save that file (say Yes)
Now you must run, in order that yaboot start with the changes you have made

```
sudo ybin
```

That's all

---

