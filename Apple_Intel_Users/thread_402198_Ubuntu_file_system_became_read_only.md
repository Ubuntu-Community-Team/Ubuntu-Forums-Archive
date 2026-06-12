---
title: "Ubuntu file system became read only"
date: 2007-04-05
forum: Apple Intel Users
---

### Post by anthemius on 2007-04-05
Suddenly I wake up in the morning and my ubuntu's gnome won't start.
i've tried to edit the "xorg.conf" and guess what was the resolution.

I was unable to to save my changes because my file "is read-only"

More painfully, all me file system had became read-only.

I think that I haven't done something special to expect this behavior.

Any suggestion?

Thanks!

---

### Post by mking213 on 2007-04-05
Since no one else has givin it a shot, i guss i will. Thats normal behievior for a machine that needs to be either rebooted into single mode and FSCKed or booted from cdrom and have all partitions fscked. When they're marked clean, you'll then be able to reboot and your disk will remount read write.

Mike
:guitar:

---

### Post by anthemius on 2007-04-07
Unfortunately the solution you suggest does not seem to work?
Another suggestion.

Is there a need to use fsck command with some options, like -c -v -f ?

---

