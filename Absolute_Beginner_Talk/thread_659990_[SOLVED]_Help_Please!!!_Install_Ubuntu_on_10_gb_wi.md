---
title: "[SOLVED] Help Please!!! Install Ubuntu on 10 gb win partition"
date: 2008-01-06
forum: Absolute Beginner Talk
---

### Post by childofstrings on 2008-01-06
Hey guys,
Basically I set up a 10GB partition in windows to install Ubuntu on. The rest of my harddrive is currently being used as storage for movies and music. I made a backup of the important files from this drive, but none the less, I'd rather not loose my 80 or so GBs of stuff on that drive.

So, I go into the install application and select the "manual" option. I get a table with all my drives and partitions.I click on the partition that I want to use and it gets greyed out/highlighted. But when I click "Next" for the next step in the install process I get the following error message...

No root file system is defined.

Please correct this from the partitioning menu.

What am I doing wrong??? I went into GParted and everything looks ok and I can identify my partition there as well so I dont know what I missing. GParted doesn't give me any options to mount or any of that. The only options GParted gives me are to flag, disklabel, or see the information on my partitions/drives.

Please halp!!! I need to install ubuntu on this drive in order to get into windows again because of grub loader. Many thanks for help in advance!

---

### Post by stump138 on 2008-01-06
when you do the partitions you need to designate 1 "/" (no quotes) and 1 "swap" (again no quotes).  You need to make sure that you designate the bulk of that 10 gig to "/" (root file system) and 1-2 gig for the "swap."

I would go with 8 gig for "/" and 2 gig for "swap" but that is really only a matter of preference:)

---

### Post by childofstrings on 2008-01-06
> **stump138 said:**
> when you do the partitions you need to designate 1 "/" (no quotes) and 1 "swap" (again no quotes).  You need to make sure that you designate the bulk of that 10 gig to "/" (root file system) and 1-2 gig for the "swap."

I would go with 8 gig for "/" and 2 gig for "swap" but that is really only a matter of preference:)

Ah thanks for the info!

But umm...whats the best way to go about doing this? Heh, forgot to mention Im a total ubuntu/linux newb.

---

### Post by stump138 on 2008-01-06
When you are going through the manual partition table, it should ask you to designate or name the partition (think like c: for windows)  There should be a checklist/checkbox
(trying to pull it out of memory)that allows you to do so.  I do this using the alternate cd.  There is a set of screen shots which shows this for a server set-up(numbers will be different, concept the same) [here]("http://www.debianadmin.com/ubuntu610-edgy-lamp-server-installation-with-screenshots.html")

good luck :)

---

### Post by childofstrings on 2008-01-06
> **stump138 said:**
> When you are going through the manual partition table, it should ask you to designate or name the partition (think like c: for windows)  There should be a checklist/checkbox
(trying to pull it out of memory)that allows you to do so.  I do this using the alternate cd.  There is a set of screen shots which shows this for a server set-up(numbers will be different, concept the same) [here]("http://www.debianadmin.com/ubuntu610-edgy-lamp-server-installation-with-screenshots.html")

good luck :)

Ah...unfortunately Im still a little confused...am I doing this in GParted? Or during the install procedure?

---

### Post by stump138 on 2008-01-06
during the install procedure sorry :)

---

### Post by taurus on 2008-01-06
Here's an easy way.  From gparted on the LiveCD, partition 9GB (as a partition) out of that 10GB and the last 1GB (another partition) formats it as swap.  And when you install, use the Manual option when you get to the partition part and tell the installer to use that 9GB as / (it means you need to mount it as / since the default is probably something like /media/sda2) and format it as ext3.  The installer should pick up the last partition as swap so you don't have to do anything about it.  Otherwise, mount the 1GB as swap.

---

### Post by childofstrings on 2008-01-06
> **stump138 said:**
> during the install procedure sorry :)

Hmmm I really wish there was a way that I could post a screenshot to show you but I dont see very many options when I am in the install procedure, and I certainly dont see anything letting me name parts of my partitions. The only option it really gives me is to "Edit" partitions, and the only thing that seems to do is resize them, which I really dont want to do,

---

### Post by childofstrings on 2008-01-06
> **childofstrings said:**
> Hmmm I really wish there was a way that I could post a screenshot to show you but I dont see very many options when I am in the install procedure, and I certainly dont see anything letting me name parts of my partitions. The only option it really gives me is to "Edit" partitions, and the only thing that seems to do is resize them, which I really dont want to do,

OK correction,

Under the "Edit Partition" Menu it gives me the following 3 options.

1.) Specify a New Partition Size (Dont want this)

2.) Use as (FIle system, currently have it set at FAT 32)

3.) Mount Point: 

Under the "Mount Point" it gives me two options  "/dos" or "/windows"

Is that what Im supposed to use to specify the root?

---

### Post by stump138 on 2008-01-06
That 10 gigs that you have set aside for your ubuntu install is going to need to be chopped up for the / and the swap partitions, so you shouldn't worry about doing so.  By looking at the mount point information you are headed in the right direction :)

You'll want to carve that 10 gig into 2 partitions, one with the mount point / and one with mount point swap. You should format / as ext3.

LOL hope this is starting to make some sense:)

---

### Post by wheredidrealitygo on 2008-01-06
You're going to want to set that as Ext2, or Ext3 (most Ubuntu users I would think have it set as ext3), it's a much better filesystem for Linux.

also, after you do that, you can delete the /dos (or /windows) mount point option, and manually set the mount point to be "/", which stands for your root filesystem, similar concept to the C: drive in windows.

---

### Post by Pogeymanz on 2008-01-06
Under the mount-point menu you should just be able to type in "/" and format the other smaller one as "swap" as opposed to "ext3", which is what your "/" should be.

---

### Post by childofstrings on 2008-01-06
> **stump138 said:**
> That 10 gigs that you have set aside for your ubuntu install is going to need to be chopped up for the / and the swap partitions, so you shouldn't worry about doing so.  By looking at the mount point information you are headed in the right direction :)

You'll want to carve that 10 gig into 2 partitions, one with the mount point / and one with mount point swap. You should format / as ext3.

LOL hope this is starting to make some sense:)

Okkkk....its finally starting to make some sense to me lol. Im working on it GParted as we speak. Im splitting my 10GBs into two partitions, the first is 1 GB, the second is 9GB. I will format the 9GB as "ext3" and the 1GB as "linux-Swap". Does this sound correct?

---

### Post by stump138 on 2008-01-06
yep yep :) the 9 gigs of ext3 should be mounted as "/"

:)

---

### Post by childofstrings on 2008-01-06
Thank you all so much for your help!!! This is finally starting to make sense to me and I dont feel like such a newb.

Thanks again! Hopefully I'll have this all sorted out in a few minutes. I'll post again if I get stuck or confused.

P.S. I love this forum :D

---

### Post by The Cog on 2008-01-06
The easy way is to just leave the 10G unpartitioned, and tell the installer to use the available unused space. Then it will make its own partitions as it likes. That way you don't have to worry about partition types, mount points etc.

---

### Post by childofstrings on 2008-01-06
> **The Cog said:**
> The easy way is to just leave the 10G unpartitioned, and tell the installer to use the available unused space. Then it will make its own partitions as it likes. That way you don't have to worry about partition types, mount points etc.

Actually for some reason it wasn't letting me install with my 10GB Partition as I had it set up in Windows. I think I needed to manually go through with GParted and change the partition from FAT32 to ext3 in order for the installer to even recognize that it was the partition I wanted my "/" on.

Well I learned a little about Linux file systems and root and swap through this experience so while it was a bit of an **** pain, it was definitely a learning experience in the end!

---

