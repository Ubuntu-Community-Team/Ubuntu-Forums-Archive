---
title: "Partition problems"
date: 2007-02-06
forum: Absolute Beginner Talk
---

### Post by mosslack on 2007-02-06
I recently downloaded v6.10 and am trying to install it on a multi-OS computer.  Boot It NG is my boot manager.  I set up a 5 Gb partition for Ubuntu, 1 Gb for Swap and have a 10 Gb Fat 32 partition for data that is common to all my different OS'es.  When I get to the disk parttion portion of the install program, I chose to manually edit the partitions.  I can see the ones I setup clearly marked.  The 5 Gb is tagged as Boot and the swap shows as it should.  When I click the forward button and select the how the partitions are to be used I set the 5 Gb as root "/", the 1 Gb as swap and the 10 Gb partition is set to media/hda3.  Now when I click the forward button I get an error message that says No root file system.  I have it formatted as reiser fs and marked as root "/".  What am I missing?

---

### Post by bodhi.zazen on 2007-02-06
It's a bug.

Here is a work arround : [http://ubuntuforums.org/showpost.php?p=1700787&postcount=29](http://ubuntuforums.org/showpost.php?p=1700787&postcount=29)

---

### Post by mosslack on 2007-02-06
that worked great, thanks!

---

