---
title: "Ubuntu installation not installing GRUB"
date: 2006-06-09
forum: Absolute Beginner Talk
---

### Post by bkuhns on 2006-06-09
I'm pretty much a complete n00b to linux, I've tried Redhat9, Fedora Core 2, Mandrake 10.1, but never really delved into it much and ended up getting rid of them. I've been playing around with Ubuntu's LiveCD and it makes me want to give linux another shot. My problem is, unlike all the other distros I've installed... I can't get it to boot.

I have two hard drives, one 200gb SATA (sda) and one 300gb SATAII (sdb). SDA contains windows XP and Vista, and SDB is where I installed ubuntu. But after installing ubuntu, it just boots straight to windows. I got rid of the vista boot loader assuming it was just being greedy and refused to see grub or something. No luck... now my computer just boots straight to XP without giving any options.

Finally after playing around with this for a few hours last night, I got "GRUB on NT" working, but I have no idea how to configure it to find my Ubuntu installation. Through trial and error, I finally found a linux kernel installed on hd(1,2) and according to the Ubuntu LiveCD's partition manager, my ext3 partition is at partition #3 of /dev/sdb. I've tried pointing the root= GRUB option to /dev/sdb3 in menu.lst like so:
> title Linux
root (hd1,2)
kernel /vmlinuz root=/dev/sdb3 ro but the linux kernel gives me the following error:
> VFS: Cannot open root device "sdb3" or unknown-block(0,0)
Please append a correct "root=" boot option Ok, so that doesn't work...

So I looked around and came across GAG. I downloaded it, burned it to a CD-R and got it installed. But it only detects my windows installation and doesn't list linux at all. I'm wondering if this is because linux is not on the primary drive...

Sorry for the long post, but I wanted to put out all the information I know so that maybe someone could spot the problem and help me out. I'm completely lost... I have ubuntu installed, but it's kinda floating out in space and I need to anchor it down somehow. PLEASE HELP :)

---

### Post by Bloch on 2006-06-09
Apologies for answering as a non-expert, but it will keep your question close to the top.

If you have two hard drives one will be master and one will be slave. You can only boot off the master disk, as I understand things.
[http://www.seagate.com/support/kb/disc/troubleshoot_master_slave.html](http://www.seagate.com/support/kb/disc/troubleshoot_master_slave.html)

The easiest solution is to install ubuntu on the master disk (alongside windows) and partition the second disk in whatever way suits you - i.e. part FAT for sharing files, and part ext 3 for your /home directory.

I see on google that it might be possible to set GRUB to boot from the slave disk. It's up to you whether you want to investigate this further.

---

### Post by Bloch on 2006-06-09
Here's a thread that might help you:

[http://www.ubuntuforums.org/showthread.php?t=184947](http://www.ubuntuforums.org/showthread.php?t=184947)

---

### Post by bkuhns on 2006-06-09
Thank you for the help. Though the specific solutions/links you provided didn't fix my problem, it did get me thinking. I didn't mention an extra 80gb IDE drive that's hooked to my computer... it seems that after I took the IDE drive out, deleted the ubuntu installation on my slave SATA drive, and reinstalled it to my primary SATA (which has windows on it), everything works fine :D  Thanks again for the help

---

### Post by brentoboy on 2006-06-09
sdb3 means "third partition" on the "b" (second) SATA drive.

if you installed ubuntu on the entire drive, it is probably sdb1 and the swap partition is probably sdb2 or sdb5

as long as grub is loaded to the master boot record, it can boot to any of the primary partitions (the first 4 partitoins) on any drives, but grub has to be installed on the master boot record (the boot record on the first hard drive)  either sda or hda depending on whether you used ide cables to connect, or the thin red sata cables (you should undoubtably be using sda)

hope that helps

I bet that you installed grub on /sdb instead of the master boot record becuase it seemed safer  --- I cant bank on that, but it is a common mix up.

---

### Post by bkuhns on 2006-06-09
brentoboy, My assumption is that having the IDE hard drive (which was registering as hda) was the issue. As soon as I took it out and reinstalled Ubuntu, everything works (and is where I'm posting from now)

now just to see if i can get a better resolution than 1024x768 (already downloaded updated nvidia drivers with no luck) and how to access my ntfs partitions...

---

### Post by brentoboy on 2006-06-09
you will have a hard time getting the ntfs partitions to give you more than read only access.  (there should be instructions all over explaining how to use fstab to autoload ntfs partitions, so I wont go into it)

even if you find some instructions for mounting it read write, and they "work"  -- I wouldnt do it,  it is any thing but dependable.

what I do on my dual boot "work" laptop (that has to have windows, becuase I develop windows apps for a living), I have a 16GB fat32 partition that I use for files that should be available from both OSes.  then, the system and win apps are on the ntfs drive, and "My Documents" are on the fat32 drive.

fat32 is a published format, so it is reliable in linux.  ntfs is not published, so it is "works for me" "oh no, I lost everything" in linux.

---

### Post by brentoboy on 2006-06-09
[QUOTE=bkuhns]
now just to see if i can get a better resolution than 1024x768 (already downloaded updated nvidia drivers with no luck) [/QUOTE]

what is the driver info in xorg.conf

do this...
```

gedit /etc/X11/xorg.conf

```

find the section that talks about your vidio card, mine looks like this...

```

Section "Device"
	Identifier	"ATI Technologies, Inc. M22 [Radeon Mobility M300]"
	Driver		"ati"
	BusID		"PCI:1:0:0"
EndSection

```

what does your's say?

---

### Post by bkuhns on 2006-06-09
Thanks for the recommendation. I was trying to avoid that but now that I think about it... that wouldn't be all so bad afterall. I thought NTFS is supposed to be faster, but anything in my "my documents" folder in windows doesn't really need blazing speed benchmarks to open an MP3 or JPEG in good time. I think I'll give the shared FAT32 partition idea a try.

---

### Post by brentoboy on 2006-06-09
avoid making a LARGE fat32 partition.

16GB is as big as I would go, but my brother is happy with 32GB  the larger the drive, the more potentially waisted space, becuase in fat32 entire sectors are allocated at once, and the larger the drive, the larger the sector.  a FAT table only allows for so many sectors.

---

