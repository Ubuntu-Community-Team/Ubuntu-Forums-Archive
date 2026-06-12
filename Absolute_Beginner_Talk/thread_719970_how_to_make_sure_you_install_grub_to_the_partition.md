---
title: "how to make sure you install grub to the partition you want"
date: 2008-03-09
forum: Absolute Beginner Talk
---

### Post by Rioku on 2008-03-09
There is probably a simple answer to this.. and I probably look like a huge nub asking it. I have Acronis OS selector installed and I have windows XP and windows Vista dual booting at the moment.

I want to make a 3rd boot with ubuntu but im afraid that the grub loader will ruin my entire laptop. How can I make sure and how do I installed the grub bootloader to the partition i want ubuntu on so that in acronis OS selector I can find that partition and label it ubuntu.

Then when I turn on my laptop I can choose either 1 of the 3 os's

Thanks guys

---

### Post by JoshuaRL on 2008-03-09
Well, GRUB might replace Acronis.  Could you give us a little more info about the program?  Is it run from Windows or from MBR?

I'm not sure what version you're using or what you paid, but their site says this costs $50 US.  GRUB does the same thing (without partition editing, for which there are great progams already) for free.  GRUB means "GRand Unified Bootloader".  It can load whatever OSs that you want.

---

### Post by louieb on 2008-03-09
Are you using the regular Live CD installer? If so just before the install begins you will see a button labeled **Advanced.  **Click on it and you specify where the GRUB IPL code goes. It defaults to the 1st hard drives MBR.  You can override the default and place it in the boot sector of your Linux / (root) partition.

---

