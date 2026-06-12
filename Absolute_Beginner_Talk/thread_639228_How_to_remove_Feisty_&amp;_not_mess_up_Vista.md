---
title: "How to remove Feisty &amp; not mess up Vista?"
date: 2007-12-12
forum: Absolute Beginner Talk
---

### Post by barbi.jo on 2007-12-12
I want to remove Feisty from my computer but don't want to mess up my Vista.  How can I do this safely?  I know that it writes something to the MBR and am not sure how to remove it without damaging my Vista.

---

### Post by LaRoza on 2007-12-12
Do the following:

* Download the Super Grub Disk (it is in the link in my sig)
* Burn it, and boot from it. Restore the Windows MBR
* Reboot

It should boot directly into Windows

Use "Disk Management" to delete and reformat the Linux partitions.

Don't delete any partitions before doing this, that way, you will have a functional system at all times.

---

### Post by hockeyfighter09 on 2007-12-12
Im not sure if this is the right way to do it, wait for someone to confirm or tell you something else before you do it.  Pop in the Ubuntu live cd and download a program called gparted.  Then delete the partition with Ubuntu on it and expand the Vista Partition so it takes up the whole harddrive.  Then after that pop in the Vista cd and go to recovery mode and type in fixmbr to fix the boot menu.  Again dont try this method until someone with more knowledge confirms it.

---

### Post by LaRoza on 2007-12-12
> **hockeyfighter09 said:**
> Im not sure if this is the right way to do it, wait for someone to confirm or tell you something else before you do it.  Pop in the Ubuntu live cd and download a program called gparted.  Then delete the partition with Ubuntu on it and expand the Vista Partition so it takes up the whole harddrive.  Then after that pop in the Vista cd and go to recovery mode and type in fixmbr to fix the boot menu.  Again dont try this method until someone with more knowledge confirms it.

That will work if the OP has the Vista disk, and knows what to do.

The method I gave, will make Windows usable at all times.

---

### Post by barbi.jo on 2007-12-12
Thanks.  I hate to do it because I love Ubuntu but my new computer just refuses to cooperate with me getting it set up and having to restore everything repeatedly when I mess things up so badly is very time consuming.  It's really not that big of a deal.  I'll just use the Vista pc when working and the Ubuntu pc when not. :)

---

