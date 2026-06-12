---
title: "Total Newbie - cdrom read permission problem"
date: 2007-09-13
forum: Absolute Beginner Talk
---

### Post by chrisginger300 on 2007-09-13
HI complete beginner, with this Ubuntu OS, but all looks good so far.
Putting in a music cd, an icon pops up and recognises it is music, I try to open the disk and I get..

Device doesn't have read permissions for this account
check the read permissions on the device.

any help please

Chris:confused:

---

### Post by bwhitaker on 2007-09-13
You need to add that user to the cdrom group.

```

$sudo usermod -G cdrom username

```

---

### Post by chrisginger300 on 2007-09-13
thanks that has sorted it!

although in system settings, disk cdrom is still stating itis disabled?

Chris

---

### Post by terrifiedkiller on 2007-10-30
> **bwhitaker said:**
> You need to add that user to the cdrom group.

```

$sudo usermod -G cdrom username

```

OMG i entered that commmand and i still have that issues now i also lost access to my windows partitions and most of the otpions on my administrative tab is gone and i cant modify user/group settings via gui anymore :(

---

