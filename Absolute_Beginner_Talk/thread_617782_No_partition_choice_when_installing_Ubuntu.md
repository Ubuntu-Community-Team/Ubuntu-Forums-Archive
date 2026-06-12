---
title: "No partition choice when installing Ubuntu"
date: 2007-11-19
forum: Absolute Beginner Talk
---

### Post by jdoiv on 2007-11-19
Noob here, so please be kind.  

I have a Dell laptop (inspirion 1501) with AMD Turion 64 bit processor that I want to have dual boot between XP Pro and Ubuntu.  I down loaded the correct OS and burned it to a disc.  When I start the install process, I'm only given two choices for partitioning.  Guided, which looks as if it is going to partition the entire disc as only one partition is showing, or manual.  

The online tutorials I've looked at, ([http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)) being one of them, say I should have three choices and be able to adjust the partition size.  The installer isn't giving me this option.  

When I try to go into the manual, it shows three different partitions, sda 1 Fat 16, sda 2 ntfs, and sda 3 Fat 32.  

Is there a way to create a partition in XP so that Ubuntu will recognize it during the install process.  

TIA

---

### Post by duruttye on 2007-11-19
The XP is probably on the ntfs partition, so if one of those other two partitions is minimum 4 GB in size, you can install ubuntu on it, the recommended file format is ext3.

Hope this helps.

---

### Post by mikewhatever on 2007-11-19
> Is there a way to create a partition in XP so that Ubuntu will recognize it during the install process. 

No. To install Ubuntu, you'd have to shrink the XP partition (presumably ntfs), create partitions for Ubuntu and then install. The guided options only shows one partition because you only need to shrink one. I think that's what you should use.

---

### Post by Pumalite on 2007-11-19
Get a Gparted Live CD:[http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)
Boot from it and resize the XP partition (right click) like mikewhatever said.

---

### Post by jdoiv on 2007-11-19
Ok, I used Gparted to partition out some space and am now using the manual option in the installer to pick the right partition.  It is asking for a mount point though.  Would that be "/" or "/boot"?  

Also it mentioned needing 256 for swap.  Do I need to create another partition for the swap or will it use part of the partition I've already created?

Thanks

edit:  looks like I need to create another partition, so I just did a small one at 256 to use as the swap.

---

### Post by Pumalite on 2007-11-19
A good scheme is 10 GB for '/'
2x RAM for /swap up to 1 GB
The rest for /home.

---

