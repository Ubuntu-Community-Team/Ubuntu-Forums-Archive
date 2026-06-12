---
title: "Which partitioning method to use?"
date: 2007-06-11
forum: Absolute Beginner Talk
---

### Post by resander on 2007-06-11
I am a Linux newbie and I am using the alternate iso distribution of 7.04 (the graphicinstall did not work for me).

The computer is just back from the repair shop and I asked the guy there to  divide the hard disk into two partitions, half half. In Windows these show up as drive c and drive d. Windows XP runs on drive c and I want Ubuntu to use the space of drive d.

I am now at the install step 'Partition disks' and can see three choices:

   Guided - resize SCSI1 (0,0,0) partiton #5 (sda) and use freed .....
   Guided - use largest continous free space
   Manual

I don't want to make a mistake and clobber Windows XP. Which method do I choose?

---

### Post by malathia on 2007-06-11
So, I take it you're able to access the internet during the installation process or did you abort and then login to post this? You can IM me if you like.

I'd recommend manual. It should show you the two partitions on the drive, the file type that they're formatted with, etc.

---

### Post by p_quarles on 2007-06-11
No, don't do manual unless you've been using for Linux for years. Assuming that your D: drive is empty (if it's not, make sure it is) choose "largest continuous free space." This won't mess with the C: because it's not "free." 

And, of course, make sure you defrag both partitions and back up any sensitive data before you do this.

---

### Post by zvacet on 2007-06-12
Manual and it goes like this:
1.root =10GB        mountpoint /
2.home = rest of free space exept      mountpoint /home
3.swap =2xRAM

if you have 20GB or less on youe D drive you can go with largest continuous free space.

---

### Post by resander on 2007-06-12
First, let me say how great this forum is. Answers within minutes! If other forums would be the same, my hair would be a lot darker now!

I am putting XP and Ubuntu on to an old, spare PC that is sitting next to the one I am using for writing this forum post.

I defragged drive c and and d from XP.

XP then reported the following sizes for drive c and d:

  c:  Free space 17.2 GB  (c used for XP)
      Total size 19.5 GB    

  d:  Free space 17.7 GB  (d intended for Ubuntu)
      Total size 17,7 GB


 I selected 'Use largest continuous free space' method, but that failed with the following message:

"
Failed to partition the selected disk.

This probably happened because the selected disk or free space is too small 
to be automatically partitioned.
"

I don't understand why it failed, but went back and selected Manual partitioning. This is how it looked:

"
This is an overview of your currently configured partitions and mount points. Select a partition to modify its settings (file system, mount poiut etc), a free space to create partitions, or a device to initialise its partition 
table.

 SCSI1 (0,0,0) (sda) - 40.0 GB ATA ST340014A
     #1 primary     21.0 GB B K fat32    /media/sda1
     #5 logical     19.0 GB   K fat32    /media/sda5
        pri/log      8.2MB      FREE SPACE
"

Partition #5 corresponds to Windows drive d.
At this point, how do I tell the installer to use this partition for Ubuntu and for swapping?

---

### Post by dptxp on 2007-06-12
Go for Manual Partition.

Select Drive D.

Resize to 6 GB for /, ext3 format.
Resizse rest space leaving out 1 to 2 GB for SWAP.
Set it /home, ext3 format , you will need a small program in Wndows to R/W to this partition from Windows.
Set rest for SWAP.

Click OK.

Ensure that C drive is not checked for format.

---

### Post by zvacet on 2007-06-12
You should select  /media/sda5 and delete it.That will give you more free space,and after that you will be able to make Ubuntu partition by selecting largest continuous free space.

---

### Post by resander on 2007-06-12
Thanks for the info, but being an absolute Linux newbie I am very unsure about this.

dptxp wrote:

>>Resize to 6 GB for /, ext3 format.
>>Resizse rest space leaving out 1 to 2 GB for SWAP.
>>Set it /home, ext3 format
>>Set rest for SWAP.

After some fumbling around with the 'Partition disks' install step (of the alternate distribution) the installer now displays:

 SCSI1 (0,0,0) (sda) - 40.0 GB ATA ST340014A
     #1 primary     21.0 GB B K fat32    /media/sda1
     #5 logical     6.0 GB    F ext3     /
     #6 logical     11.0 GB   f ext3     /home
     #7 logical     1.0 GB    f ext3     /usr
        pri/log     1.0 GB    FREE SPACE

Is this correct?
Is the name /usr correct for the swap partition?

---

### Post by dptxp on 2007-06-12
The first 3 are.
Delete all next ones till the unused space is left as one block.
Edit it to format as SWAP.
no need for /usr. Your drive is not very large.
Select SWAP, /usr is not correct for SWAP. Maybe SWAP is in FORMAT selection in the same box. I do not
remember.

---

### Post by mcduck on 2007-06-12
Your life will be much easier if you just boot into windows and delete the d: partition completely. Then you can use the 'Use largest continuous free space'-option to automatically handle partitioning for you (it's looking for free, unpartitioned disk space and therefore can't use the partition you already have made).

---

### Post by timcredible on 2007-06-12
actually, this would have been much easier had you left your hard drive as one drive (C:), because the installer would have asked you how much you want to leave for windows, and then partitioned and installed all by itself.  now, you have a harder task.  what you need to do to get linux running is have, at a minimum, 2 partitions for linux - one is for swap space (windows uses a file for this, linux uses a partition), and one for the system and user files (/).  you can get fancy with a separate partition for /home (that's what most of us that have been using linux for a while do), but i wouldn't recommend it to start out first time.  so, you need to choose manual, identify your second partition (D: in windows), and delete it.  then it should show up as free.  then you can go back to the part where you can choose 'use free space'.  the reason it doesn't work now is that you don't have any free space.

---

### Post by nanotube on 2007-06-12
> **resander said:**
> Thanks for the info, but being an absolute Linux newbie I am very unsure about this.

dptxp wrote:

>>Resize to 6 GB for /, ext3 format.
>>Resizse rest space leaving out 1 to 2 GB for SWAP.
>>Set it /home, ext3 format
>>Set rest for SWAP.

After some fumbling around with the 'Partition disks' install step (of the alternate distribution) the installer now displays:

 SCSI1 (0,0,0) (sda) - 40.0 GB ATA ST340014A
     #1 primary     21.0 GB B K fat32    /media/sda1
     #5 logical     6.0 GB    F ext3     /
     #6 logical     11.0 GB   f ext3     /home
     #7 logical     1.0 GB    f ext3     /usr
        pri/log     1.0 GB    FREE SPACE

Is this correct?
Is the name /usr correct for the swap partition?

no, swap doesn't get a mountpoint, so /usr is not correct. here's what you do:

leave the first partition as is (that's your windows drive)
make the second partition a "primary", leave it as 6 gb
assuming you want your swap to be 1 gb, then the next two partitions should be:
logical, 12 gb, /home; and
primary, 1 gb, swap (there is no mountpoint for swap, it should be listed as 'swap')

when you make that last swap partition, just tell it to use the remaining free space, and the partitioner will make sure to use all available remaining unpartitioned disk, so you won't be leaving any to waste.

the main thing to note is that "free space" in the context of partitioning is not the same thing as "free space" in the context of regular computer usage. here, free space doesn't mean "there are no files on it", but "unformatted space". so, all of those partitions you create will have some free space on them at the end, in the sense of 'they won't have files on them', but they will be partitioned. so don't leave "free space" at this stage, or you will just be leaving unformatted space that you won't be able to use. is that kind of making sense? ;)

---

### Post by dptxp on 2007-06-12
> **mcduck said:**
> Your life will be much easier if you just boot into windows and delete the d: partition completely. Then you can use the 'Use largest continuous free space'-option to automatically handle partitioning for you (it's looking for free, unpartitioned disk space and therefore can't use the partition you already have made).
Can be done using Install CD too. Delete D partition, resize C (the disk becomes one partition) to original size (then no defragmentation shall be needed) and create other partitions.

---

### Post by resander on 2007-06-12
Many thanks all!

Ubuntu is now installed and boots OK.

The information in the responses was very useful for a newbie like myself and would be for many other newbies too.

It would be nice to have a sticky thread about partitioning with contributions from Ubuntu gurus. 

Again, many thanks.

---

### Post by zvacet on 2007-06-13
We try to solve your specific situation,but if you want something more here it is 

[http://www.psychocats.net/ubuntu/]("http://www.psychocats.net/ubuntu/")
[http://www.cutlersoftware.com/ubuntuinstall/]("http://www.cutlersoftware.com/ubuntuinstall/")
[http://www.linuxcommand.org/]("http://www.linuxcommand.org/")
[http://www.oreillynet.com/linux/cmd/]("http://www.oreillynet.com/linux/cmd/")

---

