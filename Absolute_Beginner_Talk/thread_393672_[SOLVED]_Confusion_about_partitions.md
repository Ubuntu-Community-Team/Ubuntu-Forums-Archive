---
title: "[SOLVED] Confusion about partitions"
date: 2007-03-26
forum: Absolute Beginner Talk
---

### Post by Stebbins on 2007-03-26
Hi everyone,

I'm trying to install Ubuntu alongside Windows XP, and I'm running into some trouble with the partitions.  On the installation menu, I'm given three options:

* Erase entire disk (not what I want to do)
* Use the largest continuous free space
* Manually edit partition table

I first selected the second option, but when I tried to install the OS, I received an error message: "No root file system is defined. Please correct this from the partitioning menu."

So then I went back and selected the manual edit option, and got the GPartEd interface.  Now I'm afraid to try manually repartitioning my hard drive because I don't really know what I'm doing and I don't want to crash my computer (all my files are backed up, though).  I haven't been able to find any GPartEd instructions that are intelligible to someone with no partitioning experience.

My questions are:
(choosing the second option)
How do I define a root file system?

or

(choosing the third option)
How must I set up the Linux partition(s), and how can I ensure my XP files won't be destroyed?

~Stebbins

---

### Post by freebird54 on 2007-03-26
If you are not sure what is happening - I recommend going through a HowTo like this one  [http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing) 

Before you start, however, I suspect you should run defrag a couple of times on your XP drive to move things to the 'start' of the partition, as most likely you will need to resize (shrink) your Win partition to make space for Ubuntu to run on.

You could think of the process as putting up dividers to make cubicles in an office space - so that THIS is defined as Windows area, and THAT is for Ubuntu etc etc.

Hope this helps..;

---

### Post by Sef on 2007-03-26
> If you are not sure what is happening - I recommend going through a HowTo like this one [http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)


Use that one if you are using the Live CD to install.

If you are using the alternate CD to install, use the [Illustrated Dual Boot]("http://users.bigpond.net.au/hermanzone/").

---

### Post by Stebbins on 2007-03-26
> **freebird54 said:**
> If you are not sure what is happening - I recommend going through a HowTo like this one  [http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing) 

Before you start, however, I suspect you should run defrag a couple of times on your XP drive to move things to the 'start' of the partition, as most likely you will need to resize (shrink) your Win partition to make space for Ubuntu to run on.

You could think of the process as putting up dividers to make cubicles in an office space - so that THIS is defined as Windows area, and THAT is for Ubuntu etc etc.

Hope this helps..;

Thanks for the quick responses.  It looks like the walkthrough link you posted might be for an older version of Ubuntu, because my partition table screen looks rather different than the one on that page (I have the 6.10 Live CD version).  I did think that this page ([http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)) on the same website was helpful, though.

Now I have a new problem: GPartEd will only allow me to create 4 main partitions.  Linux needs 2, but WinXP already has 3 set up on the drive.  The extra two are small FAT16 and FAT32 partitions, and I'm not sure what is in them.  Any suggestions as to what I should do?

---

### Post by freebird54 on 2007-03-26
As it happens....  The partition table on hard disks suffers from limitations due to the definition being created MANY years ago - back when a 5Mb disk was quite usual.  Only 4 partitions can fit in the tiny area allotted for each disk.

Back when hard drives grew to a gigantic 40Mb, however, a standard workaround came into existence - the EXTENDED partition.  Essentially this is a 'wrapper', within which you can put other partitions.  What this means to you?  Create a single, Extended partition in the free space available, then create the 2 or 3 Linux partitions you intend to use within it.  Just go step by step - it is quite straightforward.  Linux, unlike Windows, does not require a non-extended partition to work just fine.

Sorry about the date of the HowTo - I didn't check it that closely.  I just used GPartEd from my knowledge of Partition Magic over the years (right back to OS/2 days) :oops:   Hopefully the ideas still came through though??

Don't hesitate to ask more if needed - my HD's are partitioned up the wazoo what with different distros and multiple versions of Win still hanging around...

---

### Post by Stebbins on 2007-03-26
The extended partition worked, and I now (finally) have Ubuntu installed on my machine.  I have no more questions for now.  Thank you very much for all your help.

---

