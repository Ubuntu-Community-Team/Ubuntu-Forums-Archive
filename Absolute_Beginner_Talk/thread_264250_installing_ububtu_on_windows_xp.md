---
title: "installing ububtu on windows xp"
date: 2006-09-24
forum: Absolute Beginner Talk
---

### Post by maneesh77 on 2006-09-24
Already backed up all my docs. Want to install ubuntu on my labtop but also want current windows XP to stay there too. Also to create an option for booting ubuntu or xp at start up

How do I do it, i have the ubuntu CD. Please guide me step by step ( i suck at computers)

---

### Post by bulldog on 2006-09-24
Okay step by step.

First you need to have room for Ubuntu on your hdd.
You can do this in XP with disk-management.
Make at least 15 tot 20GB of free space to use Ubuntu.
Let the space unallocated in other words do not format

Put in the ubuntu cd and boot from it,if it's the live cd you can take the first option to boot it up.

If things go well you end up with the ubuntu desktop.
Here you see the install button.

Hit it and there are some questions asked which you should answer.

When coming to partitioning you can choose three options,if you're confident enough,take manually,if not let ubuntu use the largest amount of free space [your unallocated non formatted] take alook if it's okay and hit install.

After the install which take about 20-30 minutes you have to reboot without the cd.
You should see a menu called GRUB where you can choose to boot either windows or ubuntu.

Make your choice and your done.

---

### Post by slibuntu on 2006-09-24
Try the guide on my blog, i did the exact same thing

---

### Post by petri on 2006-09-24
Step by step (Donkey can :D )

Step 1. DEFRAGMENT your harddisk in windows. (You never have to do it in Linux) If you don't you might get your windonwsfiles under the new partition and blame it on Ubuntu.

Step 2. [http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

Just two steps! \\:D/

---

### Post by rdilliker on 2006-09-24
> **petri said:**
> Step by step (Donkey can :D )

Step 1. DEFRAGMENT your harddisk in windows. (You never have to do it in Linux) If you don't you might get your windonwsfiles under the new partition and blame it on Ubuntu.

Step 2. [http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

Just two steps! \\:D/

Just curious, how would you get windows files under the new partition? Wouldn't Ubuntu not allow you to create a partition that overlaps the windows partition without resizing the windows partition first?

---

### Post by petri on 2006-09-24
You can minimize windows partition smaller than it needs space. But I didn't meant it like that. I mean that windows spreads your files all over the harddisk and when you delete some files there is free space to pack the data more efficient. Depending on how much space you have on your harddisk there might be a danger overwriting some filefragments when you resize the partition (make it smaller to make room for another OS). It might be a program, your data but unlikely a windows files.

Defragmenting is something everyone should do regular basis or have an program scheduled on it but still defragment the harddisk before installing an new program on it. Everyone is not doing that.

In Linux you don't have to worry about fragments because it's moste of it's filesystems (several latest) take care of it by themselves in other words they don't get fragmented. Exactly how they do it, I don't know.

---

