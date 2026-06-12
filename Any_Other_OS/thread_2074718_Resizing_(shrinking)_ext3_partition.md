---
title: "Resizing (shrinking) ext3 partition"
date: 2012-10-22
forum: Any Other OS
---

### Post by vicke4 on 2012-10-22
Hi all,
I have a laptop with 300GB hard disk space.It contains windows 7 & boss linux in three partitions.The partition containing boss linux has 94GB itself.I can't read and write that partition in windows 7.So,i want to shrink that partition to 10GB and convert the remaining 80GB to NTFS.Is there any way to do this?
                        Thank you.

---

### Post by ajgreeny on 2012-10-22
First things first.

**BACKUP - BACKUP - BACKUP.  **Just in case things go wrong.

You can do what you want with gparted on a live ubuntu CD/USB that you would have used to install the ubuntu OS.  I have no idea about boss linux, but if it does not use a live system to install or does not include gparted you will have to get a copy of either ubuntu live CD or download gparted live CD, burn it to a CD and use that.

Boot to the live system, ubuntu or gparted, and start gparted.  This will show you the partitions on your disk and allow you to shrink the boss partition, and then make a new ntfs data partition in the space made available.  The new partition will be seen by windows automatically, but you will need to edit /etc/fstab in boss to mount it at boot time.

---

### Post by jerrrys on 2012-10-22
This may help

[http://www.dedoimedo.com/computers/gparted.html#mozTocId335513](http://www.dedoimedo.com/computers/gparted.html#mozTocId335513)

---

### Post by mips on 2012-10-22
Any livecd with gparted on it should do the job. Resize the ext3 partition (backup and data on the drive) and then create a new ntfs partition.

---

### Post by vicke4 on 2012-10-23
Thanks for all of your reply guys i successfully shrinked the boss linux partition to 15GB(that was a 97GB partition now it has only 15GB remaining 82GB is unallocated),now i'm facing one problem i can't create a new partition using the unallocated 82GB.when i try to create a partition,Gparted reads the following,

                        "It is not possible to create more than 4 primary partitions
If you want more partitions you should first create an extended partition. Such a partition can contain other partitions. Because an extended partition is also a primary partition it might be necessary to remove a primary partition first."

---

### Post by jerrrys on 2012-10-23
Your first post said 3 partitions.  But now gparted says you have 4.

Could you post a pic of gparted to clear up the confusion?

---

### Post by mips on 2012-10-23
You are only allowed four normal partitions on a drive. If you want more you have convert one to a extended partition and create the rest of the required partitions inside the extended partition.

So somewhere you will have to delete something. I fyou have a swap partition it would be th easiest to delete and then recreate inside a extended partition.

---

### Post by vicke4 on 2012-10-23
@mips i can't get what you say please elaborate your solution whatever i posted the screenshot.

---

### Post by black veils on 2012-10-23
the problem is, you have 2 windows partitions at the start, one is for recovery, those are primary. then, you have an extended (which is primary). and finally, your linux system is on a primary partition. i dont know what to suggest, but that is your situation. await advice..

---

### Post by mips on 2012-10-23
> **vicke4 said:**
> @mips i can't get what you say please elaborate your solution whatever i posted the screenshot.

Looking at that it says to me you have,

sda1 primary
sda2 primary
unallocated (ignore this)
sda3 extended
sda4 primary
unallocated

You have reached the limits of your allowable primary partitions.

My suggestion to you is to backup whatever is in sda4 (assuming it's boss linux?). Delete sda4 and expand sda3 so your extended partition takes up the remaining space on your hard drive (ie resize sda3!). Once that is done you can create a new partitions inside the extended partition (sda3).

Hope this makes sense. You are only allowed 4 primary partitions on a msdos partition table. So you could do 3 primary partitions +1 extended partitions and then create any additional partitions inside the extended partition.

---

### Post by vicke4 on 2012-10-23
Yes,sda4(15GB)contains boss Linux.you ask me to delete that partition(after backing it up) and extend sda3.  After the resizing process sda3'll have (141+15+82) 238GB.Am i correct?  I should create 15GB partition(for boss)and resize sda5 (141GB to 223GB).after all was done.am i correct?  My doubts: Boss has the grub.if i delete sda3 my system'll become unbootable.correct?  I don't know how to back up the system partition.if i back up and replace it after the above process,can all the configurations(even desktop shortcuts)be brought back?  if all is reversible(in the case of boss os) please tell me how to back up sda4.

---

### Post by mips on 2012-10-23
> **vicke4 said:**
> Yes,sda4(15GB)contains boss Linux.you ask me to delete that partition(after backing it up) and extend sda3.  After the resizing process sda3'll have (141+15+82) 238GB.Am i correct?  I should create 15GB partition(for boss)and resize sda5 (141GB to 223GB).after all was done.am i correct?  My doubts: Boss has the grub.if i delete sda3 my system'll become unbootable.correct?  I don't know how to back up the system partition.if i back up and replace it after the above process,can all the configurations(even desktop shortcuts)be brought back?  if all is reversible(in the case of boss os) please tell me how to back up sda4.

Sorry I can't comment on the details but if you can I would suggest you just backup any data you have in boss and once you have repartitioned to simply reinstall boss. Grub is installed on the MBR of sda and I have no idea how the partitions are gonna be named/numbered after you resize and recreate.

When you delete sda4 and resize sda3 to take up the remainder of the end of the drive you will have sda3 and inside sda3 you will have sda5 & 97.65GB (15+82.65GB) of free space where you can create additional partitions.

---

### Post by Cheesemill on 2012-10-23
I know I'm a bit late but you could have just installed [Ext2Fsd]("http://www.webupd8.org/2011/08/access-ext4-ext3-or-ext2-partitions-in.html") in Windows to give you access to your linux partitions.

---

### Post by vicke4 on 2012-10-23
@Cheesemill i downloaded that software and i don't know how to use that and it's not working for me now.I'll check it out tomorrow.  @mips backup means just copying all things in that partition and saving(pasting)it in an external harddisk and it can be used whenever needed correct?  Or should i use a separate application to back up that Linux partition?  And sorry for the inconvenience I'm a newbie in such case.

---

### Post by vicke4 on 2012-10-24
I mean i should copy the entire sda3 and save that on an external drive and replace that files after creating a new primary partition for boss linux.this process is called back up.isn't it?


can i do it using live cd? or should i use a separate software for doing this process successfully?

---

### Post by mips on 2012-10-24
> **vicke4 said:**
> I mean i should copy the entire sda3 and save that on an external drive and replace that files after creating a new primary partition for boss linux.this process is called back up.isn't it?


can i do it using live cd? or should i use a separate software for doing this process successfully?

I would just backup any email, photos, music, documents etc (basically what's in your home folder) and any config files you might have changed and want to restore after reinstalling boss linux.

You can use a livecd for this and simply drag & drop the files to another partition/drive or put it on a usb flash stick.

---

### Post by vicke4 on 2012-10-24
I know we can back up that kind of personal files.what I'm asking is can we back up a installed os?that's what I'm asking can i create a back up of sda3?so that we can restore it later without installing boss from the scratch.

---

### Post by offgridguy on 2012-10-24
Very interesting thread. thank you vicke4, i need this info also.

---

### Post by mips on 2012-10-24
> **vicke4 said:**
> I know we can back up that kind of personal files.what I'm asking is can we back up a installed os?that's what I'm asking can i create a back up of sda3?so that we can restore it later without installing boss from the scratch.

Yes you could, you can use dd or clonezilla to image the partition to a file and then restore it afterwards but I suspect you will have to reconfigure your UUIDs and reinstall/update GRUB.

---

### Post by vicke4 on 2012-10-24
i can't reply for next two day. i'll be back after two days.thanks for all of your help mips.

---

### Post by vicke4 on 2012-10-28
> **mips said:**
> Yes you could, you can use dd or clonezilla to image the partition to a file and then restore it afterwards but I suspect you will have to reconfigure your UUIDs and reinstall/update GRUB.  Yes i did this using clonezilla the back up contains a folder.the back up folder's size is 2.6GB but the Linux partition(15GB) has used 6GB space.is it correct(back up file is using smaller size than the original)?       now can i delete the Linux partition and restore it back?okay what's meant by UUID?

---

