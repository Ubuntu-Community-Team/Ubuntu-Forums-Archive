---
title: "Partition question"
date: 2007-10-31
forum: Absolute Beginner Talk
---

### Post by carusoswi on 2007-10-31
The partitioning ap for 7.10 has me confused.  When it comes up, I have a choice to edit existing partitions, but no choice to create new ones.

I would like to set up a triple boot - XP, 7.04, and 7.10.  What am I missing here?

It's been a while since I installed 7.04, and that actually was a bit disastrous, as somehow, my driver letters changed so that XP now boots on my G drive, my storage partitions are C and D . . . and a second physical drive chock full of data (and one that I know I did not instruct 7.04 to alter) became corrupted so that neither OS could access the data - I had to use "GetDataBack" to access, copy, and move the data to another drive, then, reformat the corrupted drive to regain use of it.

I don't want to mess up my existing setup, so, I want to make certain this time that I fully understand what I am doing with those partitions.

I've done a little searching here, but don't find the answer to my question.

After I get to that screen where I have clicked the buttons for manual control, how do I go about creating a new partition for 7.10?

Thanks in advance for any advice.

Caruso

---

### Post by Pumalite on 2007-10-31
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)
[http://apcmag.com/5046/how_to_dual_boot_vista_with_linux_vista_installed_first](http://apcmag.com/5046/how_to_dual_boot_vista_with_linux_vista_installed_first)

[http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty_p2?](http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty_p2?)

---

### Post by bodhi.zazen on 2007-10-31
Hard to say.

You will need to first resize your existing partitions (if needed) to make "free space" into which you then make a new partition.

You can only have 4 primary partitions. If you have 3 you need to create a extended and then logical partitions.

[http://ubuntuforums.org/showthread.php?&t=282018](http://ubuntuforums.org/showthread.php?&t=282018)

---

### Post by carusoswi on 2007-11-01
> **carusoswi said:**
> 

After I get to that screen where I have clicked the buttons for manual control, how do I go about creating a new partition for 7.10?

Thanks in advance for any advice.

Caruso

I've read the links previous to these posts.  What I don't see is how I create a new partition with the partitioner supplied with 7.10.

Can someone help me with that specific question?

I don't see any option or button that takes me to a screen where I can opt to create a partition.

Sorry to be redundant, and, again, thanks for any help you can offer.

Caruso

---

### Post by Duck2006 on 2007-11-01
You can use the live cd of gparted to partition your drive.

[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

---

### Post by carusoswi on 2007-11-02
> **Duck2006 said:**
> You can use the live cd of gparted to partition your drive.

[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

If that is the partitioner that comes on the iso, then it is the application about which I have a question.  In the past, there was a way to click to add a new partition.  I don't see that option this time around for some reason.

What am I doing wrong?

Caruso

---

### Post by Duck2006 on 2007-11-02
Did you click on manual partition?
Then edit partition. You can add a partition there.
If you can't use the live cd of gparted to partition your drive.

---

