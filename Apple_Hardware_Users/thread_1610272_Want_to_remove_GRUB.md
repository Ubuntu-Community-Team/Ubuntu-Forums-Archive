---
title: "Want to remove GRUB"
date: 2010-10-31
forum: Apple Hardware Users
---

### Post by jspitzer221 on 2010-10-31
I installed Ubuntu 10.10 on my macbook and downloaded the GRUB bootloader that came with it. I later installed rEFIt, and now I want to get rid of the GRUB as it is redundant. I'm new to all this, so any help would be greatly appreciated

---

### Post by ichigo on 2010-10-31
As far as I know, refit looks for grub to identify linux partitions. If you uninstall, refit probably won't recognize your ubuntu partition. Besides you may want to use the recovery mode at some point..
I'd suggest that you change the timeout in the configuration file instead. (See: e.g.: [http://grub.enbug.org/grub.cfg](http://grub.enbug.org/grub.cfg) )

---

