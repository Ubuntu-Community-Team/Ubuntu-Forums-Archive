---
title: "Uninstall question: How do I do it?"
date: 2007-09-16
forum: Absolute Beginner Talk
---

### Post by mshadow818@msn.com on 2007-09-16
I think this is a better forum to post in than where I originally posted:

Before I knew what I was doing I installed Ubuntu Studio and before that Puppy Linux. I now want to wipe both from my system and start fresh correctly.
I cannot seem to find info on how to uninstall Ubuntu and wipe the files / partitions created by them without affecting Windows XP on the same hard drive.

Also, how can I tell if there are any Puppy Linux files/partitions hanging around?
Is there any way to reset the hard drive back to the way it was before I installed linux?

---

### Post by mocoloco on 2007-09-16
There is no "uninstall OS" option, just reformat the partitions and they're gone.  It sounds like you're planning to re-install, when you do just select to manually choose partitions, and mark the options to reformat them (not your XP partition of course).

---

### Post by Hospadar on 2007-09-16
In the partitioner, you'll want to manually edit your partitions, delete all of the non-windows partitions, and then install ubuntu into the free space that's leftover.  (you'll need to manually create the swap and ext3 partition)

---

### Post by mikewhatever on 2007-09-16
> Before I knew what I was doing I installed Ubuntu Studio and before that Puppy Linux.
Sounds crazy. Think twice next time. You can run both Puppy and Ubuntu from their CDs, so what was the rush?

> I cannot seem to find info on how to uninstall Ubuntu and wipe the files / partitions created by them without affecting Windows XP on the same hard drive.
There is no such option. You can't just click a button to uninstall an operating system. Please review this page carefully if you want Windows to work. [http://www.users.bigpond.net.au/hermanzone/p18.htm](http://www.users.bigpond.net.au/hermanzone/p18.htm)

> Also, how can I tell if there are any Puppy Linux files/partitions hanging around?
Check your partition table.

> Is there any way to reset the hard drive back to the way it was before I installed linux?
No, at least nothing automated.

---

### Post by mshadow818@msn.com on 2007-09-16
> **mikewhatever said:**
> Sounds crazy. Think twice next time. You can run both Puppy and Ubuntu from their CDs, so what was the rush?

Check your partition table.

My rush was a mixture of being an idiot and getting some bad recomendations and instructions from another idiot.  

One more dumb question, where can I find the partition table?  I see no other logic drives in the My Computer section of Windows.  
I realize this probably reveals much of my ignorance.

---

### Post by oilchangeguy on 2007-09-16
> **mshadow818@msn.com said:**
> My rush was a mixture of being an idiot and getting some bad recomendations and instructions from another idiot.  

One more dumb question, where can I find the partition table?  I see no other logic drives in the My Computer section of Windows.  
I realize this probably reveals much of my ignorance.

from gparted, in the live cd.

one other thing, unless you enjoy spam. i'd use something else for my user id.

---

### Post by mikewhatever on 2007-09-16
Gparted is a program on the live CD under System>Administration>Gnome Partition Editor. with its help, you can both see and edit partition. The partition with Windows usually has NTFS file system, and those with Linux on, ext3. There should also be swap partition. What you need to do is, fix the MBR to be able to boot Windows, and then delete all ext3 and swap partitions using Gparted.
You can not see Linux partitions from Windows, because it has no support for ext3 filesystem. The partitions are seen as unknown in the disk management window.

---

