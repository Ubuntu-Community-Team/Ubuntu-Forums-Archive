---
title: "Where Are Packages downloaded to?"
date: 2006-06-13
forum: Absolute Beginner Talk
---

### Post by chrism66 on 2006-06-13
I was wondering when you 'sudo apt get', or use Synaptic. Where the packages are downloaded to and if they are deleted at the end of installation? If not I would like to clean up and save some disc space. Thanks for any help in advance.

With regards,
Chris

---

### Post by aysiu on 2006-06-13
/var/cache/apt/archives

To delete, go to Settings > Preferences > Files

---

### Post by adwait on 2006-06-13
You can clean them up usiing
```
sudo apt-get clean
```

They aren't automatically deleted.

They are stored in /var/cache/apt/archives/

---

