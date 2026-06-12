---
title: "Unable to view my NTFS drive"
date: 2008-03-18
forum: Absolute Beginner Talk
---

### Post by bvivek88 on 2008-03-18
Till yesterday i was able to browse through my ntfs drives,but i don't know wat happened 
today,i was not able to see my ntfs drives in my desktop and also in places menu.....please help me out:confused:

---

### Post by hyper_ch on 2008-03-18
post

```

sudo fdisk -l

```

```

df -l

```

```

sudo cat /etc/fstab

```

---

### Post by taurus on 2008-03-18
Boot your windows again and this time, shut it down cleanly.  It means no hibernation mode when you shut down windows!  Then, Ubuntu should be able to mount it again without using the force option.

---

### Post by anantshri on 2008-03-18
> **taurus said:**
> Boot your windows again and this time, shut it down cleanly.  It means no hibernation mode when you shut down windows!  Then, Ubuntu should be able to mount it again without using the force option.

that is what i was going to tell you,

coz the only cause why the auto mounting of NTFS fails is due to either a hibernation or unclean shutdown.

if you have got an unclean shutdown you can also check ntfsfix for cleaning up the partition but for hibernated partition you only have one option i.e. to restart.

---

