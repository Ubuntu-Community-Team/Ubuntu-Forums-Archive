---
title: "virtual machines and defrags"
date: 2007-06-24
forum: Absolute Beginner Talk
---

### Post by maddot on 2007-06-24
Ah, another one of my virtual machines question (yes i do ask alot about erm.) Anyway, i was wondering, would i have to defrag my windows Virtual machine on ubuntu? I mean i know by default windows dies if it isn't defragged... but this is a virtual macine...so... should effort be taken to actually carry it out... lol,,,, And how about  an alternate linux VM. does it need to be maintained as well?

Also, a side question, how do i get my windows virtualcube machine to see my LAN and it's files?

---

### Post by steve.horsley on 2007-06-24
I believe you should defrag the windows inside the VM, because there is a disk image in the VM that windows can fragment just as thoroughly as it would fragment a real disk.

With Linux in a VM, defragging is not needed, as it isn't with real Linux. But since the disk image is in a file on the host os, if it's a windows host you will of course need to defrag windows as usual.

As for networking from inside a VM, I think it depends on the VM you use. Maybe check the VM makers documentation.

---

