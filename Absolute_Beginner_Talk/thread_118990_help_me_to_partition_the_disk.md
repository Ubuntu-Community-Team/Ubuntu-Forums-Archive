---
title: "help me to partition the disk"
date: 2006-01-18
forum: Absolute Beginner Talk
---

### Post by ubunlilluz on 2006-01-18
hi,
i want to improve the partions set of my hd seen that now i got the automatin one (only /  and swap)

So i want to share the space i left for linux (135 GB) in:

/ 5GB
boot 100MB
var 700 MB
log 200MB
swap 550MB (i got 256MB of ram)
home the rest

All with ext3.

Do you think it's a good sharing?
Moreover, in the installation procedure it asks me if these partition must be primary or logic, at the end or begin. I know the difference between primary and logic partitions, but not knowing what these partitions do (i'm new with linux) i can't say what is better.
So can you suggest me how to do share the disk and with which partition (primary, logic, end, begin)

thanks

---

### Post by lha on 2006-01-18
[QUOTE=ubunlilluz]hi,
i want to improve the partions set of my hd seen that now i got the automatin one (only /  and swap)

So i want to share the space i left for linux (135 GB) in:

/ 5GB
boot 100MB
var 700 MB
log 200MB
swap 550MB (i got 256MB of ram)
home the rest

All with ext3.

Do you think it's a good sharing?
Moreover, in the installation procedure it asks me if these partition must be primary or logic, at the end or begin. I know the difference between primary and logic partitions, but not knowing what these partitions do (i'm new with linux) i can't say what is better.
So can you suggest me how to do share the disk and with which partition (primary, logic, end, begin)

thanks[/QUOTE]

First question: What kind of improvement are you expecting to achieve by partitioning your drive in a different way?

The other question: Why do you want to have separate /boot and log? (Do you mean you want /var/log on a separate partition?)

These questions should not to be taken as critic against your planned partitioning. I'm just pointing out the things you want to do and I don't understand why. Maybe my questions are rhetorical; if you know the answer there's probably no need for answers. About other partitions, 5GB for root and 550MB for swap sound good to me and I like to keep /var on a separate partition. (Mine is 1.6GB but it could be smaller.)

While your partitions are in use, it doesn't matter if partitions are primary or logical. Only difference I can name is if you have to repartition your hd it does matter how primary and extended partitions are layed out on your hd. Also the order of logical partitions does matters, too.

---

### Post by ubunlilluz on 2006-01-19
[QUOTE=lha]First question: What kind of improvement are you expecting to achieve by partitioning your drive in a different way?

The other question: Why do you want to have separate /boot and log? (Do you mean you want /var/log on a separate partition?)

These questions should not to be taken as critic against your planned partitioning. I'm just pointing out the things you want to do and I don't understand why. Maybe my questions are rhetorical; if you know the answer there's probably no need for answers. About other partitions, 5GB for root and 550MB for swap sound good to me and I like to keep /var on a separate partition. (Mine is 1.6GB but it could be smaller.)

While your partitions are in use, it doesn't matter if partitions are primary or logical. Only difference I can name is if you have to repartition your hd it does matter how primary and extended partitions are layed out on your hd. Also the order of logical partitions does matters, too.[/QUOTE]

My target is to have the partitions that make easier to change distro. The best would be to cancel the os without loosing my data. All guides i've found in internet say that is better to share in different partition. I have no idea why, and i posted this question in many forums and everybody know that the guides say that but, as me, they have no idea why.

---

### Post by Sef on 2006-01-19
as long as you have a separate home partition, you can reinstall and not lose your data.  Mine are

ubuntu fat32

/           reiserf

/home reiserf

swap

and i have reinstalled my system with my data intact.

---

### Post by Luke771 on 2006-01-19
If your goal is to store data, then reinstall the OS and get your data to stay there, I would suggest you partition like this: make a primary 10GB Ext3 partition att the beginning of the free space, and that one is the partition that has to be mounted as / during OS install; then you make a logical 1GB Swap partition at the beginning of the free space remaining after making the primary partition, and then you make a logical Ext3 partition as big as the remaining free space; this will be the partition where you store the data you dont want to lose when you install another distro or reinstall the same distro or whatever.
This way you can simply delete your OS partition, make a new partition, install the OS on it and still have your data on the logical partition.
That's as good as fool safe (no offense :-))
If you are setting up a dual boot sytem, consider making the last logical partition FAT32 instead of Ext3; that way it will be accessible by Windows as well, no point in doing that if you plan to use Linux only.
in short:
1 primary Ext3 10 gig to be mounted as /
1 swap 1 gig 
1 logical Ext3 (or FAT32 if you use both linux and windows) to be mounted as /media/whatever if you want it to show up on your desktop or /whatever if you want it to be acsessible as a subdirectory in the "File Sistem" directory ("directories"=folders, more or less) but not to show up directly on the desktop.
Notes: you can change these settings later by editing the /etc/fstab file, and of course you can change the directory name /whatever to ... well, whatever you like :-)

---

### Post by lha on 2006-01-19
[QUOTE=ubunlilluz]My target is to have the partitions that make easier to change distro. The best would be to cancel the os without loosing my data. All guides i've found in internet say that is better to share in different partition. I have no idea why, and i posted this question in many forums and everybody know that the guides say that but, as me, they have no idea why.[/QUOTE]

Partitioning can be used to achieve many different goals. For example /tmp on a separate partition prevents temporary files from filling up your root partition. On a server, /var is used to store logs, mails and news. Putting /var to its own partition on such a system is is useful, as it prevents spam and whatever to flood the whole filesystem. On a desktop in home use those are not big threats so you don't necessarily need separate partitions for /tmp, /var or /var/log. I like to keep /var (and /tmp) on a separete partition to prevent fragmentation. (I've symlinked /tmp to /var/tmp.)

/boot is useful on really old computers with bigger hard drives. Some bioses can't boot partitions that exceed 1024 cylinder boundary. If you haven't had that kind of issues, I'd recommend **not** to make a separate boot partition.

The three partitions I discussed above contain files specific to your current installation and are not of interest if you reinstall, so they wont be of use for you. What I recommend you is to make /, swap and /home. Basically, the things you want to keep from current installation if you decide to reinstall or change distro, are on /home. / will contain files for your current installation and swap is there to do its own job.

There reason why separate /home makes reinstallation easier is atleast Debian (and Ubuntu, maybe others too) want to erase all files from root partition when installing. Ubuntu installer refuses to install over an existing installation. If you had only one partition, you'd have move all personal files somewhere and format root partition. (Maybe removing all system files would do, don't know.) With separate /home partition you can just wipe out / and do a fresh install keeping your files on /home unharmed. (Maybe you'd want to delete some config files from your ~.)

From your previous posts I got the idea you are dual booting, maybe Windows. If that is the case, making a primary partition for / and logical partitions for swap and /home would be my choice. (I'd put grub on boot sector of root and not on mbr, but you probably have installed grub on mbr already. Ubuntu installs it there by default. This isn't of that much importance, but It would keep Windows bootable even without any Linux installation.) Make all partition in the beginning of free space.

PS. You dont want to make /home fat32 or any other fat either. Fat doesn't support file permissions or ownerships and is not fault tolerant. Use a native Linux filesystem.

---

### Post by ubunlilluz on 2006-01-20
thanks to everybody.
I'll make so 3 partitions:
/         10GB  primary ext3
Swap   1 GB 
home   the rest logic ext3

to continue the discussion i post what i found in the howto [http://www.tldp.org/HOWTO/Partition/requirements.html#number](http://www.tldp.org/HOWTO/Partition/requirements.html#number) :

4.3. File Systems
4.3.1. Which file systems need their own partitions?

Everything in your linux file system can go in the same (single) partition. However, there are circumstances when you may want to restrict the growth of certain file systems. For example, if your mail spool was in the same partition as your root fs and it filled the remaining space in the partition, your computer would basically hang.

/var

    This fs contains spool directories such as those for mail and printing. In addition, it contains the error log directory. If your machine is a server and develops a chronic error, those msgs can fill the partition. Server computers ought to have /var in a different partition than /. 
/usr

    This is where most executable binaries go. In addition, the kernel source tree goes here, and much documentation. 
/tmp

    Some programs write temporary data files here. Usually, they are quite small. However, if you run computationally intensive jobs, like science or engineering applications, hundreds of megabytes could be required for brief periods of time. In this case, keep /tmp in a different partition than /. 
/home

    This is where users home directories go. If you do not impose quotas on your users, this ought to be in its own partition. 
/boot

    This is where your kernel images go. See discussion above for placement on old systems. 

bye

---

### Post by chimera on 2006-01-20
A question related to partitioning but not big enough to start another topic for it:

Why would you need any more partitions than /, /home and /swap?

---

### Post by aysiu on 2006-01-20
[QUOTE=chimera]
Why would you need any more partitions than /, /home and /swap?[/QUOTE] You don't, really.

---

### Post by KrazyPenguin on 2006-01-28
[QUOTE=chimera]A question related to partitioning but not big enough to start another topic for it:

Why would you need any more partitions than /, /home and /swap?[/QUOTE]

I set my system up like this: (for 80GB Hard Drive)

1. 5GB 	Linux1 --- Used for main Linux Distro.
2.Primary 5GB 	Linux2 --- Used for secondary Linux Distro.
3.Primary 5GB	Linux3 --- Used for testing distros.
4.Extended    1GB Linux-Swap --- Used as a shared swap partition between the distros.
5.Extended  50GB  Home --- Used as a shared home directory for 3 installed Linux distros.
6.Extended  10GB Music --- Used for music storage

So for your basic home user you just need /, /home/ and /Swap.
But eventually you will get curious and want to try another distro and you will want to install it to your harddrive.  So I find having 3 root partitions of 5GB each is good for testing purposes, and they all share the /home partition.
I think 1 GB Linux-Swap might be too much since I have 1GB ram now and my computer has never used it, even with 10 things going at once.
With only512MB my computer did use swap!!!
They 10GB Music Storage isn't really necessary and I might not include it with my new harddrive.  Did I mention I bought a new harddrive yet???
Just bought it and it is a Western Digital 200GB 7200 RPM 8M.
I want to make this a primary but was debated with myself whether to include a boot partition or not.
Seems like it doesn't really matter but if I did how big would I make it??
Thanks

---

### Post by lha on 2006-01-28
[QUOTE=KrazyPenguin]I set my system up like this: (for 80GB Hard Drive)

1. 5GB 	Linux1 --- Used for main Linux Distro.
2.Primary 5GB 	Linux2 --- Used for secondary Linux Distro.
3.Primary 5GB	Linux3 --- Used for testing distros.
4.Extended    1GB Linux-Swap --- Used as a shared swap partition between the distros.
5.Extended  50GB  Home --- Used as a shared home directory for 3 installed Linux distros.
6.Extended  10GB Music --- Used for music storage

So for your basic home user you just need /, /home/ and /Swap.
But eventually you will get curious and want to try another distro and you will want to install it to your harddrive.  So I find having 3 root partitions of 5GB each is good for testing purposes, and they all share the /home partition.
I think 1 GB Linux-Swap might be too much since I have 1GB ram now and my computer has never used it, even with 10 things going at once.
With only512MB my computer did use swap!!!
They 10GB Music Storage isn't really necessary and I might not include it with my new harddrive.  Did I mention I bought a new harddrive yet???
Just bought it and it is a Western Digital 200GB 7200 RPM 8M.
I want to make this a primary but was debated with myself whether to include a boot partition or not.
Seems like it doesn't really matter but if I did how big would I make it??
Thanks[/QUOTE]

I'd make it 0 bytes. (No, it's not a typo.) I'm usually against having a separate boot. You don't use LVM or raid and you don't seem to have any problems booting from partitions beyond 8GB so there's hardly any gain to you on a separate partition for boot. On the other hand, having an extra partition adds clutter in your system and complicates some things a bit.

I guess the answer you want is
```
du -sh /boot/
```
It shows how much space is needed to store the files on your /boot. A little extra room would be nice, in case you add another kernel or so.

---

