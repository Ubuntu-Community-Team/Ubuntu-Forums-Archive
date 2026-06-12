---
title: "How do I resize my primary ext3 partition safely?"
date: 2007-06-28
forum: Absolute Beginner Talk
---

### Post by diablo75 on 2007-06-28
I have a laptop with 7.04 install on it and nothing else.  I am wanting to reinstall the OS, and figured the best way to do this would be to format the hard drive.  But I'd like to try resizing the partition down to clear out free space for a new partition that will have backup data copied over to it.  Then I would format the original ext3 partition that the OS is currently installed on and then install 7.04 from scratch.  I'm trying to remove Ubuntu Ultimate from my system as it's sluggish compared to a fresh, thin install.

Thanks for any help in advanced!
:popcorn:

Edit:

Here's what I ended up doing.

I downloaded a [Gparted Live CD ]("http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828"), used it to resize my system partition that Ubuntu is installed on.

In the empty space I ended up created a new NTFS partition.  The reason for this a little beyond me at the moment, but I did it because trying to created ext2 or ext3 partitions resulted in permission problems after reboot.  NTFS was a faster alternative for the purpose of temporary backup.

---

### Post by stchman on 2007-06-28
> **diablo75 said:**
> I have a laptop with 7.04 install on it and nothing else.  I am wanting to reinstall the OS, and figured the best way to do this would be to format the hard drive.  But I'd like to try resizing the partition down to clear out free space for a new partition that will have backup data copied over to it.  Then I would format the original ext3 partition that the OS is currently installed on and then install 7.04 from scratch.  I'm trying to remove Ubuntu Ultimate from my system as it's sluggish compared to a fresh, thin install.

Thanks for any help in advanced!
:popcorn:

Use the LiveCD and then fire up gparted.  This will allow you to partition your hdd.  If you are wanting to to a fresh install then you can try this strategy:

Delete all partition on the hdd as this will make the the entire hdd free space
Create a new partition in the free space and use the left side of the slider (select ext3)

This will create a section of free space at the front of the drive and an ext3 partition at the end

When you install Ubuntu tell it to use the largest continuous free space.  You will have Ubuntu on one partition and another ext3 partition for storage.

This procedure assumes you have all your important data backed up.

---

### Post by diablo75 on 2007-06-28
I tried to resize the partition, and I get this (See attached image)

---

### Post by diablo75 on 2007-06-28
Then I tried this, and chose not to continue just yet...

What should I do?

---

### Post by diablo75 on 2007-06-28
...Anybody?

---

### Post by kpkeerthi on 2007-06-28
Are your booted into ubuntu and trying to resize the partion where you have ubuntu installed? The partition your are trying to resize should not be mounted. I suggest you to boot from ubuntu live CD and resize the partition. gparted can be accessed from the System menu -> Disk Partition Editor or something like that.

---

### Post by milton1 on 2007-06-28
Another option: download the image for the gparted live cd. boot to that, you should have no difficulty rearranging your partitions.

---

### Post by diablo75 on 2007-06-28
The screen shots above were taken IN a live CD environment.

---

### Post by kpkeerthi on 2007-06-28
As I could see from the screenshot. /dev/sda1 is mounted. Unmount /dev/sda1 and search for options in gparted to disable automounting and try again. I'm not in front of ubuntu right so can't tell you exactly where the option is in gparted.

---

### Post by kpkeerthi on 2007-06-28
Or try using Gparted Live CD

---

### Post by milton1 on 2007-06-28
> **diablo75 said:**
> The screen shots above were taken IN a live CD environment.

In an ubuntu live cd, or a gparted live cd? they are different. The gparted live cd will not mount the partitions, and will work much more smoothly.

---

### Post by diablo75 on 2007-06-28
I used the Gparted live CD and was able to resize the partition.  That was all I wanted to do for now, and restarted to make sure my system still booted just fine.  After it booted, I used Gparted (from within Ubuntu) to create a new partition in the unallocated space.  I told it to make a "Primary Partition" with ext3.  Then I told it to format the drive as an ext3.

Now, I have a disk icon on my desktop that is suppose to represent the new partition.  But I can't write anything to it.  The only contents of the drive appears to be a "lost+found" folder with a big red X over the icon.  Upon attempting to open the folder, it says I don't have permission to.

So I deleted the partiton, rebooted with the Gparted CD, and attempted to do the same thing again using Gparted.  Rebooted after creating and formating an ext2 partition (it's what it selected by default, I don't know if that made a difference).

Rebooted, same problem.  The partition appears to mount, but I can't read or write anything to it.

---

### Post by diablo75 on 2007-06-28
SOLVED:

I created an NTFS partition instead, then used automatix to quickly mount the NTFS partition.  I'm copying data to it right now.

---

