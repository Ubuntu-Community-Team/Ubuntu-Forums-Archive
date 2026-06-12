---
title: "Dual Boot XP/Ubuntu - Partition Info needed."
date: 2007-05-19
forum: Absolute Beginner Talk
---

### Post by kingbuxton on 2007-05-19
Got an 80Gb drive - 70Gb for XP and 10Gb unused. XP is installed. Ran the LiveCD thing (7.04).

Right, ran the install - here is where I am stuck. I assume the min requirement is the main Partition for Ubuntu and a Swap Partition? So I made a 512Mb Swap and the rest is the main Partition. Can't seem to get the installer to give me an option of selecting the 9Gb bit. 

If I go guided it wants to do a full erase of the 80Gb (clean install). In manual I am not totally sure which format to use from the dropdown, there are like 7 options.

I deleted the partition and started again. Booted the CD. Ran the Partitioner from Admin and tried again. Made the main Partition and a Swap Partition. Went to install - again there is no option of the drive i just made - just the 80Gb as a whole or manual and I am back to square1.

So my question.

I have XP installed in the 70Gb NTFS and 10Gb of empty space. Which procedure to follow in the installer (after keyboard selection and all that) that will created a Partition and Swap file, of the correct type and will give me a boot menu of XP and Ubuntu on reboot.

Note: I did a search and there are few threads, but can't find anything that just gives the basics. Also all the tutorials on the www seem to be with every version of Ubuntu except 7.04 and they all look a bit different.

Most annoying part is about two years ago I had XP and Ubuntu Dual booting - it seemed easy enough, no idea why I can't get it working.

Cheers.

---

### Post by tchoklat on 2007-05-19
Download gparted and use it to partition your drive if you like. It is an iso file like the liveCD.
 
Otherwise you can use the livecd to partition your drive. you can shrink your NTFS partition and create a / partition for ubuntu, a swap of double your RAM up to 2 Gb, and a /home partition for your data
 
Tony

---

### Post by overdrank on 2007-05-19
> **kingbuxton said:**
> Got an 80Gb drive - 70Gb for XP and 10Gb unused. XP is installed. Ran the LiveCD thing (7.04).

Right, ran the install - here is where I am stuck. I assume the min requirement is the main Partition for Ubuntu and a Swap Partition? So I made a 512Mb Swap and the rest is the main Partition. Can't seem to get the installer to give me an option of selecting the 9Gb bit. 

If I go guided it wants to do a full erase of the 80Gb (clean install). In manual I am not totally sure which format to use from the dropdown, there are like 7 options.

I deleted the partition and started again. Booted the CD. Ran the Partitioner from Admin and tried again. Made the main Partition and a Swap Partition. Went to install - again there is no option of the drive i just made - just the 80Gb as a whole or manual and I am back to square1.

So my question.

I have XP installed in the 70Gb NTFS and 10Gb of empty space. Which procedure to follow in the installer (after keyboard selection and all that) that will created a Partition and Swap file, of the correct type and will give me a boot menu of XP and Ubuntu on reboot.

Note: I did a search and there are few threads, but can't find anything that just gives the basics. Also all the tutorials on the www seem to be with every version of Ubuntu except 7.04 and they all look a bit different.

Most annoying part is about two years ago I had XP and Ubuntu Dual booting - it seemed easy enough, no idea why I can't get it working.

Cheers.

Hi I hope this link will help
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)
I wish I could help more with feisty but that one I have not used! good Luck ! :)

---

### Post by Pisi-Deff on 2007-05-19
> **tchoklat said:**
> Download gparted and use it to partition your drive if you like. It is an iso file like the liveCD.
 
Otherwise you can use the livecd to partition your drive. you can shrink your NTFS partition and create a / partition for ubuntu, a swap of double your RAM up to 2 Gb, and a /home partition for your data
 
Tony
That's totally not what he asked.

The swap partition has to be formated as swap and the main Ubuntu partition( / ) ext3.
With only 10GB's for Ubuntu making a /home partition in pointless.

---

### Post by stalkingwolf on 2007-05-19
There should be a 3rd option, Use existing free space.  If you select this option Install will automatically 
set up your / and swap partitions.   If you dont have this option you may have a corrupted CD or 
you may need to create more available space ( shrink your win partition).I am not sure what the minimum requirement is.

---

### Post by kingbuxton on 2007-05-19
Got it. Nice one. Dual booting fine.

Now just got this pesky nVidia crap to sort? Off to make another thread.

---

