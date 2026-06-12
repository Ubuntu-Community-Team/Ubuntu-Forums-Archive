---
title: "windows install"
date: 2008-01-05
forum: Absolute Beginner Talk
---

### Post by rockinlinux on 2008-01-05
I have been running nothing but ubuntu and mandriva for quiet sometime now but i need to install windows xp. I tried to do this once last week and it would not install...i got a strange message saying that there was not enough room on the partition for a mbr entry. I then exited the installer to find that somehow it switched all my sda numbers around so i have to reinstall ubuntu (lucky i have a /home parition)...it was a big mess.

so now i want to give it another go, even hough i know i shouldnt because i dont really need windows for anything. i guess im bored. ;)

what should i do?

---

### Post by nitro_n2o on 2008-01-05
i don't know how to use gparted.. but it seems that you have 4 primary partitions, which is the maximum you can get. . 

I think you'll need to put your windows cd and delete one of those partitions to be used by windows, which means that you'll loose some information or maybe another OS.. 

in any case, try to delete a partition from parted or windows CD, after you back up, and then use this free space as the installation partition for windows 

Good luck

---

### Post by rockinlinux on 2008-01-05
that what i tried to do before, i used the bigpartition and the XP installer gave me a MBR error saying there was not anyroom at the beggining of the disk.

---

### Post by rkd on 2008-01-05
Windows is very picky.  It cannot be installed into an extended partition, and it is best to install it as the first partition on the disk.

One possible way to get around this is to use virtualbox and install Windows into a virtual machine.  That way you won't have to fiddle with your partitions at all. Windows doesn't have direct access to the hardware that way, so you couldn't run graphics-intensive games in Windows, and access to USB devices is limited or doesn't work. But if you just want to play around with Windows a bit, that might be a satisfactory approach.

The next simplest approach is to backup any files you don't want to lose onto some external disk, delete all the partitions on the disk, install Windows, giving it only a portion of the disk for itself, install your Linux OSes after Windows is installed, then restore the files you saved.

The hardest approach is to move partitions around on your disk to make some room for Windows. I'm not very familiar with gparted, but I think you can rearrange things on your disk to make a place for Windows at the beginning.  I've not done any of this, so I may have a detail or two wrong -- I hope someone else can chime in with either confirmation or correction.  Certainly, before you start on this, read up on gparted and redoing GRUB after a Windows install, to be sure you understand the procedures and that I'm not telling you to do something the software doesn't do.

I'm particularly ignorant about gparted.  I think it can do the things I suggest you do below, but I've never used it, so I could be wrong.  See the paragraphs near the end of this post to find places to read about redoing the GRUB install after installing Windows.

If you decide to try the hard approach, here is how I think you can do it:

First backup to some removable device any data you don't want to lose.

Temporarily copy the contents of sda2, sda5, and sda6 into holding directories under /media/Media.  There seems to be plenty of empty space in that partition. To do this copy, you might use the cp command with the -r and -p options, or you might use tar. Perhaps there are even better ways that I don't know.

Delete sda2, sda5, sda6, and sda7.

Delete sda1, then create a new sda1 as NTFS, with the amount of space that you want to give to Windows.  Make sure that sda1 is placed at the beginning of the disk.

Move sda4 and sda3 so that they are adjacent and either next to the end of the new sda1 or next to the top end of the disk. The point is to make the unallocated space be one large chunk instead of two smaller chunks.

Create a new sda2 as an extended partition in the unallocated space.

Create new sda5, sda6, and sda7 inside sda2, to hold the contents they used to hold.  You might need to make them slightly smaller than they originally were, since you have devoted some of the space to Windows.

Create a new sda8 inside sda2, to hold the old sda2.

Move the contents of the temporary holding directories created at the start of this procedure into the partitions where they should be.

Boot the Windows install CD and be careful to tell it to use the partition you set up for it.

After Windows is installed, you'll need to set up GRUB again, since Windows overwrites it.  You can do that from the live CD according to the directions here:

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

Another approach to reinstalling GRUG is to use Super GRUB, described here:

[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

I've not used either, so I can't say which is easier.

You might be able to simplify this procedure if you can delete more of the partitions than I suggest, or maybe you can think of a different sequence of steps to make some unused space at the beginning of the disk.

Good luck with whichever approach you choose!

---

### Post by skymera on 2008-01-05
all i know is Windows HAS HAS HAS to be at the front of the disk.

---

### Post by bumanie on 2008-01-05
Do you have any idea what may be on sda5 and sda6?  I suspect there is very little, if anything. If this is a correct assumption, I would try to remove the extended partition with gparted and then join sda5 and sda6 together and format it as ntfs. You will then have space to install windows. But before installing windows, I would also look at joining sda2 and sda3 together, this way you will have three partitions plus the windows partition and won't need an extended partition any more. All this 'parttioning' can be done with gparted.
Hope this works OK. Please back up important data first.

---

### Post by master_kernel on 2008-01-05
It's never good to install Windows XP after Linux is already installed because Windows only likes to be installed on the first section of your hard drive. When I installed it past that point, it just screwed up my entire system.

---

### Post by skymera on 2008-01-05
perhaps get a second hard drive, cheap.

and install windows on rthat.

---

### Post by bumanie on 2008-01-05
> **master_kernel said:**
> It's never good to install Windows XP after Linux is already installed because Windows only likes to be installed on the first section of your hard drive. When I installed it past that point, it just screwed up my entire system.

You are right with that, however in this instance, if the extended partition and sda5/sda6 can be removed and joined together and made into a ntfs partition, windows would then be on the first section of the drive. Windows would overwrite the mbr, but it should then just be a matter of reinstalling grub (probably installed to sda4, by the look of the screenshot).

First we'll see whether the partitions can be altered via gparted in the manner I've described and we can worry about restoring grub later.

---

### Post by rockinlinux on 2008-01-05
sda 5 is mandriva root
sda 6 im mandriva home
sda 4 is extra space for music
sda2 is ubuntu home
sda3 is root

I am very familular with gparted so moving stuff is not a problem. and SGD (super grub disk)

> would also look at joining sda2 and sda3 together, 
they are /home and / and ill never not have a serperate home.

[qutoe]It's never good to install Windows XP after Linux is already installed because Windows only likes to be installed on the first section of your hard drive. When I installed it past that point, it just screwed up my entire system. [/quote]
me too and that why im here....i was lucky and i know enough to fix it all though.
> perhaps get a second hard drive, cheap.

and install windows on rthat.

I have a notebook. and i have other hard drives but i cant boot from USB.

I guess im just not going to do this now.

---

### Post by rockinlinux on 2008-01-05
> this way you will have three partitions plus the windows partition and won't need an extended partition any more

whats wrong with extendeds? nothing at all....they are a gift for all of us to use and everyone should take advantgae  for them. they allow you to have more than 4 partitions on your disk and that my friends is very helpful.

---

### Post by bumanie on 2008-01-05
Sorry, I missed the /root at sda3. As sda5 and sda6 are mandriva partitions, I guess you have little room to move. The only thing you could do is reduce sda4, move all the partitions away from the front of the drive and then install windows. I think I would try to get another hard drive, unless you take 20-30g from sda4. 
You would also need to add one of the linux partitions to the extended partition area as windows will only accept being on a primary partition.
Sounds like a lot of work. Hope everything works out in the end.

---

