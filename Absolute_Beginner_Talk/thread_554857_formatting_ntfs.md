---
title: "formatting ntfs"
date: 2007-09-19
forum: Absolute Beginner Talk
---

### Post by gupta_sumesh63 on 2007-09-19
Hi,
I have Ubuntu with XP.
XP is behaving erratically. I want to format it and reload XP.
Is it possible through Ubuntu?
What will be the repercussions?
Thanks:confused:

---

### Post by notwen on 2007-09-19
I'd simply format the XP partition using GParted, then select the unallocated space to install to during your XP installation.  You may want to back up any of your data from the XP partition before formatting it too.  You could use the GParted LiveCD to do this, making sure that your XP partition was not mounted, or simply be sure to unmount it if you want to format the XP partition while working in your regular Ubuntu session.  Hope this helps. =]

---

### Post by the_nite_owl on 2007-09-19
Not an answer to your question but something you might want to consider.

I had setup my machine as a dual boot XP/Ubuntu box also.
Now that I have Ubuntu working the way I want it (almost anyway) and know enough about it I rarely ever boot back to XP.
So recently I installed VirtualBox and created a virtual system to run XP under.  A quick install of XP inside the virtual and I now have the ability run XP from inside of Ubuntu rather than rebooting to get to it.

There are considerations to be had for running in a virtual as opposed to a full blown install but it is worth looking into.

---

### Post by mysticmatrix on 2007-09-19
> **gupta_sumesh63 said:**
> Hi,
I have Ubuntu with XP.
XP is behaving erratically. I want to format it and reload XP.
Is it possible through Ubuntu?
What will be the repercussions?
Thanks:confused:
Well simply use the Windows CD and reinstall after formatting required partition.
Now, you'll boot directly to Windows. Don't Panic.
Simply use [Super-Grub CD]("http://supergrub.forjamari.linex.org/") and that would solve the boot order problem.

---

