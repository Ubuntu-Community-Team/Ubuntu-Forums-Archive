---
title: "Just Installed"
date: 2008-02-26
forum: Absolute Beginner Talk
---

### Post by AlexOliver on 2008-02-26
I just installed Ubuntu and I am very impressed. Before I removed XP I backed up all of my MP3s onto an external hard drive. When I plug the hard drive in, Ubuntu come up with an error and I cannot get the files from this drive. Can anyone please help?
Thanks,
Alex

---

### Post by Joeb454 on 2008-02-26
Sure, though could you post the exact error that Ubuntu gives when you plug the drive in :)

---

### Post by sayakb on 2008-02-26
Could be due to an improper eject under Windows.
Try this:

```
mount -t ntfs-3g /dev/sdb1 -o force
```

Replace sdb1 with your HDD's device name.

---

### Post by herbster on 2008-02-26
Er, before you try that above, post the error please.

---

