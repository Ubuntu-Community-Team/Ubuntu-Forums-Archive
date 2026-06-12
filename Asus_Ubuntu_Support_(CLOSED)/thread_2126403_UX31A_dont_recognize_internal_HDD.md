---
title: "UX31A dont recognize internal HDD"
date: 2013-03-17
forum: Asus Ubuntu Support (CLOSED)
---

### Post by kcho on 2013-03-17
Hi! I've got a strange problem. My notebook doesnt show the internal HDD in the boot options, but internal disk appears in SATA configuration.
I think it is due I erased all extra partitions (windows and recovery) and keep only linux partitions (Mint in this case, one for /, one for swap and one for /home).
Any ideas?

Thank You!

---

### Post by kcho on 2013-03-17
Well, I solved it.
Thanks god I've got two zenbooks. So, I created a new first FAT32 partition with boot flag enabled. Then I copied the content of the first partition on the second notebook ... and voilà ... it works :D
This partition had been written by boot-repair app in order to boot linux and win8. It contents an efi directory with a lot of files.
It seems like the bios doesn't show the disk in the boot options if it doesn't contain this partition.

---

