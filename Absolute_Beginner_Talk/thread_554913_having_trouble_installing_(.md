---
title: "having trouble installing :("
date: 2007-09-19
forum: Absolute Beginner Talk
---

### Post by Mosho on 2007-09-19
Hello people :)

I'm trying to install the OS, and when I get to the partitions menu, pick a partition to format as ext3, and click next it sends the following error; "No root file system is defined, please correct this from the partitioning menu" I have no Idea what the problem is, I've defined it as /boot and ext3, even deleted the partition and made a new one as ext3, still won't let me continue.

Thanks for any help :)

---

### Post by mattskr on 2007-09-19
The easiest way I found to install Ubuntu is to have unpartitioned (free space) available when you launch the installer. So if you want 40gb for Ubuntu, clear 40gb of space and leave it unpartitioned. Then tell Ubuntu to "Use the largest contiguous free space". This way the installer will take the free space and partition it automatically, including the swap.

---

### Post by tszanon on 2007-09-19
You need to assign a partition to **/** (also known as the root partition). So, modifying the partitioning scheme you posted, it should be:
partition 1: /boot
partition 2: swap (recommended)
partition 3: / (and, implicitly, everything else that does not have an assigned dedicated partition, like /var, /home, /usr...)

You must have at least one partition (for root). It's highly recommended that you have at least two partitions (root and swap). It's good to have a third partition for /home.

---

### Post by Mosho on 2007-09-19
Thanks alot, tsanzon, I tried doing that and it still gives me the error. 1 50GB /boot, 1 50GB /swap, and 1 45GB /home. 

will try doing it automatically...

Got it, thanks.

---

### Post by tszanon on 2007-09-19
> **Mosho said:**
> Thanks alot, tsanzon, I tried doing that and it still gives me the error. 1 50GB /boot, 1 50GB /swap, and 1 45GB /home.
So you created:
/boot - 50GB
swap - 50GB
/home - 45GB

That's too much disk space. For example, my disks are divided this way:
/boot - 150 MB
swap - 1 GB
/        - 25 GB
/home - all that's left

/boot is where the files needed to boot the system are saved.
swap is the swap space, the virtual memory.
/ is where the system files are. In my case, it includes every program I may install, the tmp folder, system configuration files....
/home is where my personal files and my personal configuration files are stored. That's why it should be so big (about 250 GB in my case).

Based on your post, it seems that you still have not created a root partition ( **[COLOR="Blue"]/[/COLOR]** ). You created /boot, swap, /home, but no /. And that's why that error message appears.

If you ever reinstall the system again, I suggest you to try the manual partitioning again. It's fun. :)

---

