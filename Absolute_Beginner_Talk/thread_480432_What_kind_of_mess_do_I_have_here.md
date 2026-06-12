---
title: "What kind of mess do I have here?"
date: 2007-06-21
forum: Absolute Beginner Talk
---

### Post by captgadget on 2007-06-21
Someone suggest I create a boot partition to solve my grub error 18 problems. As you can see I got that done, but now I'm apparently running my system on a partition that is only 3.07 GB and I have an unused partition of 66.73 GB. Now, is there  a way for me to resize something here without have to reinstall the OS?

---

### Post by diatribe on 2007-06-21
You installed your / partition on the one you had reserved for boot.  Short of booting from a livecd and just resizing your present partition, there is no way for you to fix this without formatting.  And if you resize this parition, you will not have a seperate boot parition either.

---

### Post by phr0ze on 2007-06-21
But if your problems have cleared up, you can just increase the size of the partition.

---

### Post by LaRoza on 2007-06-21
Expand the partition to free the empty space, using GParted. I recommend the live cd, see my sig. If you have booting problems, try using the Super Grub Disk, also in my sig.

---

### Post by captgadget on 2007-06-21
I got the iso downloaded. Now how to I turn that into a cd in Linux?

---

