---
title: "[SOLVED] Problems with a U3 USB Memory stick"
date: 2007-09-20
forum: Absolute Beginner Talk
---

### Post by MikeSz on 2007-09-20
Having done a search of previous threads, looks like I could use some help with this...

I have a 1GB U3 memory stick that I have been using fine for a couple of months now.  It did come with some proprietary software but as it was tiny, and kept coming back whenever it was deleted anyway, I just left it.  

Unfortunately however, I now have no capacity left on the drive.  The U3 software is now showing as being 900Kb in size!!!  The drive is also showing as locked and wont let me delete anything...

Help...I have a 1GB drive and I can only use 8kb of it! :)

*SOLVED*

---

### Post by ddrichardson on 2007-09-20
U3 should be banned. It's basically formatted in such a way as to appear as ISO9660 (hence the read only problem) and a FAT32 partition. You can remove the software but its a bit of a hassle and AFAIK needs to be done from Windows.

The damn things don't even work with Vista without an upgrade, and are a security nightmare in the workplace. Anyway if you have access to Windows then the removal tool is [here]("http://www.u3.com/uninstall/").

---

### Post by MikeSz on 2007-09-20
Thanks - il have a go from a windows comp.  Wonder why it just started doing it then?  Ive managed to use it in Ubuntu for the last couple of months without any bother (although I never have been able to remove that u3 software)

---

### Post by MikeSz on 2007-09-20
Cheers - that fix worked a treat!

---

