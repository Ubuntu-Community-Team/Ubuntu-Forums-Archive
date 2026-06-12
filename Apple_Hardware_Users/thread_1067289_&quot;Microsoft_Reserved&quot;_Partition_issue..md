---
title: "&quot;Microsoft Reserved&quot; Partition issue."
date: 2009-02-11
forum: Apple Hardware Users
---

### Post by nate_derby on 2009-02-11
Hello all - hopefully you can help me with this problem...

I recently installed Ubuntu 10 and Fedora 10 onto two separate partitions on my Macbook Pro (1, 1). I was using rEFIt to boot the separate partitions but I was only able to get rEFIt to work a couple of times. I've literally done everything I can find to get rEFIt working again and it won't, so I'm done with it. I was hoping to start from scratch - get Windows back on my Macbook Pro and use Windows to boot into Linux.

I was able to delete one of the Linux partitions (not sure if it was Ubuntu or Fedora), but the other partition and remaining swap drive (disk0s5 and disk0s6 on my machine) are set to a "Microsoft Reserved" partition type and I can not mount the disks or modify them whatsoever using Disk Utility. I've also tried by using the basic diskutil commands I know in the Terminal, but they are no use. I need to get rid of these partitions to reclaim the space on my disk.

So...what the hell do I do? Is there something I could do via Windows that can't be done through OS X? I feel like I need to just back-up my data, wipe the drive and re-install OS X but I don't have my 10.5 discs anymore, and I've never had to wipe any drives so I wouldn't be sure how to go about it properly. I'm feeling pretty hopeless at the moment. Thanks for any help.

---

### Post by cyberdork33 on 2009-02-11
what is your FINAL goal?

OS X + Ubuntu + Fedora

or

OS X + Ubuntu + Fedora + Windows

What?

Have you read through:
[https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation](https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation)

If you need to delete partitions, you can boot the Ubuntu LiveCD and use the partition editor (gparted) to delete them.

You will very likely NEED rEFIt, but I think you are having trouble because some of the partitioning issues you will run into. Particularly the 4 partition limit in the MBR, and partition table sync bug.

---

