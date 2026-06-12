---
title: "Linux Noob... Stuck at partitioning"
date: 2007-05-10
forum: Absolute Beginner Talk
---

### Post by jlanaway on 2007-05-10
Hi,

I am totally new to Linux - wanted to try Linux on a Dell PC which used to have an installation on SuSE 9.0 on it (not mine!), so got hold of the Ubuntu 7.04 CD.

The CD runs fine, and I can begin the install; however it quickly falls over with the following partitioning message:

Failed to create a file system: The ext3 file system creation in partition #1 of SCSI1 (0,0,0) (sda) failed.

I tried the suggestions in this post: [https://answers.launchpad.net/ubuntu/+question/5296](https://answers.launchpad.net/ubuntu/+question/5296), but to no avail.

Help - any suggestions!?

Thanks in advance,

James

---

### Post by Stickymaddness on 2007-05-10
Are you partitioning manually or automatically?

---

### Post by jlanaway on 2007-05-10
Trying to do it automatically... I haven't got a clue what I should set up manually!

---

### Post by Terl on 2007-05-10
Are you trying to set up a dual boot with windows or will Ubuntu be the only o/s on the computer?

If it is the only o/s (no windows or other operating system) just select the option in the installer to use the whole disk and it will do the rest.

Unless there is a need to manually partition... what have you tried to do?

---

### Post by hyper_ch on 2007-05-10
Manual partitioning is actually quite simple :) It just looks/sounds scary :)

Question: Do you have unpartitioned space on your harddisk?

If the answer is yes, then you can directly go create partitions :)
If the answer is no, then you will have to resize the Suse partition first :)

Once you have some free space you will need to create several partitions:

(1) SWAP --> However as you have Suse installed, there should already be a SWAP partition. You can just select to use that one :)
If there isn't a SWAP then create a new partition in the unallocated space. Make it about the double size of your ram and select as filesystem type "SWAP"

(2) Root ("/") --> depending on how much space you have this could be larger or smaller... 4 GB should be the minimum and it can go up to 20GB (depends on your liking). This is the partition where the program files, logs and stuff will be on. Select as filesystem type "EXT3" and as mounting point "/"

(3) Home ("/home") --> There should all the rest of your unallocated space go to. This partition will store the user (config) files such as the documents, music and stuff... Select as filesystem type "EXT3" and as mounting point "/home"

If you are unsure, then fire up during the live-session IRC (XChat, Konversation, whatever client) and join the #ubuntu or #kubuntu or #xubuntu channel on the irc.freenode.org server. People will help you there directly :)

---

### Post by jlanaway on 2007-05-10
I only want Ubuntu to be on the PC - I have selected the whole disk, and asked Ubuntu to take care of the partitioning... and this is the error I get.

All I've done is put the LiveCD in, boot off it and enter the basic info (location, timezone etc.).

I haven't tried manually partitioning, because I'm not sure what to wet... All I want to do is have a clean install - I'm more than happy for all existing data to be destroyed!

J

---

### Post by hyper_ch on 2007-05-10
Well, go with manual partitioning anyway :) Then you just delete first all partitions and you start making a swap, a root and a home one. The auto-install won't make a seperate home partition (and it's very much recommended to have one).

If you select manual partitioning you will see it's not really that difficult :) Just remember SWAP is about twice the size of ram (of course with 2 GB ram you can leave it at 1 GB swap [if you don't hibernate]) , root should be at least 4 GB... 10 GB is a good size for it... and rest ist home...

Have a try and you will see it's really simple :)

---

### Post by jlanaway on 2007-05-10
OK - had a go at manual partitioning... 2GB Swap, 10GB / and the rest /home.

Now I get this message:

Do you want to resume partitioning?:   The attempt to mount a file system with type swap in SCSI1 (0,0,0) , partition #1 (sda) at none failed.  You may resume partitioning from the partitioning menu (Go Back) / (Continue)

I'm restart the PC and the LiveCD and try again from scratch....

---

### Post by Carlos Santiago on 2007-05-10
Just do the following:
1) With any windows program that you are used to use (*), delete a partition with 6 GB to 10 GB
2) Leave the partition unformated
3) Run the liveCD and the installer
4) Select _use all free space_ when asked.

NOTE: Do NOT select use entire disk, and your windows will be untouched

(*) For example Fdisk, Partition Magic or Disk Manager. The last one come with windows, and you can find it at C:\windows\system32\diskmgmt.msc or C:\winnt\system32\diskmgmt.msc.

---

### Post by hyper_ch on 2007-05-10
Can you make screenshots of the settings for the individual partitions?

---

### Post by maniacfox on 2007-05-10
I am suffering from exactly the same problem as the OP. I installed standard Ubuntu 7.04 on my system without any problems, but the PC is a bit old so I though I'd switching to Xubuntu to make things a bit quicker. I boot from the live CD  fine, but then I get this problem installing.

I have tried automaitcal partitioning, manual partitioning, using all of the disk, using just the free space, you name it, nothing works. Maybe it doesn't like something on the disk  from my original Ubntu install.

I am resigned to the fact that I will have to wipe the HDD completely, maybe format it with NTFS or something weird and then try again.

---

### Post by jlanaway on 2007-05-10
All - thanks for your help... I seem to have got it working :)  

here's what I did:

1. Start up clean from the live CD
2. Disable automount of removable drives as described in this post: [https://answers.launchpad.net/ubuntu/+question/5296](https://answers.launchpad.net/ubuntu/+question/5296)  
3. Run the Gnome Partition Editor (System... Administration... GNOME Partition Editor) and delete all current partitions; create new swap, root and home partitions.
4.  Launch the installer and select manually configure partitions, checking that the newly created partitions are correctly configured.
5. So far... so good!

Thanks again for all your help!  I'm sure I'll have more questions soon!

James

---

### Post by hyper_ch on 2007-05-10
If the partitioner works, it's not that difficult to manually partition the drive, right? ;)

---

