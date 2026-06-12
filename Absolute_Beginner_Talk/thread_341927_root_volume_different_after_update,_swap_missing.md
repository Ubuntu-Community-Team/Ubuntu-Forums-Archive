---
title: "root volume different after update, swap missing"
date: 2007-01-19
forum: Absolute Beginner Talk
---

### Post by je1117 on 2007-01-19
For some reason, after updating my amd64 dapper machine, when I went to my "computer," it listed things differently.

Before, it listed my CD/DVD-RW cdrom, my "Root Volume" which I could see how big it was underneath the icon, and my swap volume.

Now, it lists my CD/DVD-RW, my "Root Volume" has been changed to "Filesystem" (no size specs.) and my swap is just gone completely.

What should I do?

---

### Post by jd65pl on 2007-01-19
Can you do the command below in the terminal. It will put a document called diskSpace.txt in your home folder please post this file.

```
df -h > ~/diskSpace.txt
```

---

### Post by mcduck on 2007-01-19
> **je1117 said:**
> For some reason, after updating my amd64 dapper machine, when I went to my "computer," it listed things differently.

Before, it listed my CD/DVD-RW cdrom, my "Root Volume" which I could see how big it was underneath the icon, and my swap volume.

Now, it lists my CD/DVD-RW, my "Root Volume" has been changed to "Filesystem" (no size specs.) and my swap is just gone completely.

What should I do?

That's how they should be displayed. I have no idea why your swap showed there before, it shouldn't :D

Anyway, it seems that you had a problem before and now it fixed itself. Don't worry about it, just be happy that everything is fine now (even though you didn't know that something was wrong before).

---

### Post by je1117 on 2007-01-19
here's the diskspace.txt, jd65pl.

Filesystem            Size  Used Avail Use% Mounted on
/dev/hda1              36G  2.5G   32G   8% /
varrun                503M   80K  503M   1% /var/run
varlock               503M  4.0K  503M   1% /var/lock
udev                  503M  100K  503M   1% /dev
devshm                503M     0  503M   0% /dev/shm
lrm                   503M   22M  482M   5% /lib/
modules/2.6.15-27-amd64-generic/volatile

How's it look?

---

