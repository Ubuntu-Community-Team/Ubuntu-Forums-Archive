---
title: "No &quot;Windows&quot; in GRUB"
date: 2007-04-11
forum: Absolute Beginner Talk
---

### Post by mindtrick on 2007-04-11
Just installed Ubuntu. I still have my Windows partition (hda5). And I can mount it and transfer the files to my Linux partitions. But I don't have an option to boot from that partition in GRUB. How can I fix it and boot from Windows again?

---

### Post by dstew on 2007-04-11
I do not think that Windows can boot from a logical partition. I think it has to be on a primary partition. I might be wrong.

If you can boot Windows from a logical partition like hda5, you need to add the correct menu item to your /boot/grub/menu.lst file. See [http://ubuntuforums.org/showthread.php?t=394967](http://ubuntuforums.org/showthread.php?t=394967)

---

