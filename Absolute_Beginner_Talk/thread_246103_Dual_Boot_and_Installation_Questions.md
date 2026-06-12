---
title: "Dual Boot and Installation Questions"
date: 2006-08-28
forum: Absolute Beginner Talk
---

### Post by Chickencha on 2006-08-28
I'm new to Linux and I've decided to take a shot at Ubuntu.  Before I install, I just want to make sure I'm planning out the installation in a good way.

Here's my setup: I'm currently running Windows XP on one hard drive.  I'm getting a second hard drive to install Ubuntu and I plan to dual boot.  I've looked at some information regarding dual booting with two hard drives and I think I have a pretty good idea of how to set it up, but I want to confirm it to be sure.

From what I've seen, people say it's a better idea to have the Ubuntu drive as the master drive and the Windows drive as the slave.  Then during the Ubuntu install I have to install GRUB and afterwards I have to edit menu.lst in a particular way (which I've found in other posts here).

Right now I'm planning to divide the Ubuntu into 3 partitions:
1) A swap partition.  I usually read that it should be 1.5 to 2 times the size of my RAM.  That's not a problem, but I'm just wondering what difference it really makes?  Will I see a performance difference if I make it larger or smaller or what?
2) An Ubuntu install partition.  I don't know how large it should be.  Does anyone have any suggestions for a minimum/maximum size?
3) An Ubuntu /home and shared data partition.  The size of this would just be the remainder of my hard drive after the other two partitions are made.

I've also read that it might be beneficial to make separate /boot or /usr partitions.  Any opinions on this either way?  And if anyone does recommend these I'd also be interested in knowing what size to make them (approximately).  Just for the record, the Ubuntu drive is huge (500 GB), so space shouldn't be an issue.

Finally, is there anything else I should know?  Can I do everything I want to using the desktop CD (as opposed to the alternative CD)?  I'd rather do things the easy way for my first Linux install, but I also want to be able to set up everything the best way I can (within reason), so I'm willing to put forth some extra effort if necessary.

Thanks in advance for any help.

---

### Post by bodhi.zazen on 2006-08-28
he he...  Easier if you overwrite windows


1. I am not sure it matters, but I would keep the windows drive master, Ubuntu slave.

2. I would install grub to BOTH the MBR and the Ubuntu partition (use the go back button during the install process). I do not think you will have to edit menu.lst.

3. Swap size will not affect performance Unless it is too small, in which case expect a significant crash. Too large -> no help. I use RAM X2, but I run some memory intense apps.

4. Ubuntu root / size = 10-15 Gb -> Minimal 5 Gb, 15-20 is more then enough.

5. I suggest a FAT 32 partition mounted as /mnt/data rather then home. You can always back /home to /data (personal preference here).

6. For what you are doing /boot or /usr partitions are not likely to be helpful.  You can use /boot like /home; it will not get overwritten if you re-install an OS. Also you need a /boot if you use XFS rather then ext3 or Rieser FS. /usr is helpful on networks to share applications (from a server).

Install away...... Welcome.

---

### Post by catlett on 2006-08-28
[http://www.ubuntuforums.org/showthread.php?t=179902](http://www.ubuntuforums.org/showthread.php?t=179902)
This is a how to for using 2 drives and not touching the windows mbr.

If you want to make it as simple as possible, keep your drives as they are. Boot into the live cd. Launch the installer by double clicking the icon. When it asks about partitions, give the entire second drive (assuming you have ubuntu as the slave) to ubuntu. If ubuntu's drive to be is installed as the slave, it will be labeled /dev/hdb.
That is it. Let the installer do what it wants. It will make 2 partition, a swap and a root.
That is the simplest way. Multiple partitions are not imperative if you are using ubuntu as a desktop. Linux's roots are unix/server based. When you have a server with multiple users, separate partitions were very important. It kept damaged contained and it also allowed you to mount critical areas as read only so there was no way to overwrite/corrupt them.
Same with boot. Years ago you had to make sure your boot folder was within a certain boundary of the drive. They made boot partitions to ensure boot would be up front. With modern hardware, it is not an issue.
I would do it the easy way first. To share data with windows, you will be able to read the data in windows and copy it over to ubuntu if you want to. It is writing to windows that is an issue. If you install the ext2 driver for windows, you will be able to read and write to ubuntu from windows [http://www.fs-driver.org/](http://www.fs-driver.org/)

---

