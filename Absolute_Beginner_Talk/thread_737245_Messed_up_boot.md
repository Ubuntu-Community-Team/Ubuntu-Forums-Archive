---
title: "Messed up boot"
date: 2008-03-27
forum: Absolute Beginner Talk
---

### Post by communized on 2008-03-27
Well I'll give you a quick rundown

Windows was first installation
then ubuntu was installed
and finally xubuntu.


So I like xubuntu so I figure I'll blast the ubuntu partition, which seems like I did.

(There was an NTFS partition, then "partition 1 and partition 2" ) i think, not sure. So I blast the #1 and reboot.  problem booting the OS or finding OS I forget. So I put my XP CD back in and go to the other 2 small small partitions, so I blast at random ( I think it was the smallest one and ubuntu was smaller than xubuntu on first installation so it seemed like a good guess )


So now when I booted up the live CD I right away got that the drive couldn't be mounted and I guess that is meaning the windows drive, what do I do?

---

### Post by bumanie on 2008-03-27
As long as your windows install is still there (randomly nuking partitions is not a great idea), you will need to firstly reinstall the windows mbr. Do you have a windows disk and are you running vista or xp?

---

### Post by meindian523 on 2008-03-27
A careful read says that he has a Windows CD and is using XP.:lolflag:

---

### Post by bumanie on 2008-03-27
> **meindian523 said:**
> A careful read says that he has a Windows CD and is using XP.:lolflag:

Fair enough, but I'm at work and get distracted sometimes.

---

### Post by communized on 2008-03-27
Well, decided to just backup anything important and get rid of the swat partitions and the xubuntu partition and just install a new xubuntu. Thanks for the help.

---

### Post by hessiess on 2008-03-27
you can use the supagrubdisk to boot partitions on the drive. even if the instaled bootloader is broken

---

