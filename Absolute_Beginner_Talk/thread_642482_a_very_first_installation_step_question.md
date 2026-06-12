---
title: "a very first installation step question"
date: 2007-12-16
forum: Absolute Beginner Talk
---

### Post by babel on 2007-12-16
[FONT="Verdana"][COLOR="Navy"]Hi.

I just tried to install an old Ubuntu 5.10 by CD on a new computer.
For now, I want to keep the current Windows installation & add the Ubuntu in a separate partition.
I know the Ubuntu CD can do this, but I can't figure out how.
I want to install Ubuntu withOUT removing Windows (at least for now !).  

I have also just sent a request for a Ubuntu 7 CD to be sent by mail.

Can you help me with these very first steps.

Thank you,

Babel.[/COLOR][/FONT]

:confused:

---

### Post by LaRoza on 2007-12-16
Are you using Vista? If so, don't try it.

I would recommend waiting for the new CD, which will work better on your computer.

-EDIT I just remembered, that version had a live and install cd, if you have the live cd, you can't install.

---

### Post by Ub1476 on 2007-12-16
If using Vista, open its partition manager and create a few gigs for Ubuntu. Upon installing choose it to use "largest free space available" (something like that).

If using any earlier version, simply use Ubuntus partition editor you get there when you follow the instructions) and give Ubuntu a few gigs by dragging the bar up/down. 

Remember not to give Ubuntu so much space that it will overwrite Windows

Good luck!

BTW, I also recomend you to wait for Ubuntu 7.10. At least considering you're on a new PC with new hardware!

---

### Post by mcduck on 2007-12-16
Even if it's old computer, you should get a new Ubuntu version. The support for 5.10 has already ended, which means that it's program repositories are closed. You won't be able to get any programs for 5.10 any more..

---

### Post by babel on 2007-12-16
I am using XP . 
I have both the install & the live 5.10 CD's.
My concern is that the jacket to the Ubuntu 5.10 CD tells me that the default installation will delete Windows (which I am not quite ready to do) but the advanced installation will not.  
My problem is that I see no option for advanced insstallation and I don't want to erase Windows by moving into the default installation.

BTW, I only ordered Ubuntu 7 today so it will be quite some time until it arrrives.  Should I wait ?  Should I download it instead ?

---

### Post by LaRoza on 2007-12-16
If you can download it, you will be doing yourself a favour. You will only need the one CD, but you can get the alternative disk, which isn't live.

The options are worded very well on the install disk so you won't have trouble, but remember to back anything up, just in case something happens.

---

### Post by mcduck on 2007-12-16
> **babel said:**
> I am using XP . 
I have both the install & the live 5.10 CD's.
My concern is that the jacket to the Ubuntu 5.10 CD tells me that the default installation will delete Windows (which I am not quite ready to do) but the advanced installation will not.  
My problem is that I see no option for advanced insstallation and I don't want to erase Windows by moving into the default installation.

BTW, I only ordered Ubuntu 7 today so it will be quite some time until it arrrives.  Should I wait ?  Should I download it instead ?

There is no 'advanced installation'. You just need to chose 'manual partitioning' or 'resize windows to make room for Ubuntu' at the partitioning stage of the installer.

Juts make sure you don't use the 'use whole disk'-option. That is the one that would delete Windows.

(The actual options may have slightly different names, it's been a long time since 5.10 and I really can't remove the exact names any more..)

---

### Post by babel on 2008-01-12
OK  -  I downloaded a copy of Ubuntu 7.10.  It would not do much more than show me a moving orange bar.  So I waited for the 7.10 CD to arrive.  I now have the 7.10 CD and today I tried it.  I did not have much luck.  I tried the option where I left Windows in place.  The program told me that I do not have enough contiguous space for Ubuntuu. 

What I did was this:  Install  >  I set language & time zone, etc   >   partitioner  >  Guided - use the largest continuous disk space  >  "Failed to Partition the Selected Disk  -  This probably happened because the selected disk or free space is too small to be automatically partitioned".

I find this difficult to understand.  There is 74.5 GB on the hard drive of the computer I am trying to install Ubuntuu on.  Windows XP is already installed.  Of the 74.5 GB, 65.8 GB is free space.   If I look at how the disk is set up - using disk defragmenter - I see that most of the disk written to is crowded together on the left side of the pictogram with a small bar written to in the center.  That looks as if there is about 25 GB of continuous free space on each side of the thin bar.

So why no "continuous free space"?

What should I do ?

I suppose I can reinstall Windows, hope it is all crowded together on one end, and then try to install Ubuntuu again.  I still want Windows XP on this machine (at least for now).

Any suggestions ?

---

### Post by wolfen69 on 2008-01-12
choose "manual" partition and use the 7gb space for ubuntu.

---

### Post by oldos2er on 2008-01-12
Have you run defrag from Windows? If not, you should. Then try again with the install.

---

### Post by babel on 2008-01-13
I've run Defrag multiple times.  The small band of written-to hard drive in the center of the drive gets a bit smaller, moves a tiny bit, but is still in the center.

OK - I chose Manual installation.  
I get a window that is called "**Prepare Partitions**"

/dev/sda1        ntfs       /media/sda1        80015 MB        unknown

free space                                                8 MB

On the bottom I get the choices of "New Partition Table" and Undo Changes to Partitions".

If I choose "New Partition Table"  I get a window called "Create new empty partition table on this device" 
You have selected an entire drive to partition.  If you proceed with creating a new partition table on the device, then all current partitions will be removed"

Now this is not what I wish to do.
I wish to keep my present Windows XP installation, at least for now.

What would you advise I do next to create a partition for Ubuntuu that does not remove Windows XP, when "Guided - use the largest continuous free space" does not work?

---

### Post by oldos2er on 2008-01-13
> **babel said:**
> 
What would you advise I do next to create a partition for Ubuntuu that does not remove Windows XP, when "Guided - use the largest continuous free space" does not work?

 Buy another hard drive, and install Ubuntu to it.

---

### Post by babel on 2008-01-19
Sorry  -  I was away for a week.

Short of buying a second hard drive, which i am not sure I can figure out how to install, does anyone have any ideas as to how I can convince Ubuntu to install in either of the two >20 GB blocks of free space on my hard drive?  

I am really stuck at this very first step.

---

