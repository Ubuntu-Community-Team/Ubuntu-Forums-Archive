---
title: "Trying to set up dual boot system and am stuck"
date: 2005-01-21
forum: Apple PPC Users
---

### Post by kadymae on 2005-01-21
Okay, got Ubuntu loaded up and running. 

Decided I want to make a dual boot system.  Grabbed OS X disk #1, wiped my drive, and partitioned it into 12 and 6 gig portions.  Just got done installing OS X on the 6 gig partition.  It's alive and well.

Grabbed Ubuntu disk and started the install process.  It wants to take over the whole disk.

Despite poking about in the FAQs I can't find instructions that I understand about how to make Ubuntu only use the 12 gig partition.  And the guide in the partitioning program doesn't really explain that. (Me=n00b).

Can somebody *please* tell me, in *excruciating* (think "how would I explain this to grandma") detail what I need to do?

Or, if you know of a tutorial/FAQ aimed at the n00b, point me there.

I have *never* set up a dual boot system before, so I'm going to need some serious hand-holding on this.

Thanks.

---

### Post by Brian McConnell on 2005-01-21
[QUOTE=kadymae]Okay, got Ubuntu loaded up and running. 

Decided I want to make a dual boot system.  Grabbed OS X disk #1, wiped my drive, and partitioned it into 12 and 6 gig portions.  Just got done installing OS X on the 6 gig partition.  It's alive and well.

Grabbed Ubuntu disk and started the install process.  It wants to take over the whole disk.

Despite poking about in the FAQs I can't find instructions that I understand about how to make Ubuntu only use the 12 gig partition.  And the guide in the partitioning program doesn't really explain that. (Me=n00b).

Can somebody *please* tell me, in *excruciating* (think "how would I explain this to grandma") detail what I need to do?

Or, if you know of a tutorial/FAQ aimed at the n00b, point me there.

I have *never* set up a dual boot system before, so I'm going to need some serious hand-holding on this.

Thanks.[/QUOTE]


this is a "B" plan -- it will require re-parting and re-installing mac OS. If you use Apple's disk utility you could try to format the free space as ext3 or ext2 and then see if Ubuntu merely takes over existing linux format partitions. I've not run into this problem with installing Ubuntu, but I may have already had existing Linux part's for it to just take over. Good luck......

---

### Post by Viro on 2005-01-21
You could try manually partitioning the 12 GB space yourself, since AFAIK there is no way to prevent Ubuntu from taking over the hard disk when using the automatic partitioning mode.

You will need to set up 3 partitions. The first is a NewWorld boot partition that is required for booting (yes, it is PowerPC specific). This partition is normally under 1 MB in size and I think it automatically calculates the size for you so you needn't worry.

Next, set up your root partition. This will take the majority of your free space (11 GB perhaps?). The root partition should have a ext3 or reiserfs as a filesystem and "/" as the mount point. 

Lastly, you need a swap partition. This will take the remainder of free space. When creating the partition, change the way the disk is used from "Format this partition" to "Use as swap". Finish creating the partition, write changes to disk and you're done!!

Sorry it isn't more detailed as I don't have the installed booted up here and all of it is off the top of my head.

---

### Post by kadymae on 2005-01-21
Quoth Viro:  "You could try manually partitioning the 12 GB space yourself"

And that is *exactly* what I have no clue how to do and can't find instructions on that which  make sense to me.

Okay, so I know I need to select  the manual partion option, but after that what do I do to create boot, root and swap?  (And what kind of cthuluspeak names to I have to give them, because I know calling them boot, root, and swap would, y'know, actually make sense and be easy, therefore it will not be done that way in Linux.)

thanks.

---

### Post by juart on 2005-01-21
Hi - I’m also an absolute linux newbie. The following worked for me.

After booting from the CD you choose as required:
language
location
keyboard
detect hardware (automatic)
scanning CDrom (automatic
loading installer components (automatic)
detecting network (automatic)
configuring network (automatic)
enter hostname (you enter a name here) 
detecting disks and hardware (automatic)
start partitioner (automatic)

partition disks screen - select manually edit partition table then scroll to the partition you wish to use which I believe in your case is the 12 gig partition then hit return (be careful to select the correct partition here). Then select delete the partition. This should now show as FREE SPACE.
Select the FREE SPACE and  hit return then select automatically partition free space. The partitioner will do the rest and create the appropriate 3 partitions for boot, swap, and /.

You should then select finish partitioning and write changes to disk. Installion should then procede to completion. Let us know if this works.

Good Luck,

---

### Post by Viro on 2005-01-21
Sorry my post wasn't as detailed as it could be. I don't have the installer up and running and I installed Ubuntu quite some time ago.

For the names of the partitiion, you can call it anything. What's important is the "mount point" and "/" is the mount point of the root directory. The swap partition doesn't have a mount point or name, and neither does the NewWorld boot partition.

But juart has posted some promising looking instructions. I think you should try them first.

Btw, you kadymae who hangs out occasionally on OSNews?

---

### Post by kadymae on 2005-01-21
[QUOTE=juart]

partition disks screen - select manually edit partition table then scroll to the partition you wish to use which I believe in your case is the 12 gig partition then hit return (be careful to select the correct partition here). Then select delete the partition. This should now show as FREE SPACE.
Select the FREE SPACE and  hit return then select automatically partition free space. The partitioner will do the rest and create the appropriate 3 partitions for boot, swap, and /.

You should then select finish partitioning and write changes to disk. Installion should then procede to completion. Let us know if this works.

Good Luck,[/QUOTE]

Will give this a try as soon as I get home from work tonight.  

Thanks.

---

### Post by kadymae on 2005-01-21
[QUOTE=Viro]Sorry my post wasn't as detailed as it could be. I don't have the installer up and running and I installed Ubuntu quite some time ago.[/quote]

I know, but I appreciate that you took a stab at it.  :)

> 
Btw, you kadymae who hangs out occasionally on OSNews?

Yup.  Reading the reviews over there is what convinced me to give Ubuntu a try.  

And, despite the fact that there's lots of room for improvement in Ubuntu and Linux as a whole, Ubuntu blows the doors off of YDL.

---

### Post by kadymae on 2005-01-22
Juart --

SNOOPY DANCE SNOOPY DANCE SNOOPY DANCE!

My install is in progress as I type this.  Worked like a charm.

(And I'm jotting down a bunch of notes to build a little webpage -- you'll get your props.)

---

### Post by Viro on 2005-01-22
Well done! Good job on getting it to work. :)

---

