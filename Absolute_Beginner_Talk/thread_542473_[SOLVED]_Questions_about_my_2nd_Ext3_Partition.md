---
title: "[SOLVED] Questions about my 2nd Ext3 Partition"
date: 2007-09-04
forum: Absolute Beginner Talk
---

### Post by Brightbelt on 2007-09-04
Hi,
I'm on Feisty and just recently wiped Vista off my computer, that being the only way I could get more hard drive room for Ubuntu. Think of a spiraling disaster involving my attempts to use G-Parted and you'll get an idea.    

So Ubuntu got the big partition and I wiped the second one clean (it became unallocated space) and attempted to expand Ubuntu's partition up the limit. But something,...I know not what....prevented that expansion and I got an error every time I tried to expand Ubuntu's partition into neighboring, unallocated space to its right. 

So I formatted it as ext3 and left it as a partition just sitting there. It shows up on my desktop as a drive titled 'sda'. But I can't read or write to it even though it is an Ext3 format.

Is this just irrevocable dead space beyond repair?? Or is there any way to use it ??

BTW, this inability to change partition sizes was still reminiscent of Vista, because even though the Vista partition had 80+ GB of free space it wouldn't let me shrink it to save my life.

Many Thanks for any clarifications and/or help.

Frank B.

---

### Post by mikewhatever on 2007-09-04
Perhaps you only need to change permissions for that partition and mount it properly. [http://psychocats.net/ubuntu/mountlinux](http://psychocats.net/ubuntu/mountlinux)

---

### Post by vanadium on 2007-09-04
Before enlarging the first partition, the second should really have been removed. I am not sure whether you really effectively removed your second partition.

You could now leave your system with two partitions anyway, but you will have to manually configure your system to mount the second partition automatically. There are lots of guides on fstab and mounting, but basically it goes like

* create a mount point for your second partition: "sudo mkdir /mnt/partition_2"

You can customise the name ("partition_2") of the moint point.

* Add an entry to fstab so that the drive gets mounted during boot time

For this, you need to know the name of your partition. The command "sudo fdisk -l" will list all your drives and partitions. It will be something like "/dev/sda2"

Second, you should copy your /etc/fstab to a backup copy in case you screw up.

sudo cp /etc/fstab /etc/fstab.backup

Now edit /etc/fstab ("gksudo gedit /etc/fstab"). Add the line:

/dev/sda2 /mnt/partition_2 ext3 defaults 0 2

Save the file

* "sudo mount -a" will reprocess fstab. If an error message appears, you made a mistake. If not, you should be able to access the drive through /mnt/partition_2 (or the name you choose). You should now, as root, create some directories on that drive and give the directories to the different users on your system so they can read and write to it.

---

### Post by PetruM on 2007-09-04
I'm not sure whether you can resize a partition while it's being used (mounted) or not.  Correct me if I'm wrong. 
Personally, I always resize partitions using the live CD and I have to unmount them before I do it, else it fails. :popcorn:

---

### Post by Brightbelt on 2007-09-04
Thanks for the help, guys. I used the live CD when I was trying the partition expansion, and in response to Vanadium about completely removing the other partition, I had in fact 'deleted it' and it showed itself to be free, unalllocated space. (grey color there in GParted)

Now I've heard in windows that 2 restarts are needed for the OS to fully process these type of partition changes, but I don't know about Linux.  

What must be understood about all this is that GParted LET ME RESIZE THE PARTITION at first, like it was a legitimate procedure and THEN threw up an error when I tried to apply it. 

Vanadium, I appreciate the detailed instructions. I'll see if I can get up my nerve to try them. Is there any danger of breaking Grub with that procedure? One recent attempt to use GParted resulted in me breaking Grub and I had to do a reinstall. 

(I tried to fix it with SuperGrub but it gave me an error 15: file missing. I've never been able to fix a Grub anyways)

Many Thanks again for helping, Frank B.

---

### Post by Brightbelt on 2007-09-04
More Thanks are in order. Thanks Mikewhatever for your link.I ended up following those instructions and it looks like I've got more storage space now, which is great !!

Many Thanks guys!! It seems I can rest now & I won't need to use GParted for a while ;)

Frank B.

---

