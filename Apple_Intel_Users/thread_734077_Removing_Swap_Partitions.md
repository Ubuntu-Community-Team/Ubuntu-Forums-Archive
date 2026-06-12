---
title: "Removing Swap Partitions"
date: 2008-03-24
forum: Apple Intel Users
---

### Post by dellegazze on 2008-03-24
I'm dual-booting Mac OS X and Ubuntu Gutsy on Santa Rosa macbook.

I want to completely uninstall ubuntu and reinstall it afterwards. I tried this before, but i accidentally left the swap partition there, so i now have two swap partitions. I want to delete both of these, along with the main partition.

 The best way i can think of doing this is going on the ubuntu live CD (Gutsy), opening GParted, and deleting all three of the partitions there. Problem is, there's a lock next to the two swap partitions and i can't modify them.

How do i bypass this? And, if i can't, how can i delete them otherwise?

---

### Post by prshah on 2008-03-24
> **dellegazze said:**
> 
 The best way i can think of doing this is going on the ubuntu live CD (Gutsy), opening GParted, and deleting all three of the partitions there. Problem is, there's a lock next to the two swap partitions and i can't modify them.

How do i bypass this? And, if i can't, how can i delete them otherwise?

Yes the live CD is your best bet if you also want to delete your main partition. If you want to delete JUST your swap partitions, give the command ```
sudo swapoff -a
``` then delete them and recreate them.

The above command will also disable swap when you have booted from the live CD (which is why there is a "lock"). Or, in gparted, you can just right-click it and choose "swapoff"

---

### Post by dellegazze on 2008-03-24
wow, i wasn't expecting an answer so quickly, thanks.

 thanks so much, it works.

argh unfortunately, GRUB seems to be still installed in those partitions. How do i uninstall it?

---

