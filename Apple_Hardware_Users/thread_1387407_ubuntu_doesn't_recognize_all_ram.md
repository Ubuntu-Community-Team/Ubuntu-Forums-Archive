---
title: "ubuntu doesn't recognize all ram"
date: 2010-01-21
forum: Apple Hardware Users
---

### Post by ichigo on 2010-01-21
I have a macbook pro 5,5, which has 4GB of RAM. MacOS and the memcheck application listed in grub are able to identify this correctly. In karmic however, top (the CLI command) and the system monitor claim that ther are only 2.8GB... :(

Any ideas how to fix this or to find out what's happening? Any input appreciated...

Cheers!

---

### Post by pirateghost on 2010-01-21
> **ichigo said:**
> I have a macbook pro 5,5, which has 4GB of RAM. MacOS and the memcheck application listed in grub are able to identify this correctly. In karmic however, top (the CLI command) and the system monitor claim that ther are only 2.8GB... :(

Any ideas how to fix this or to find out what's happening? Any input appreciated...

Cheers!
i guess you are running 32bit.  that is a limitation of 32bit OSes

---

### Post by jflaker on 2010-01-21
32 bit operating systems can only address 3GB.  64 bit version is the one you want...warning though, there are less drivers available for 64 bit than 32....test thoroughly

---

### Post by ichigo on 2010-01-21
thx for your prompt answer!
i had forgotten about that... I guess I'll have to completely reinstall ubuntu in order to change to 64-bit. I think I'll do that when I upgrade to Lucid, since I need the computer now.

---

### Post by ichigo on 2010-02-05
Just in case somebody else has the same problem: If you have a 32-bit linux installed and don't want to switch to 64-bit, you may want to try the kernel with enabled pae. These have 32-bit and support up to 64GB RAM...

---

