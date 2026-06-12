---
title: "Install on RAID?"
date: 2007-03-06
forum: Absolute Beginner Talk
---

### Post by Geek33 on 2007-03-06
'Ello,

I can load Ubuntu from the CD, with the 4x burned .iso. Aside from tweaking one boot option to make my video card work, it is running from the CD perfectly. :D Yay!

I went to Install and went thru the easy steps until I got to Step 5 of 6.

I did 'Manually Edit Partition' tables and I just had one large Windows Partition (NFTS, or is it NTFS? :P) that is 149gb.

I know how to create the new partitions to set up a dual-boot Windows XP / Ubuntu system, but I'm having an issue.

My harddrives are linked in a RAID array, both 149gb, each with plenty of free space (windows and co. only using 30gb or so, but ofc the freespace/usedspace is the same on both).

When changing the partitions, I can either load /dev/sda1 or /dev/sda2, 1 is the main drive that is accessed and I think 2 is just the mirror drive.

I changed the windows partition to be something smaller, and made a 20gb Linux ext3 partition, and a 4gb linux-swap partition. I have 2gb of RAM and I read that 1.5x-2x your RAM was a safe bet for the swap partition size.

gparter or whatever the tool name is (linux noob here :P) tried to resize the big windows partition, it failed to actually resize it.

I opened the details why it failed, and it just said 'Failed to resize partition', the other 5 or 6 little steps like recognizing the drive..acessing the partition, etc, had all worked and had a nice green checkmark next to them.

I'm sure the reason it failed was because it tried to resize the partition on my main drive..and my mirror drive didn't like that..or something just messed up. 

I've looked on google about how to install Ubuntu on RAID linked drives, but all the helpfull things I've found are all terminal line commands, like fdisk and stuff..dmraid..etc.

I am really looking for a way I can keep in the Ubuntu GUI and get a visual feel on how my disk is going to be partitioned rather than screw around in Terminal, since I have almost no idea what all the commands these guides and posts list actually do in terms of partitioning.

Thanks for reading all this, heh. Hoping for a reply.

P.S. I'm not sure the type of my harddrives, or whether it's RAID0 or RAID1...I'm currently not at the computer I want to install on..but I will be soon, in case anyone needs specs. :S

---

### Post by Geek33 on 2007-03-06
'Ello,

I can load Ubuntu from the CD, with the 4x burned .iso. Aside from tweaking one boot option to make my video card work, it is running from the CD perfectly.  Yay!

I went to Install and went thru the easy steps until I got to Step 5 of 6.

I did 'Manually Edit Partition' tables and I just had one large Windows Partition (NFTS, or is it NTFS? :P) that is 149gb.

I know how to create the new partitions to set up a dual-boot Windows XP / Ubuntu system, but I'm having an issue.

My harddrives are linked in a RAID array, both 149gb, each with plenty of free space (windows and co. only using 30gb or so, but ofc the freespace/usedspace is the same on both).

When changing the partitions, I can either load /dev/sda1 or /dev/sda2, 1 is the main drive that is accessed and I think 2 is just the mirror drive.

I changed the windows partition to be something smaller, and made a 20gb Linux ext3 partition, and a 4gb linux-swap partition. I have 2gb of RAM and I read that 1.5x-2x your RAM was a safe bet for the swap partition size.

gparter or whatever the tool name is (linux noob here :P) tried to resize the big windows partition, it failed to actually resize it.

I opened the details why it failed, and it just said 'Failed to resize partition', the other 5 or 6 little steps like recognizing the drive..acessing the partition, etc, had all worked and had a nice green checkmark next to them.

I'm sure the reason it failed was because it tried to resize the partition on my main drive..and my mirror drive didn't like that..or something just messed up. 

I've looked on google about how to install Ubuntu on RAID linked drives, but all the helpfull things I've found are all terminal line commands, like fdisk and stuff..dmraid..etc.

I am really looking for a way I can keep in the Ubuntu GUI and get a visual feel on how my disk is going to be partitioned rather than screw around in Terminal, since I have almost no idea what all the commands these guides and posts list actually do in terms of partitioning.

Thanks for reading all this, heh. Hoping for a reply.

P.S. I'm not sure the type of my harddrives, or whether it's RAID0 or RAID1...I'm currently not at the computer I want to install on..but I will be soon, in case anyone needs specs. :S

P.P.S I'm not sure if this double posted, apologies if it did. :(

---

### Post by overdrank on 2007-03-06
> **Geek33 said:**
> 'Ello,

I can load Ubuntu from the CD, with the 4x burned .iso. Aside from tweaking one boot option to make my video card work, it is running from the CD perfectly.  Yay!

I went to Install and went thru the easy steps until I got to Step 5 of 6.

I did 'Manually Edit Partition' tables and I just had one large Windows Partition (NFTS, or is it NTFS? :P) that is 149gb.

I know how to create the new partitions to set up a dual-boot Windows XP / Ubuntu system, but I'm having an issue.

My harddrives are linked in a RAID array, both 149gb, each with plenty of free space (windows and co. only using 30gb or so, but ofc the freespace/usedspace is the same on both).

When changing the partitions, I can either load /dev/sda1 or /dev/sda2, 1 is the main drive that is accessed and I think 2 is just the mirror drive.

I changed the windows partition to be something smaller, and made a 20gb Linux ext3 partition, and a 4gb linux-swap partition. I have 2gb of RAM and I read that 1.5x-2x your RAM was a safe bet for the swap partition size.

gparter or whatever the tool name is (linux noob here :P) tried to resize the big windows partition, it failed to actually resize it.

I opened the details why it failed, and it just said 'Failed to resize partition', the other 5 or 6 little steps like recognizing the drive..acessing the partition, etc, had all worked and had a nice green checkmark next to them.

I'm sure the reason it failed was because it tried to resize the partition on my main drive..and my mirror drive didn't like that..or something just messed up. 

I've looked on google about how to install Ubuntu on RAID linked drives, but all the helpfull things I've found are all terminal line commands, like fdisk and stuff..dmraid..etc.

I am really looking for a way I can keep in the Ubuntu GUI and get a visual feel on how my disk is going to be partitioned rather than screw around in Terminal, since I have almost no idea what all the commands these guides and posts list actually do in terms of partitioning.

Thanks for reading all this, heh. Hoping for a reply.

P.S. I'm not sure the type of my harddrives, or whether it's RAID0 or RAID1...I'm currently not at the computer I want to install on..but I will be soon, in case anyone needs specs. :S

P.P.S I'm not sure if this double posted, apologies if it did. :(


Hi I found this thread and hope it helps. Good luck!
[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

---

