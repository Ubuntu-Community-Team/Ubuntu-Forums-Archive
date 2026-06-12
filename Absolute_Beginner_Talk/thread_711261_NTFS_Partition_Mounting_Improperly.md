---
title: "NTFS Partition Mounting Improperly"
date: 2008-02-29
forum: Absolute Beginner Talk
---

### Post by vergeh on 2008-02-29
I'm a complete dunce when it comes to things like this. I have Ubuntu dual-booted on my laptop, and there's an NTFS partition that is attached to it. Under Gutsy, the drive usually mounts on boot. However, about 1 in 5 bootups, it doesn't mount the drive. Is there a quick way to reattempt or force the drive mounting?

---

### Post by jan quark on 2008-02-29
it is unusual that the drive is not mounted occasionally

please post the output from

```
cat /etc/fstab
```
```

sudo fdisk -l
```


you can mount all drives listed in fstab with
```

sudo mount -a
```

---

### Post by forrestcupp on 2008-02-29
Usually when it can't mount an NTFS drive, it means that you didn't shut down Windows properly.  For some reason when Windows doesn't shut down right, it locks the drive.  So try booting back to Windows and shut it back down making sure that it completely shuts down.  Then it should show up in Ubuntu.

---

### Post by samitharansara on 2008-03-03
sudo mount -a   Must work.......!!

---

