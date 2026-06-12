---
title: "[SOLVED] Error installing gutsy on sony vaio vgn-s3HP"
date: 2008-03-17
forum: Absolute Beginner Talk
---

### Post by Andavane on 2008-03-17
Hello
am installing gutsy on a sony vaio vgn-s3hp... thought it was going well, then have the message that it had failed, possibly owing to a dirty cd (I had prior to this checked the cd for faults -- it was fine). On try again to bot in to windows I got the message that an operating system had failed to boot.

Then, forcing the laptop to spin down I booted from the CD to attempt another install.

Now I have the message

> Resize operation failure. An error occurred while writing the changes to the storage devices. The resize operation is aborted. OK. 

Now I have clicked OK and it is scanning discs again.

Next, the Prepare partitions section reads as follows:

> 
/dev/sda1 ntfs /media/sda1 format? 7501mb
/dev/sda2 ntfs /media/sda2 format? 27965mb
/dev/sda5 ntfs /media/sda5 format? 67205mb
/dev/sda6 ntfs /media/sda6 format? 86615mb
/dev/sda7 swap....................format? 4445mb
/dev/sda2 ntfs /media/sda2 format? 87185mb

Underneath this are listed 3 boxes, saying

> Edit Partition             Delete Partition              Undo changes to partitions

and underneath that:

>  You need to specify a partition for the root file system (mount point "/") with a minimum size of 2 GB and a swap partition of at least 256 MB. You may also set up other partitions if you wish.

Under this it says it is step 4 of 7 and there is cancel option, forward and back.

I seem to have gotten into rather deep water.

I will abort the laptop installation and try again tomorrow.
As I am in the dark, I'd very much appreciate help!

Am typing this on my desktop machine.

Regards

John

---

### Post by duncan.hawthorne on 2008-03-18
dont panic.

if one of those partitions is empty (ie the one you were trying to install ubuntu on)
then format it as ext3 mount it as / ( / means where ubuntu goes)
continue, ubuntu should install and windows should be back too

do you need to resize any of the partitions, if not, just choose one and go

---

### Post by Andavane on 2008-03-19
> **duncan.hawthorne said:**
> dont panic.
Thank you ;)

> if one of those partitions is empty (ie the one you were trying to install ubuntu on)
then format it as ext3 mount it as / ( / means where ubuntu goes)
continue, ubuntu should install and windows should be back too

do you need to resize any of the partitions, if not, just choose one and go
When I returned to the PC, with trepidation (!) I tried again.
This time it didn't ask me to create a mount mount, but just went ahead and installed.
I think I must have botched something, as Windows XP seems to have vanished --although I admit I'm not entirely sorry for this.

It is working and the responses are lightning fast compared with what it used to do.
There are some issues --such as some partitions appearing to have vanished, but the machine is working and that is good.

Thanks.

The other issues can be posted separately.

Kind regards

John

---

### Post by lswest on 2008-03-19
what may have happened is that you chose "use entire disk" at the partitioning menu of the installer, which means XP is gone, and it's now an Ubuntu only PC, don't worry, it's happened to us all at some point in time.  If you're not in desperate need of XP you can probably do with WINE, or running it in a VM from ubuntu.

---

### Post by Andavane on 2008-03-20
> **lswest said:**
> what may have happened is that you chose "use entire disk" at the partitioning menu of the installer, which means XP is gone, and it's now an Ubuntu only PC, don't worry, it's happened to us all at some point in time.  If you're not in desperate need of XP you can probably do with WINE, or running it in a VM from ubuntu.
You are right, that is what happened...
But it may have been a blessing in disguise! 
Let's see.
As i said, there are some issues, which will now list in a separate post.
The impressive thing is that the system is "Up-and-Running".
Regards
John

---

