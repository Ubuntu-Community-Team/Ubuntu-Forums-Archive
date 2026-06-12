---
title: "Can I mount Windows HD with GUI?"
date: 2006-03-23
forum: Absolute Beginner Talk
---

### Post by confused57 on 2006-03-23
I have 2 hd's, the master being Ubuntu Breezy(1 large partition) and the slave drive is WindowsXP(again, 1 large partition).  I found my Windows drive listed in Ubuntu under System-Administration-Devices as /dev/hdb1, which shows the drive as inacessible.  There is an "Enable" button just to the right of the inaccessible and I was wondering if this is a GUI way of mounting the Windows ntfs drive that would enable me to read it rather than going through the terminal for mounting.

---

### Post by aysiu on 2006-03-23
I haven't known GUI mounting with Windows in Ubuntu to work with the correct permissions (read-only for NTFS, read/write for FAT32), but you're welcome to try it.

If you're utterly dependent on GUI mounting, I'd recommend using Mepis or Knoppix (on which Mepis is based).

Otherwise, using the command-line is usually just copying and pasting some commands:

[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

