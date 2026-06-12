---
title: "Can't boot computer after formatting new partition"
date: 2007-02-14
forum: Absolute Beginner Talk
---

### Post by RBird on 2007-02-14
I just did something without understanding it first and messed up the Ubuntu installation on my laptop. I am hoping that this is something that can be fixed.

I had my laptop up and running well on Ubuntu when I noticed a message that said I was low on disk space. That seemed unlikely since this is an 80GB hard drive. I checked the disk  realized that there were three small partitions (the largest being 3GB). The rest of the drive was unformatted. I thought I had taken care of that when I installed Ubuntu on this machine.

I decided to format the rest of the drive so I could access the space. Unfortunately I did something wrong and now I cannot boot the computer. Before the system locked up I noticed that none of the menus worked. It looks like formatting the rest of the drive changed all the "pointers" (not sure of the right word) in the menus. Now they are looking for programs in /home. [I think the newly formatted partition was named /home - this was the default setting so I did not change it.]

I can boot from the Ubuntu live CD, and I can see the partitions on the hard drive. But the partitions will not mount so I cannot see what is on them or copy any files.

Did I mess this up beyond repair? If not, how would I fix this problem?

---

### Post by Sanus Compleo on 2007-02-14
Did you try reinstalling ubuntu?

---

### Post by housam on 2007-02-14
Format your entire HDD ,then do the partitioning manually to get the suitable size of each partition i.e.
- 10 Gb for the root ( / ) ext3 format.
- 1 Gb for the swap - swap format.
- the rest for the /home ext3 format .
and afterward go for the new installation.

---

### Post by DerHesse on 2007-02-14
Can you post your fstab?

---

### Post by drivel on 2007-02-14
Maybe reinstall Grub is a good way.

---

