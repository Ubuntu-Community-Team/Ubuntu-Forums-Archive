---
title: "[SOLVED] need to move ubuntu"
date: 2007-12-03
forum: Absolute Beginner Talk
---

### Post by stanton816 on 2007-12-03
hello,
i added ubuntu last week and after leaving the DVD in accidentally installed ubuntu twice. i'm not proud of myself.  anyway, i'm dual booting vista and ubuntu on one drive, but just added a second hard drive to my computer and would like to remove ubuntu from the drive it's sharing with windows and put  it on my empty drive.   
Can tell me how to remove the partition and ubuntu without wiping out Windows and then add it to the new hard drive.  ubuntu is currently sharing a 120 gig hard drive with vista and i want to move it to the other 100 gig hard drive. 
thanks as always. :guitar:I can't resist posting the guitar guy.

---

### Post by DGortze380 on 2007-12-03
I'm sure you can do it through windows too, but I've given up on vista at least until the next SP.. (in reality I think I'll skip Vista all together)... anyways...

boot from your live CD/DVD for Ubuntu. Open a terminal and run "Sudo gparted" . It will run in the GUI, just mark your ext3 partition and swap partition for removal and click apply. This will remove your current install of Ubuntu permanently.  Then double click install on the desktop and install on your new internal HDD.

Note: This will permanently remove any information saved on your current Ubuntu partition.

---

### Post by milton1 on 2007-12-03
You can do this without deleting/reinstalling your ubuntu system. Use the gparted liveCD to copy your ubuntu partitions to the new drive. Make sure the new drive has the "boot" flag. You will need to update, or possibly reinstall, grub. You can then delete ubuntu from the windows partition, and even stretch the windows partition to take up that space if you want.

---

### Post by stanton816 on 2007-12-04
well, i've had a long journey since yesterday, when I wiped out my entire computer.  I ended up borrowing a neighbor's fedora dvd (really didn't like fedora as much as ubuntu).  I backed up everything before I started messing with the partitioning, but i'm considering just letting microsoft go.  it would be nice to be able to work on statistical stuff at home, but i guess i'll just do it at work.  oh well.
thanks for everyone's advice.

---

