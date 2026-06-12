---
title: "Uninstall with Tiger"
date: 2008-02-14
forum: Apple Intel Users
---

### Post by russbuss on 2008-02-14
I installed Gutsy as a dual-boot using rEfit just fine on my MacBook Pro running Tiger.  While it was fun while it lasted, I would now like to uninstall the Ubuntu partition.  Unfortunately, it is not entirely clear how to do this.

It seems that the most straightforward way to do this is with the Mac Disk Utility.  However, when I run the Disk Utility, I can see the Ubuntu partitions, but they are greyed out.  The only option I have it to Erase them and reformat them in the process.  Is this all I need to do?  Will the partitions be removed and my hard drive restored to  its original state?  If so, what formatting option should I use?

I found some information in this post:

[http://ubuntuforums.org/showthread.php?t=649882&highlight=uninstall](http://ubuntuforums.org/showthread.php?t=649882&highlight=uninstall)

But it wasn't really that clear.  Any additional help will be appreciated.

Thanks.

---

### Post by cyberdork33 on 2008-02-14
HA! you are stuck with it now!

Ok, really, if you are on leopard, just use Disk Utility to select the partition and click the "-" minus sign to remove the partition. This will fill the space with the other partitions on your disk, i.e. the OS X partition.


Unfortunately, you are in Tiger, and it is a bit more difficult. Tiger's Disk Utility will only let you reformat the partition as is, and without having to repartition the entire disk, you cannot just remove the extra partition as can be done in Leopard. If you have boot camp available, you can use Gparted to "delete" the partition, then start the Bootcamp Assistant, and "add" a windows partition (I know this is counter-intuitive, but keep reading). When it is done, reboot back into OSX and start the Bootcamp assistant again, this time opting to "restore" the hard drive to one partition. This will delete the bootcamp-created partition, and resize the OSX partition to the full disk.

Your other option would be to use the "diskutil resizeVolume" command at the commandline to change the partition layout. There is a bit of information out there about this tool. (It is actually the tool that Bootcamp uses to resize your partitions). [http://www.google.com/search?q=diskutil+resize+volume](http://www.google.com/search?q=diskutil+resize+volume)

---

### Post by russbuss on 2008-02-14
Thanks for the info.  I figured I would have to do something screwy like this.

One question: Is gparted the same partitioning tool that is included in the Ubuntu installation CD?  If so, can I just use that to "delete" the partition prior to reformatting with Boot Camp?  I must confess, I don't possess much knowledge regarding gparted.

Thanks.

---

### Post by cyberdork33 on 2008-02-14
> **russbuss said:**
> One question: Is gparted the same partitioning tool that is included in the Ubuntu installation CD?  If so, can I just use that to "delete" the partition prior to reformatting with Boot Camp?  I must confess, I don't possess much knowledge regarding gparted.Yes, although it is named "Partition Editor" in the menus I think.

---

