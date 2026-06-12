---
title: "If I install ubuntu on my second hard drive"
date: 2007-01-19
forum: Absolute Beginner Talk
---

### Post by GI_Josh on 2007-01-19
If I install ubuntu on my second hard drive, and let ubuntu have the entire disk, and let windows have my entire first disk, and then somewhere down the road I decide that I no longer want ubuntu, what would I do?  I think I can hand the bootloader issues I would have (or at least I could find that info) but would windows be able to "see" my second drive so that I could reformat it if it's in ext3?

---

### Post by taurus on 2007-01-19
You can install f3-driver in Windows so that it would see your ext2/ext3 (Ubuntu).

[http://www.fs-driver.org](http://www.fs-driver.org)

---

### Post by Sefrin on 2007-01-19
You could fix the bootloader with your Windows install disc, probably using FIXMBR from the recovery console.

As far as reformating your second hard drive you could use a bootable partition program or try disc management from inside Windows.  You can do a lot of things while Windows is loaded with drives that aren't "system".

---

