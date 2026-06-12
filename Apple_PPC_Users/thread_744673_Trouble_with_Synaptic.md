---
title: "Trouble with Synaptic"
date: 2008-04-03
forum: Apple PPC Users
---

### Post by deamon_knight on 2008-04-03
It crashes! I've tried uninstalling & reinstalling with apt-get remove and no luck. Here is the error:

terminate called after throwing an instance of 'std::logic_error'
  what():  basic_string::_S_construct NULL not valid
Aborted (core dumped)

Any suggestion? I'm using Ubuntu 7.04 on a powerbook G3. Thanks.

---

### Post by stream303 on 2008-04-04
Hmm.. is this from a fresh install, or from a series of upgrades etc?  Have you had a lot of install failures prior to this, even though synaptic seemed to work?

You may want to see this bug report which might indicate that your /var/cache/apt/*.bin files may be corrupted, and need possible deletion or cleaning.

[https://bugs.launchpad.net/ubuntu/+source/apt/+bug/72475](https://bugs.launchpad.net/ubuntu/+source/apt/+bug/72475)

I know it is a longshot, but have you tried triggering an fsck disk check on the next reboot?

```
sudo touch /forcefsck
```

---

