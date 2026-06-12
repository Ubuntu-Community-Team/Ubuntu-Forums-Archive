---
title: "partition help and dual boot"
date: 2007-07-20
forum: Absolute Beginner Talk
---

### Post by grantuser on 2007-07-20
Hey guys. I'm sure this has been asked before, so I apologize.

I'm using Gparted right now to partition my hard drive in order to dual boot Windows98 and Ubuntu (alternative install CD). I've resized the Windows partition and created a new one for Linux.

What file system should I be using for the Ubuntu one? I made it the same as the Win98 one which is FAT32. Is this okay? And when I created it the program asked if I wanted the Linux partition to be the "primary partition" or the "extended partition". I chose primary. Will this cause problems dual booting the two operating systems?

Any general help in dual booting the two would be appreciated. How do I set the things up? When I turn my PC on will it simply ask what OS I want to boot in or what?

Thanks!

-Grant

---

### Post by ddrichardson on 2007-07-20
I'd use ext2 or ext3 - they're the default. Primary and extended partitions don't really matter.

As for dual booting as long as Windows is installed first you'll be fine.

---

### Post by kngunn on 2007-07-20
I would partition the drive into Win98 (*shudder*) and FREE SPACE.  Then load Ubuntu and partition the free space within the installer to provide swap space and a root partition (/).  You can get fancier, but unless I'm running a server I don't.  Set it to be EXT3.

The Ubuntu installer will install GRUB for you to manage the dual-booting.  Then you'll get a screen when you boot to let you pick Win98 or Ubuntu.

---

### Post by rajeev1204 on 2007-07-20
Linux uses the ext3 filesystem so u cant use fat32 to install it.

Need to basically select a / partition and a swap

Also good if u define a separate /home partition .

/ and /home will be ext3 . Swap will be twice the size of ur ram and doesnt need to specify a filesystem for it .


Ubuntu can read and write to FAT 32 easily so u can view ur windows partitions as well

---

### Post by grantuser on 2007-07-20
Okay thanks. I'll use ext3 for the new Ubuntu partition. Will the Ubuntu alternate install CD still give me GRUB to manage dual booting?

What is a swap partition? Do i have to have one?

Thanks for the replies!

-Grant

---

### Post by ddrichardson on 2007-07-20
Yes grub is installed during installation.

Swap partitions are used to page memory to a file when you run short of physical memory. Under Linux, a swap file of the at least the same size as your physical memory, or double it (depending on who you ask).

---

### Post by grantuser on 2007-07-20
So what partitions do I create? So far it looks like this in Gparted--- Should I change something? I have 192MB RAM.

/dev/hda1                    4.41 GB size

New Partiton #1          5.08 GB size

Unallocated                  54.91 MB size

---

### Post by ddrichardson on 2007-07-20
Delete the new partition. With only 192 Mb I'd go for atleast 640 Mb Swap and the rest for the root partition. You can get fancy but personally I only allocate other mount points on servers.

---

### Post by wak_maximus on 2007-07-20
sorry to interrupt..i just want to ask something..
i already a windows xp user..and now i'm interested in using linux..but i want to use both operating system..about partition the hard disk..i already have 2 partition..50% on each partition..am i need to re-partitioning my hard disk or i can use the one i have?

-wak-:confused:

---

### Post by buuntuu! on 2007-07-20
ok, before playing around, read aysius great [guide]("http://psychocats.net/ubuntu/index.php") covering all the questions you might have as an ubuntu-beginner, there is also a good illustrated example of a dual-boot-install (alternate)
have fun!!

@ wak_maximus: when installing you can choose the partition you want to install to, make sure you choose the right one! ;)

---

### Post by wak_maximus on 2007-07-20
thanks a lot..
about choosing the partition..i read some article that windows must be install on first partition..

is that right??

---

### Post by buuntuu! on 2007-07-20
yes. if you already have xp installed, you're fine. if you plan to reinstall xp as well, install FIRST xp and THEN ubuntu for a troublefree installation.

---

### Post by ddrichardson on 2007-07-20
its not so much where windows is rather the order you install the os's. WIndows overwrites the MBR so install it first.

---

### Post by wak_maximus on 2007-07-20
so..i just empty the one partition and install ubuntu on it right?
i'm sorry ddrichardson but i'm not familiar with a computer terms like MBR and ext1,ext2,ext3..
sorry...+_+

---

### Post by ddrichardson on 2007-07-20
You don't need to physically create any partitions before installation, just resize the Win98 one and leave the unallocated space. Reboot and check Windows still boots.

Backup any important data (just in case).

Run the live CD and then the install icon from the desktop. Answer the questions and when the partioning screen pops up select manual config.

Create a swap partition of approx 640Mb. Create an ext2 partition using the rest of the free space. Select format on the ext2 and swap ONLY. Select edit on the ext2 partition and choose "/" for the mount partition. For the windows partition you can choose a mount point like /media/windows so you can access that drive from Ubuntu.

Follow out all the other steps as they default and reboot.

I don't mean to appear ignorant to new users but a quick google for MBR gives a description on the second hit. Ext2 and Ext3 are the most common Linux file system types as stated in a previous post. ;-)

Hope this helps.

---

### Post by wak_maximus on 2007-07-20
[IMG]http://img264.imageshack.us/img264/9426/feistydual12xc2.png[/IMG]

so the mount "/" is to name like windows..just like in my windows xp OS --> C:/windows
is it like that??:confused:

Grub is Multiboot boot loader..if i not using this software, am i still be able to switch between windows and ubuntu??

it's ok..you already help me a lot..thanks:)

---

### Post by ddrichardson on 2007-07-20
Kind of. The file system starts at / and everything else is put where it needs to be from here.

For example from the screenshot you'll have an NTFS (Windows) partition available, and the file system will see it as being a file in /media called hda1.

Where as Windows allocates letters to each drive, Linux just sees them as being another file on the root system.

---

### Post by wak_maximus on 2007-07-20
Grub is Multiboot boot loader..if i not using this software, am i still be able to switch between windows and ubuntu??

---

### Post by ddrichardson on 2007-07-20
No you wont be able to. There are other methods to switch OS at boot time - but use Grub.

---

### Post by wak_maximus on 2007-07-20
[IMG]http://img519.imageshack.us/img519/9278/feistydual18cv5.png[/IMG]

this screen appear during installation process..if i want to use grub, what i need to do?i need to download this GRUB software or...???and Grub is to be install to MBR..am i need a specific steps on doing this??:confused:

---

### Post by ddrichardson on 2007-07-20
No - click "OK"

---

### Post by wak_maximus on 2007-07-20
thanks a lot..looks like i have a lot to learn..

---

### Post by ddrichardson on 2007-07-20
So is it all working then?

---

### Post by wak_maximus on 2007-07-20
not yet..:)
i just gathering information on HOWTO..
need to really careful in this thing...

out of the topic..if i use windows and ubuntu..can i still using internet on windows??probably on Ubuntu also??
because some hardware like networks card may not suitable with Ubuntu right? so if i can use internet in either one of this OS, it still be alright for me though..

---

### Post by ddrichardson on 2007-07-20
All being well your windows installation will be fine so if you can use the net now you will be able to afterwards.

---

### Post by wak_maximus on 2007-07-20
if i using desktop cd..i need to reboot my computer and go to BIOS settings to start installation..is that right??

---

### Post by ddrichardson on 2007-07-20
Yes you need to enable the cd drive as the first boot device.

---

### Post by wak_maximus on 2007-07-20
[IMG]http://img379.imageshack.us/img379/2128/partitioning5bu8.png[/IMG]

I think this is my partitioning plan..
so..how much space i need to allocated on "/" (ext3)?
for swap is approx 640mb..
and the rest i can give it on /home (ext3)..

*sorry for my english..:(

---

### Post by ddrichardson on 2007-07-20
I don't remember what size your drive is, but an average install is approx 2.5 Gb so you'll need to go for about 4 Gb on the / partition to allow for expansion.

---

### Post by wak_maximus on 2007-07-20
sorry for not mentioned my drive size..it's 60Gb..
so i just need to place around 4Gb..
thanks..

---

### Post by ddrichardson on 2007-07-20
Personally I'd give it a bit more just in case. I would just allocate everything to / unless you are going to have an awful lot of users data to preserve.

---

### Post by wak_maximus on 2007-07-20
[IMG]http://img379.imageshack.us/img379/2128/partitioning5bu8.png[/IMG]

**This last dual-boot scenario is my favorite now that I know about FS-Drive, which is a small program that allows Windows to read from and write to Ext3 partitions. So FAT32 can go out the window&#8212;one less partition to worry about and none of the limitations of FAT32 (no file permissions, lots of fragmentation, and a file size limit of 4 GB).**

this is the article i read about..if i put all space in / , am i still able to access it from windows?
and i also deal with picture editing software, games, song files..which plan is much better you think?

---

### Post by ddrichardson on 2007-07-20
Yes with efs2explorer or such like.

---

