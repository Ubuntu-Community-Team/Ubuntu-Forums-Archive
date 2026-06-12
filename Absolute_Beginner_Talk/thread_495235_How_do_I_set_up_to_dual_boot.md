---
title: "How do I set up to dual boot?"
date: 2007-07-07
forum: Absolute Beginner Talk
---

### Post by Utopus on 2007-07-07
Hello, I'm a newbie. I like to install Ubuntu 7.04 in my PC, but I already have Windows Vista installed on. I heard that I can have both OS and dual boot..? On the other day, I've tried it to install Ubuntu and it erased my Vista. Now I reinstalled Vista and Ubuntu is gone... Someone please help me... :(

---

### Post by Moop on 2007-07-07
The stickies at the top of the page have lots of useful info. How to dual boot Ubuntu and Vista. 
[https://help.ubuntu.com/community/WindowsDualBoot]("https://help.ubuntu.com/community/WindowsDualBoot")

---

### Post by atria on 2007-07-07
Ubuntu and Vista must exist on different partitions.

Heres the procedure for simple dual booting:
While installing vista at the partition manager, create a partition instead of using the entire disk for vista.

Once vista is installed, boot the Ubuntu live cd and while you're at the patitioning step, make sure that the "erase disk" option is not selected. Instead choose to manually partition or to use existing free space. That should ensure that vista is not erased.

Finally the problem with ubuntu being erased when vista is installed is because vista overwrites ubuntu's bootloader (in this case grub). It is definitely possible to reinstall grub so that dual booting works.

You will want to check out the grub manual in [https://help.ubuntu.com/community](https://help.ubuntu.com/community)

Good luck

---

### Post by p_quarles on 2007-07-07
Here's the deal: the version of gparted (the partition manager) that comes with the Ubuntu CD doesn't seem to notice the presence of Vista, or doesn't think it can shrink the volume. It works better with older versions of Windows.

Step by step instructions:

1) In Vista, defragment your hard drive **twice**. This will take some time.
2) Go to System Tools >> Disk Management. This will show a list of your partitions. By right-clicking on the main Vista partition, you get the option of shrinking the partition to make free space. Free up at least 10 Gigabytes, preferably more (depending on how much open space you have).
3) Boot from the Ubuntu disk. During the installation process, it will now give you the option to use the free space you just created to install Ubuntu. Choose that option, and answer the questions, etc., just like the first time you installed it. 
4) If you did it right, on the next bootup from the hard disk, you'll be given the option of booting from Ubuntu or Vista (though the GRUB boot manager refers to Vista by its production codename Longhorn).

FYI, if you had done a quick search on Google or in these forums, you would have come across several posts with these exact same instructions.

---

### Post by p_quarles on 2007-07-07
> Finally the problem with ubuntu being erased when vista is installed is because vista overwrites ubuntu's bootloader (in this case grub). It is definitely possible to reinstall grub so that dual booting works.

That's the case if Windows already had a separate partition, but it sounds like he/she used the entire disk for Ubuntu before reinstalling Windows -- so it must have formatted the entire disk a second time, meaning it didn't just erase GRUB.

---

### Post by atria on 2007-07-07
1) That was implied in the first part of my explanation (where he erased vista with ubuntu). It is far easier to destory vista's partition with ubuntu than the other round, where you have to actually instruct vista to delete the unknown partition.

2) I was trying to show that the order doesn't matter; if he chooses to reinstall vista again in future, his ubuntu installation will not be lost.

3) You might want to edit your post in future instead of double posting.

Cheers

---

### Post by p_quarles on 2007-07-07
> 1) That was implied in the first part of my explanationNo, it wasn't. You may have intended to imply that, but you did not do say in a way that would be graspable to someone who doesn't know what a partition is.

> 
3) You might want to edit your post in future instead of double posting.You might want me to, but that has nothing to do with me. In the future, please say what you mean, and don't attribute it to me.

---

### Post by atria on 2007-07-07
[edit]Nevermind[/edit]

I'm not trying to start a flamewar with you here.

See you, i'm out.

---

### Post by Sef on 2007-07-07
Read the [Illustrated Dual Boot]("http://users.bigpond.net.au/hermanzone/").

---

### Post by Utopus on 2007-07-08
I thank you all for your help! Thank you very much! :)

---

### Post by halon on 2007-07-08
From my experience with dual booting, Windows needs that first partition.  Having said that, and please for give me if I'm not 100% accurate with the Vista info but install your Vista disk, and erase all partitions on your hard drive so you have n bytes of free space (n is your disk size).  

You should then have the option to create a partition of a particular size, so specify the size for Vista, format the partition and install.  You will then have a disk with n- (bytes for Vista) of free space and Vista.

Set your boot order to boot from cdrom with Ubuntu and follow the install. When it comes to the option, select "Use largest contiguous free space" and install.  This will install Ubuntu and GRUB.  In the end you should be presented with a boot selection screen at start up that lists the OS's installed on that machine.

Hope that helps.

---

### Post by dptxp on 2007-07-08
First 10 GB for Vista. Next 6-8 GB for Ubuntu / (root) (minimum 4 GB). Next data partition (/home or just any in ext3 format). You can have multiple data partitions, need to install a program to access ext3 from Windows. Last 2GB for SWAP.

Make maximum 3 primary partitions, you can have 4 but if you need more than do not make 4th as primary.

Install Vista First. No need to defragment if installation is new.

Resize with Live CD at time of install (manually), one by one.

---

### Post by por100pre1 on 2007-07-08
Install Vista first and then use Vista's Disk Manager to shrink its own partition (you may need to defragment first if its not a fresh install). Then install ubuntu on the free space.

---

