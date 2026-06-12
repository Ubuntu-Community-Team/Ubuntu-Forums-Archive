---
title: "How to add Ubuntu after you install Windows by using the bootcamp partioning system?"
date: 2007-04-03
forum: Apple Intel Users
---

### Post by orlandopozo on 2007-04-03
Hello Folks,

I already installed Mac OS X and Windows XP SP2 by using the bootcamp partitioning system on my Imac, I am here:

1) Installed Mac OS X (250 GB HDD) (GTP based partition with HFS using the boot.efi booloader)
2) By using the bootcamp partitioning software, this resized the Mac OS X partition to 200 GB in order to get 50 GB of free space and it mounted the Windows XP SP2 partition there (MBR based partition with NTFS using the NTLDR booloader).

The STEP 3 would be adding Ubuntu Dapper or Ubuntu Edgy to the group, therefore I need to resize again the Mac OS X GPT based partition (200 GB HDD) to 170 GB and give Ubuntu Dapper or Ubuntu Edgy 30 GB (MBR based partition with ext3 using the LILO bootloader).

Since I begun with the bootcamp partitioning system (If I would begin partioning the HDD by using diskutil command like all the guides say (eg: wiki.onmac.net/index.php/Triple_Boot_via_BootCamp) , it would be easier), I don't know exactly how to do STEP3.

Any ideas?

---

### Post by Chrisj303 on 2007-04-04
If your doing a triple boot, then you don't partition with bootcamp - you use diskutility to split your hardrive into 3.

---

