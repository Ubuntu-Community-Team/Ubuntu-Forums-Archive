---
title: "is it alright to partition your drive while its in use?"
date: 2006-06-22
forum: Absolute Beginner Talk
---

### Post by user1397 on 2006-06-22
is it okay to partition my hard drive, even though at least one partition is mounted?  when i tried to, it gave me a warning that the kernel could get messed up (i dont remember the exact message) or is it better just to always use live cd's to partition hard drives?

---

### Post by aysiu on 2006-06-22
[QUOTE=erik1397]is it okay to partition my hard drive, even though at least one partition is mounted?  when i tried to, it gave me a warning that the kernel could get messed up (i dont remember the exact message) or is it better just to always use live cd's to partition hard drives?[/QUOTE]
You can't partition a drive that is mounted.

You can resize or delete a partition that is unmounted if you're resizing from a partition that's in use, though.

For example, from /dev/hda5 (your Ubuntu installation), you could unmount and repartition /dev/hda1.

---

### Post by user1397 on 2006-06-22
[quote=aysiu]You can't partition a drive that is mounted.

You can resize or delete a partition that is unmounted if you're resizing from a partition that's in use, though.

For example, from /dev/hda5 (your Ubuntu installation), you could unmount and repartition /dev/hda1.[/quote]so that kernel warning is not a worry?

---

### Post by az on 2006-06-22
I don't think you can partition a drive with a mounted partition on it.

---

### Post by user1397 on 2006-06-22
[quote=azz]I don't think you can partition a drive with a mounted partition on it.[/quote]well the thing is, i **have **already done it, i was just worried about that kernel error.  see, i was in dapper, but i wanted to resize my fedora core 5 partition while in dapper, but both OS's are on the same drive.  but it worked nonetheless.

---

### Post by underdog on 2006-06-22
Well its good that it worked, but using something like GParted liveCD is pretty much foolproof for common uses, and a not-very-big download, for future reference.

---

### Post by steve.horsley on 2006-06-22
You can partition the drive while some partitions are mounted but you need to be aware of potential confusion to the kernel. It's definitely safer to use a live CD. 

Remember that if you split/join partitions, all the later ones change name which will possibly leave /etc/fstab and /boot/grub/menu.lst using the wrong names.

---

### Post by user1397 on 2006-06-22
[quote=steve.horsley]You can partition the drive while some partitions are mounted but you need to be aware of potential confusion to the kernel. It's definitely safer to use a live CD. 

Remember that if you split/join partitions, all the later ones change name which will possibly leave /etc/fstab and /boot/grub/menu.lst using the wrong names.[/quote]okay thanks for that info, it has helped me quite a bit

---

### Post by steve.horsley on 2006-06-22
As an afterthought, GRUB gets installed with knowlege of where to find menu.lst embedded somewhere within itself. If the partitions all shuffle up/down by name, GRUB might not even be able to find menu.lst, in which case the fact that the names in menu.lst are now wrong is moot.

---

