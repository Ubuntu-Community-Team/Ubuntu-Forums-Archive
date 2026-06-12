---
title: "I deleted /media :("
date: 2007-05-25
forum: Absolute Beginner Talk
---

### Post by the.dark.lord on 2007-05-25
I logged as root, and deleted /media from the filesystem by mistake. What should I do now? It's not in the trash.

---

### Post by compmodder26 on 2007-05-25
Have you tried remaking the directory (mkdir /media) ??  Do that, then remount everything (mount -a).

---

### Post by Sparkster185 on 2007-05-25
I'm not expert, but I would imagine as long as you didn't have anything mounted to the directory, no real harm was done.  Perhaps you can just re-create the directory as root?

---

### Post by rohan! on 2007-05-25
i don't know if you need to do any more than

```
sudo mkdir /media
```

in the command line.

---

### Post by thelinuxguy on 2007-05-25
I doubt /media contains any real data. It holds the mount points though.
Recreate /media.
Look in /etc/fstab and recreate the mount points under /media that appear in that file. I think that should do it.

---

### Post by the.dark.lord on 2007-05-25
Hey, you guys sure are fast. I re-created it. Thanks a lot :)

By the way, it doesn't have any data now. Is this normal?

---

### Post by compmodder26 on 2007-05-25
I just tested my method on my own machine.  Remounting everything automatically didn't work.  I had to manually mount everything that was in there, or a restart of the machine would do the trick as well.  I had to manually recreate the cdrom0 and floppy0 folders.  Inserting a flash drive would autocreate the necessary folder(s) for the drive.

---

