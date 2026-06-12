---
title: "Grub Cannot Install on EXT3 Ubuntu 7.10"
date: 2008-01-15
forum: Absolute Beginner Talk
---

### Post by bme on 2008-01-15
I am not new to Ubuntu since I have been using it on my dell laptop since LTS. For some reason,I decided to reinstall 7.10. 
Now I cannot install when the partition is ext3-grub cannot install giving the "fatal error" message. I tried manually using grub-install and inside grub(root, setup) and it complains that the partition cannot be accessed.
So I googled about the problem and found several replies suggesting using ext2 format. I've done that and the install went smoothly.
So what is the problem with ubuntu ext3 install?

---

### Post by njparton on 2008-01-16
Did you delete the old partitions in the partitioner that comes with the installer first?

---

### Post by bme on 2008-01-17
no I did not delete any partition.....
as I mentioned I used ubuntu before and had to do some "housekeeping" so I reinstalled ubuntu on the partition where it was installed before.I also formatted that partition as ext3. that is when the grub refused to install.
when I googled (under XP) there were several forum replies(in another forum,not here in ubuntu) that suggested ext2instead and that is what I did. grub installed and the ubuntu installation proceeded well.there was also no problem converting ext2 to ext3 once the installation was up and running.
anyway I do not want to go trough another reinstall.I just thought to post this experience to see if anyone else had this problem.....

---

### Post by dstew on 2008-01-17
There have been several posts about this problem. I could not find this bug clearly defined on the Ubuntu bugs site. I recommend that you submit this as an Ubuntu grub bug to [https://bugs.launchpad.net/ubuntu/+source/grub](https://bugs.launchpad.net/ubuntu/+source/grub). It seems to be specific to Dell laptops.

---

