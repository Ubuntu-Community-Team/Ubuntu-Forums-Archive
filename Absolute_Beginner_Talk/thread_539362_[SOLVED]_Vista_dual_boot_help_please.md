---
title: "[SOLVED] Vista dual boot help please"
date: 2007-08-31
forum: Absolute Beginner Talk
---

### Post by Dave Crowhurst on 2007-08-31
I'm trying to set up a dual boot Vista + Ubuntu, and i'm following the guide at [apcmag.com]("http://apcmag.com/5046/how_to_dual_boot_vista_with_linux_vista_installed_first") site. 

My computer is an Acer Aspire 5710 with an 80gb HDD.

I went in to disk management in Vista and I have...

Hidden volume 9.76 GB (EISA Configuration) - this is some kind of Acer backup/recovery partition?
ACER (C: ) 32.51 GB NTFS (System, Boot, Page File, Active, Crash Dump, Primary Partition)
DATA (D: ) 16.18 GB NTFS (Primary Partition)
16.08 GB Unallocated - this is where I want to install Ubuntu. I created this unallocated space by skrinking down the DATA (D:) partition.

Following the instructions I boot from my Live CD (64bit version)

> Ubuntu will then load the disk partitioner to determine where it's going to be installed. Choose "Manual - use the largest continuous free space". This will automatically select the unpartitioned space we created earlier using the Shrink tool. Click Forward.

I assume that should say Choose "Guided - use the largest continuous free space"

> On the "Ready to install" screen, you'll see that Ubuntu now has enough information to commence the installation. In the summary under Migrate Assistant, it should say "Windows Vista/Longhorn (loader)". This means that regardless of whether Ubuntu found any user account to migrate, it certainly knows that Windows Vista is installed on the other partition and is aware of it. Click Install.

The problem is that it does NOT know that Vista is installed on the other partition. Under 'Migration Assistant:' it is blank, whereas on the guide it should say Windows Vista/Longhorn (loader) (/dev/sda1)

On the bottom of the screenshot in the guide it says...
> The following partitions are going to be formatted:
partition #2 of SCS|1 (0.0.0) (sda) as ext3
partition #6 of SCS|1 (0.0.0) (sda) as swap

Whereas mine says...

The following partitions are going to be formatted:
partition #5 of SCS|1 (0.0.0) (sda) as ext3
partition #6 of SCS|1 (0.0.0) (sda) as swap

So I go back to Step 4 (prepare disk space) and click manual instead.

/dev/sda
/dev/sda1 ntfs /media/sda1 10478MB 8199MB free
/dev/sda2 ntfs/media/sda2 34911MB 18400MB free
/dev/sda3 ntfs/media/sda3 17371MB 3200MB free
free space 17261MB

So i'm thinking that **sda1** is the hidden recovery partition
**sda 2** is ACER (C: ) where Vista is installed
**sda 3** is DATA (D: )
**free space** is the space i created earlier.

So I need some help please.

Why is "Windows Vista/Longhorn (loader) (/dev/sda2" not being seen?
How do I install Ubuntu in the free space without messing up anything else and so that I can dual boot.

To be specific, I want to install Ubuntu in the free space I have already created and not mess up Vista. Please please please answer this specific question (I tried asking this elsewhere and got answers that did not answer my question).

Please keep answers very simple as i'm a complete linux newb.

Many thanks.

---

### Post by eph1973 on 2007-08-31
It sounds like you have not yet actually installed Ubuntu, and you are concerned about making some sort of irreversible change to your hard drive that will somehow damage or destroy the data on your Vista partitions, and want to make sure you are doing the right procedure.  Is that an accurate description of your situation?

---

### Post by Dave Crowhurst on 2007-08-31
Exactly :)

I have created free space by shrinking the DATA D: partition (as detailed in my post) and want to use this for my install of Ubuntu.

I need to know how to achieve this please.

---

### Post by eph1973 on 2007-08-31
If you go ahead and install it according to the apcmag instructions (using the Guided - Largest Contiguous Free Space option), and as long as on that last screen it does not say that sda1, sda2, or sda3 is going to be formatted, you should be fine to continue with the install.  The warning that that screen gives you can give you pause, because it almost seems like it is going to destroy your data by reformatting your whole hard drive, but that is not the case.  That being said, as you have probably already have read, there is a very small chance something could go wrong, so to be absolutely sure, you should have a backup.  But in all actuality you should be fine, just take that leap of faith :-)

Good Luck!

---

### Post by Dave Crowhurst on 2007-08-31
Do you think I might be better using Wubi and LVPM to install Ubuntu and then move it to the free space?

---

### Post by eph1973 on 2007-08-31
First off one note on my last post...you may actually have to use the Manual option, make sure that if you use the Guided option you have the option to set the size of your swap and ext3 partitions.  If not, use the manual option.

On your other point, I am not knowledgeable about using Wubi, but there is this thread that you may find interesting:

[http://ubuntuforums.org/showthread.php?t=438591](http://ubuntuforums.org/showthread.php?t=438591)

I suggest you read that before you decide what you are going to do.

---

### Post by Dave Crowhurst on 2007-08-31
> **eph1973 said:**
> 
On your other point, I am not knowledgeable about using Wubi, but there is this thread that you may find interesting:

[http://ubuntuforums.org/showthread.php?t=438591](http://ubuntuforums.org/showthread.php?t=438591)

I suggest you read that before you decide what you are going to do.

Cheers :) I'll have a look at the video guide.

---

### Post by svalding on 2007-08-31
In the manual setup select your freespace and set the mount point to /. This will put Ubuntu on top of the list of your GRUB menu. You shouldn't have any data loss.

---

### Post by Dave Crowhurst on 2007-08-31
Thanks :) I'm going to use Wubi to install for me.

---

