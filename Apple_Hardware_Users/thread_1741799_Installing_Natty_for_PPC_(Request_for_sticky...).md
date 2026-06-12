---
title: "Installing Natty for PPC (Request for sticky...)"
date: 2011-04-28
forum: Apple Hardware Users
---

### Post by pauljwells on 2011-04-28
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/756719]("https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/756719")

The live cd for ppc Natty hangs during installation because the mirror for the repos has no been set. I don't know if this can be changed from within the live session but I can confirm that the alternate installer works, you have to type

```
ports.ubuntu.com
```

as the mirror at the appropriate point.

---

### Post by aectow on 2011-04-29
Had the same problem. Will try with the alternate installer.
Where should I enter: *ports.ubuntu.com* ?

Thanks

---

### Post by dlgn on 2011-04-29
Where *is* the ppc build for Natty? I can only find the daily build.
(I checked releases.ubuntu.com, cdimage.ubuntu.com.)


Thanks, dlgn

---

### Post by pauljwells on 2011-04-29
I just used the daily build pre-beta and keep upgrading - 'release' is a pretty arbitrary milestone!

---

### Post by pauljwells on 2011-04-29
> **aectow said:**
> Had the same problem. Will try with the alternate installer.
Where should I enter: *ports.ubuntu.com* ?

Thanks

In the alternate installer it asks for a mirror around halfway through the install. Just type in the ports.ubuntu.com line, accept default for the next input and I think that's the ast thing it asks for.

---

