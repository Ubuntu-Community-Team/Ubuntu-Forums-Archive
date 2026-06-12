---
title: "install help"
date: 2005-06-05
forum: Absolute Beginner Talk
---

### Post by war-totem on 2005-06-05
ok, heres the problem.

this is a Compaq armada e500.

im attempting to install ubuntu on a laptop that allready has win2k.  sidenote-its important that i dont screw this pc up as it is a govt laptop on loan.

i did create a partition allready (ext2)  however it is unformated for now.  when ubuntu prompts me to configure my partition disks, this is what my settings show:

Usage method:  format the partition
File system:  no file system
Bootable flag:  off
Size:  11.2

when i hit finish partition changes this comes up
No root file system
No root file system is defined.
Please correct this from the partitioning menu.

logically my question is how do i define a root file system?

thanks in advance and sorry if this has been asked.  i searched but could not find anything.

---

### Post by poofyhairguy on 2005-06-06
[QUOTE=war-totem]ok, heres the problem.

this is a Compaq armada e500.

im attempting to install ubuntu on a laptop that allready has win2k.  sidenote-its important that i dont screw this pc up as it is a govt laptop on loan.

i did create a partition allready (ext2)  however it is unformated for now.  when ubuntu prompts me to configure my partition disks, this is what my settings show:

Usage method:  format the partition
File system:  no file system
Bootable flag:  off
Size:  11.2

when i hit finish partition changes this comes up
No root file system
No root file system is defined.
Please correct this from the partitioning menu.

logically my question is how do i define a root file system?

thanks in advance and sorry if this has been asked.  i searched but could not find anything.[/QUOTE]


Hit enter on the lin that says file system. It will change to /

Be sure to add a swap partition too...

---

### Post by heart_reaver on 2005-06-06
hello there

at the time of installation when it ask where to install u can first delete the partition and then let it auto configure for swap and "/" size form ur free space 
 
 :wink: 


heart_reaver

---

### Post by war-totem on 2005-06-06
thanks a lot guys its installed perfectly now.

however, the windows partition is acting oddly, taking a long time to load up programs and programs crash a lot more.

could this be a potential problem because of the dual install?

---

