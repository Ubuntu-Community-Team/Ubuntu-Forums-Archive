---
title: "Bootloader partition help request"
date: 2006-03-05
forum: Apple PPC Users
---

### Post by nuke on 2006-03-05
Hi all!

I am trying to get Kubunutu installed on my new hard drive.  I thought I read all the installation documentation and read through the forums, but I missed something about this Apple_Bootloader partition.

I am trying to install on a Bronze Keyboard Powerbook.  It has a New World ROM.  The install goes well until it gets to the bootloader part.  As I didn't read about this before, and hadn't prepared a partition for it, I aborted the install.

Could someone explain to me if and why I need this?  Does it really have to be at the start of the drive?  Why?

What is the risk of letting Kubuntu just create a partion for this?  Will it kill the existing partition map or will it move all the existing partitions back to make room for this?

Could you also help me with how to search for this info?  I did advanced search for the forums, searched the wiki but I still can't find the documentation that actually talks about it.

I have a 40GB drive.  I read a bunch of docs and posts to figure out how to partition my disk but now I find out that I probably missed one.  My drive was partitioned as follows:
/dev/disk01 to /dev/disk08 -> what ever Apple disk partitions it does automatically [~3GB]
/dev/disk09 -> OS 10.2.8 and Applications [8.6GB]
/dev/disk10 -> ext3 for [K]ubuntu [6GB] but not installed yet.
/dev/disk11 -> swap for mac os [1GB]
/dev/disk12 -> swap for [K]ubuntu [1GB]
/dev/disk13 -> /Users [20GB]

Thanks in advance for your help.

---

### Post by nuke on 2006-03-05
Hi all!

I am trying to get Kubunutu installed on my new hard drive.  I thought I read all the installation documentation and read through the forums, but I missed something about this Apple_Bootloader partition.

I am trying to install on a Bronze Keyboard Powerbook.  It has a New World ROM.  The install goes well until it gets to the bootloader part.  As I didn't read about this before, and hadn't prepared a partition for it, I aborted the install.

Could someone explain to me if and why I need this?  Does it really have to be at the start of the drive?  Why?

What is the risk of letting Kubuntu just create a partion for this?  Will it kill the existing partition map or will it move all the existing partitions back to make room for this?

Could you also help me with how to search for this info?  I did advanced search for the forums, searched the wiki but I still can't find the documentation that actually talks about it.

I have a 40GB drive.  I read a bunch of docs and posts to figure out how to partition my disk but now I find out that I probably missed one.  My drive was partitioned as follows:
/dev/disk01 to /dev/disk08 -> what ever Apple disk partitions it does automatically [~3GB]
/dev/disk09 -> OS 10.2.8 and Applications [8.6GB]
/dev/disk10 -> ext3 for [K]ubuntu [6GB] but not installed yet.
/dev/disk11 -> swap for mac os [1GB]
/dev/disk12 -> swap for [K]ubuntu [1GB]
/dev/disk13 -> /Users [20GB]

Thanks in advance for your help.

---

### Post by Ptero-4 on 2006-03-07
You can reformat /dev/disk10 and put the bootloader partition (it's 1MB only).

---

### Post by nuke on 2006-03-08
[QUOTE=Ptero-4]You can reformat /dev/disk10 and put the bootloader partition (it's 1MB only).[/QUOTE]

Thank you.  

Then I presume the location of the bootloader partition isn't important?  

If it isn't, then I will probably steal a MB from the swap which is about 256MB too big based on the 2xRAM rule of thumb.  And I also have a separate mac and linux swap partition.

Is there a part of the script that asks where to install the boot loader?

Thanks again.

---

