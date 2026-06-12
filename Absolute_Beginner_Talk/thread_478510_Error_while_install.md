---
title: "Error while install"
date: 2007-06-19
forum: Absolute Beginner Talk
---

### Post by bth on 2007-06-19
i want to make a dual-partition.(XP and Ubuntu)
i have 2 partions in NTFS format.

i receive an error while trying to install (in the middle of the installation) Ubuntu 7.04 from the CD.
the error says that the installation can't format the partition in "ext3" format.

what can i do for this?

---

### Post by BarfBag on 2007-06-19
Did you create the second partition from Windows with the intent of installing Ubuntu on it?  If that's the case, you're going to have to delete the extra partition and let Ubuntu do all the work.  The reason it cannot format the partition is because it's NTFS, which is not yet supported very well in Linux (although, it is improving).  Just in case you don't know how to delete the partition, I've listed the steps below.

1.  In Windows, click on the Start menu and then Control Panel.

2.  Click on Administrative Tools (this part might be a little different, depending on your settings).

3.  Click on Computer Management.

4.  In the column on the left, click on Disk Management.

5.  Right click on the extra partition and click on Delete.

6.  Boot off the Ubuntu CD and go through the install.  When the partitioning options pop-up, select the option "Use the Largest Contiguous Free Space."

Good luck!

---

