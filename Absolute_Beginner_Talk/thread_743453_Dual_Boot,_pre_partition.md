---
title: "Dual Boot, pre partition"
date: 2008-04-02
forum: Absolute Beginner Talk
---

### Post by domifan28 on 2008-04-02
Okay, I have my harddrive pre partitioned. I have XP on 170mb of it, but I have another 60 for Ubuntu.

the 60 is formatted in ntfs, how do I install Ubuntu from the live cd onto that existing partition?

thanks.

---

### Post by meborc on 2008-04-02
during the install you will be able to reformat that partition into linux filesystem (ntfs will not do)... just choose MANUAL partitioning, NOT the full drive install during the installation process

a guide can be found here - [http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

---

### Post by domifan28 on 2008-04-02
oh great, what is a good size for the swap file (what is that), and what format does the remaining have to be in? the tut says ext3(don't know what that is) so is that what i put it in?

Sorry I'm a super newbie at Linux.

---

### Post by mikewhatever on 2008-04-02
> **domifan28 said:**
> oh great, what is a good size for the swap file (what is that), and what format does the remaining have to be in? the tut says ext3(don't know what that is) so is that what i put it in?

Sorry I'm a super newbie at Linux.

Yes, ext3 is the format. The swap is similar to Windows page file in concept and should be about 1.5 the size of RAM or 1-2 GB.

---

### Post by domifan28 on 2008-04-02
Ok, well i tried that and i changed the partition to ext3 but when I go to proceed in the installation i get an error message.

---

### Post by louieb on 2008-04-02
What phase of the install gave you the error message?
What is the error message?

---

### Post by domifan28 on 2008-04-03
Its right after i select manual>select the partition and format it to EXT3 and then i click continue and I get a message something about the root something being unreachable.

---

### Post by louieb on 2008-04-03
Probably **no root files system defined**. You need to select the partition you want to install Ubuntu on. I think it right click and select edit. Then choose its **mount point to be /** (root). That should tell the installer what it need to know in order to continue.

---

### Post by bumanie on 2008-04-03
You need to designate the partition as / (at the bottom of the menu and all you have to type is /)
A good way to set up ubuntu is to have a / partition of 6-8g. As already stated a 1-2gig swap. These two partitions are mandatory. It is a good idea to set up the remaining hard drive space with a separate partition designated /home. By making a separate /home, if something goes wrong with your installation, you only have to reinstall to / and all your saved data in /home will be safe.

---

