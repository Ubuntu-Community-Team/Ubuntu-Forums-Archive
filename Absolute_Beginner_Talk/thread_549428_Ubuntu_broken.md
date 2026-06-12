---
title: "Ubuntu broken"
date: 2007-09-12
forum: Absolute Beginner Talk
---

### Post by waste301 on 2007-09-12
Windows is running fine, but when I try to run the ubuntu installation disk this is what I get

BusyBox v1.1.3 (Debian 1|1.1.3-3ubuntu3) Built in shell (ash)
Enter 'help' for a list of built in commands.

/bin/sh: can't access tty; job control turned off
(initramfss) [ 33.434886] ata1.00: failed to set xfernode (err_mask=0x40)

*(repeats attempts with different numbers)* ata2.00...err_mask=0x4


when I type I get double letters "help" becomes "hheellpp"

I burned a brand new installation CD and it still does this.

In windows there is a 20 GB partition listed as unallocated space. I can't figure out how to install or uninstall umbutu on this partition, or why this is happening.

Ubuntu was loading fine for a few hours, and then this started happeneing.  I had to uninstall GRUB to get windows back, and would like to do a fresh install of ubuntu if possible.

Every once in a while the CD will boot correctly, but it takes FOREVER.

Thanks to anyone who can help.

---

### Post by waste301 on 2007-09-12
bump - help please!

---

### Post by CaptainInsaneO on 2007-09-12
You should check the image itself to make sure it's not corrupt. The checksum might be bad. Use this link for more info: [http://losrivas21.blogspot.com/2006/04/how-to-verify-md5-checksum-of-ubuntu.html](http://losrivas21.blogspot.com/2006/04/how-to-verify-md5-checksum-of-ubuntu.html)

---

### Post by jamvegan on 2007-09-12
I've read several posts in which people who had the same problem you're having with the Live CD were able to install without a problem using the alternate install CD (there's a box to check under the "Start Download" button on the [download page]("http://www.ubuntu.com/getubuntu/download")).

Good luck!

---

### Post by cubeist on 2007-09-12
Also, try re-burning the cd at a much lower burn speed... some people have reported problems with live iso cd's burnt at high speeds...

---

