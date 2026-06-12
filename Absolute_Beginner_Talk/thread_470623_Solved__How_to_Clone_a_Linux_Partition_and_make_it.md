---
title: "Solved:  How to Clone a Linux Partition and make it bootable ..."
date: 2007-06-11
forum: Absolute Beginner Talk
---

### Post by cwmoser on 2007-06-11
The following is a summary of what folks on this forum helped me with.

I come from a Windows XP world and I had certain "perceptions" that hindered my understanding how to clone a Linux partition.  From a Windows perspective, when I wanted to clone a partition or drive, I used Norton Ghost --- so, I thought that was the best way for Linux.  Then I had trouble with making the partition bootable.

Well, Ghost was the wrong choice as it created an ext2 file system where Ubuntu uses an ext3 file system.

Also, I had some misunderstandings about grub.  Grub can be perceived as *two* parts -- one part resides on the boot drive and the other is the menu that appears on the screen allowing you to select which partition.  If you have a dual boot Windows XP/Ubuntu configuration like I do, the bootable part of Grub is going to be your C: or hd0 drive.

I have 5 main partitions on my 2 hard drives:  XP, a backup image of XP via Norton Ghost, Ubuntu 6.10, Ubuntu 7.04 in a 20GB partition, and now an image of my Ubuntu 7.04 in an 80GB partition.  The reason for this apparent mess is because I believe in backups and fallback options in case I screw something up.

So, if you are searching for a way to clone your Ubuntu to another partition like I was wanting for either backup or that you need more disk space, check out this procedure I documented:

Clone Linux Partition

Don't need Norton Ghost use the command cp  -a instead
You need to boot off the CDROM so that neither the source partition nor the target partition is mounted.
Procedure:
Assume in the following example that we are copying /dev/sdb3 to /dev/sda6:

1.Boot Ubuntu CDROM
2.Click on Terminal in order to get command prompt
3.Run fdisk to create partition:
sudo  fdisk  /dev/sda
p			<- display partition table
n  then  p	<- create a new primary partition
	NOTE:  If you have Windows XP, you can use it to create the partition – but
		don't format it.
4.sudo  mkfs  -t  ext3  /dev/sda6		<-- make file system, format it
5.mkdir  /tmp/sdb3					<-- mount points
6.mkdir /tmp/sda6
7.sudo  mount  -t  ext3  /dev/sdb3  /tmp/sdb3
8.sudo  mount  -t  ext3  /dev/sda6  /tmp/sda6
9.cd  /tmp/sda3					<- go here to start copy
10.sudo  cp  -a  *  /tmp/sda6			<- copy relative to this


Now setup grub and the menu.lst file so you can boot the new partition.

In this example, we put in an entry in menu.lst like this:


#Proposed Ubuntu 7.04 on /dev/sda6:
#------------------------------------------
title		Ubuntu, kernel 2.6.21.1 on /dev/sda6 80GB Partition 
root			(hd0,5) 
kernel		/boot/vmlinuz-2.6.21.1 root=/dev/sda6 ro quiet splash 
initrd		/boot/initrd.img-2.6.21.1 
quiet 
savedefault 




Now this creates a copy of your Ubuntu in another partition but it is not bootable yet.
To make it bootable, you can use Grub like the following:


Grub

Boot Loader 		= on the boot drive
/boot/grub/menu.lst	 = on the Linux Partition

Note:  If you need to install Grub, boot the Ubuntu CDROM, click on the Terminal, to get a shell prompt.

sudo  grub
grub>  find  /boot/grub/stage1		<-- find all Linux partitions
grub>  root  (hd1,2)				<-- select the partition that has
							    /boot/grub/menu.lst
grub>  setup  (hd0)				<-- drive that boots – usually hd0
grub>  quit


Edit /boot/grub/menu.lst

#Proposed Ubuntu 7.04 on /dev/sda6:
#------------------------------------------
title		Ubuntu, kernel 2.6.21.1 on /dev/sda6 80GB Partition 
root			(hd0,5) 
kernel		/boot/vmlinuz-2.6.21.1 root=/dev/sda6 ro quiet splash 
initrd		/boot/initrd.img-2.6.21.1 
quiet 
savedefault 

Set the default variable in /boot/grub/menu.lst so that the default is as you prefer.



Thanks to all you nice folks who helped me understand this.

Carl

---

### Post by southernman on 2007-06-12
Very nice post, Carl. People like you are what make the Ubuntu Community a great one!

---

### Post by MenZa on 2007-06-12
Wonderful. As I always tell people to when they write a wonderful HowTo, I suggest you post it on the [Ubuntu Community Wiki](http://help.ubuntu.com/community/).

---

