---
title: "Does GRUB not like Reiser?"
date: 2008-01-05
forum: Absolute Beginner Talk
---

### Post by eternicode on 2008-01-05
I decided to repartition my Kubuntu drive to have separate /boot and /home partitions.  I've read a little bit about how reiser4 is supposed to be the fastest filesystem, so I decide to try a reiser4 /boot partition.  GParted finishes fine, I get the files from my old /boot copied over to the new partition, modify my /etc/fstab as necessary.  Naturally, I have to update grub, so I enter a grub prompt:

```
grub> find /grub/stage1

Error: file not found
```

Not the exact wording, but that's how it went.  Grub couldn't find the files.  I could mount the partition, run ls, and see all the files, but grub couldn't.

Tried again with reiserfs (formatted, copied, unmounted, grub'd) with the same results.

Finally gave up and went with ext3, which works.

So, is reiser support not built into grub yet?  Is it planned?  The results of reiser4 weren't surprising, since it's so new, but I would've thought reiserfs would've been there for sure.

---

### Post by mattismyname on 2008-01-05
According to this thread, Grub can support reiserfs:

[http://www.linuxforums.org/forum/suse-linux-help/50024-can-grub-read-reiserfs-filesystems.html](http://www.linuxforums.org/forum/suse-linux-help/50024-can-grub-read-reiserfs-filesystems.html)

---

### Post by BOBSONATOR on 2008-01-06
it works fine on arch

---

### Post by Bachstelze on 2008-01-06
Grub support Reiserfs just fine. However, you have to mount your partition with notail for it to work.

---

