---
title: "[SOLVED] How can I chek bad sectors and volumes integrity from terminal?"
date: 2008-02-11
forum: Absolute Beginner Talk
---

### Post by Kosimo on 2008-02-11
How can I scan a volume to check integrity from terminal?  

Can I do some kind of bad sector search like scandisk does in windows?

Thank you!

---

### Post by jordanmthomas on 2008-02-11
You can use badblocks.
```
sudo badblocks /dev/sdb
``` for example
I'm not sure if you should run it on a mounted drive though.  If you're checking the drive with your root partition, you'd probably want to grab a LiveCD to do it.

---

### Post by Rocket2DMn on 2008-02-11
The program fsck is what you're looking for.
```
sudo fsck /dev/*yourpartition*
```
The partition probably has to be unmounted.

---

### Post by Kosimo on 2008-02-11
> **Rocket2DMn said:**
> The program fsck is what you're looking for.
```
sudo fsck /dev/*yourpartition*
```
The partition probably has to be unmounted.

Thank you for that super quick answers! ;)

fsck also search for bad sectors?

as said, do I have to unmount my partitions first?

---

### Post by Kosimo on 2008-02-11
> **jordanmthomas said:**
> You can use badblocks.
```
sudo badblocks /dev/sdb
``` for example
I'm not sure if you should run it on a mounted drive though.  If you're checking the drive with your root partition, you'd probably want to grab a LiveCD to do it.

Ok, in this case

fsck for integrity and badblocks for bad sectors.  Is that correct?

---

### Post by jordanmthomas on 2008-02-11
badblocks finds problems with the hardware itself (used it to diagnose a failing external hard drive and it found many), and fsck finds problems with the filesystem.

badblocks doesn't check for bad sectors, but bad blocks, which is a little different.  Honestly, to tell you the exact difference I'd have to look it up, so I'll leave it to you to do that.

---

### Post by Kosimo on 2008-02-11
> **jordanmthomas said:**
> badblocks finds problems with the hardware itself (used it to diagnose a failing external hard drive and it found many), and fsck finds problems with the filesystem.

badblocks doesn't check for bad sectors, but bad blocks, which is a little different.  Honestly, to tell you the exact difference I'd have to look it up, so I'll leave it to you to do that.

Clear now.
Thank you

---

### Post by Tatty on 2008-02-11
easiest way is:

**EDIT:**  I suddenly realised the command i suggested to use here was incorrect, so i am editing this now with the corerct code:

```
cd /
touch /forcefsck
```

---

