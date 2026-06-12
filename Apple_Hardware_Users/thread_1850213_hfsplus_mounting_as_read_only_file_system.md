---
title: "hfsplus mounting as read only file system"
date: 2011-09-26
forum: Apple Hardware Users
---

### Post by pier25 on 2011-09-26
Yesterday netatalk and avahi worked perfectly.

Today all the hfsplus drives are being mounted in read only mode.

Is it possible that journaling was enabled again by netatalk via afp?

The error message that finder says is

> Something wrong with the volume's CNID DB, using temporary CNID DB instead.Check server messages for details. Switching to read-only mode.

---

### Post by xdracco on 2012-09-24
A couple of things to check...

1. Make sure your volumes allow the user/group that your share is set for (permissions)
2. Verify that the option 'rwlist' is configured for your shared volumes

It would help if you posted AppleVolumes.default. Yes, I know it worked perfectly yesterday but if you want help... we need help from you. =)

---

