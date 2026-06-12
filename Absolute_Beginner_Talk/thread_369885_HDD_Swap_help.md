---
title: "HDD Swap help"
date: 2007-02-25
forum: Absolute Beginner Talk
---

### Post by GermanMafia on 2007-02-25
Completely new to linux, don't know what i'm doing, I have 3 hdd's in my computer, 2 IDE's and 1 Sata. The sata is all my music and movies, I had quite a bit of free space so I made a new partition, then found out I needed some swap so I made another one. I selected the wrong swap one and 100 gb of my hdd is now swap and unaccesible to my Windows. I can't reformat it to NFTS or else I'll lose everything (really surprised I didn't lose everything in the change to swap), so how can I change my swap to the 5 gb i set for it, without losing the 100 gb of data on my harddrive? Everything was somehow preserved and now my linux has been treated to all my music and whatnot.

Also, I can see that it's there under Windows (in the system menu, it identifies it as a drive but because it's swap it won't let me grab stuff from it), it's just I can't get any information on the drive. 

Thanks in advance.

---

### Post by moshuptrail on 2007-02-25
Are you saying that when you boot windows, you can see the drive, but not access any data?
If so, how do you know the data is still there?

Linux rarely needs the swap area (unless you are running a lot of large programs) so it probably has not yet over-written anything on the swap partition.

Linux determines which drive is which in the file called /etc/fstab.  It might be useful to post the contents of that file and let's have a look.

---

### Post by GermanMafia on 2007-02-25
When I boot into windows, I can see the drive under the device manager tab, it just tells me Western Digital 160 SCSI drive - no volume information or anything. When I boot into linux, under HDA5 (or whatever the root is) all that stuff i can just see, it's under HDA5. I know for a fact it's not in the root because I can see the root, and it's in a 20 gb partition I made for it. So what happens if I deswap file the swap file? It won't revert back to NFTS correct? What format is swap file in?

Thanks.

---

### Post by ed-j on 2007-02-25
sayhkasfhouiryuregt;lp.l

Oooops? Sorry, k'bd damage!

---

### Post by GermanMafia on 2007-02-26
Wha? 

Anyone got anything?

---

### Post by ed-j on 2007-04-07
As a Novice, I'd probably say i386. Definitely not FAT32 though.

---

### Post by freebird54 on 2007-04-07
The partition type is stored in the MBR - so if you can get that changed back without reformatting anything, you should be OK.  Personally - I would try to image what's there before trying to make any more changes.  Is there anywhere on another drive big enough to hold an image file of this current partition?

---

### Post by jerryrw on 2007-04-07
Really need to see the results of:

sudo fdisk -l

and the current fstab

You may I repeat may be able to force a mount on that partition to a Linux directory and retrieve the files.  But need the fdisk results to really know.

---

