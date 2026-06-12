---
title: "remote /etc/fstab entries don't mount over wireless"
date: 2007-05-22
forum: Absolute Beginner Talk
---

### Post by Emeriz on 2007-05-22
When I am connecting over a wired connection my remote /etc/fstab entries work with no issues.  When I am on wireless neither of my remote shares mount automatically, but I can mount them manually without problem.

The error I see is -113, no route to host so it looks like the mount process is trying to occur before the network is fully up.  Any ideas on how to work around this?

Thanks,

Em

---

### Post by dbott67 on 2007-05-22
I think this is due to the fact that NetworkManager does not obtain an IP address until after you login.

You have a few options:

1. Set a static IP for wireless

2. Run this command after logging in:
```
sudo mount -a
```

-Dave

---

