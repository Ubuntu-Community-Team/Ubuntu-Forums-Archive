---
title: "Dual Hard Drives"
date: 2007-05-05
forum: Absolute Beginner Talk
---

### Post by eyesrglazed on 2007-05-05
Okay. I have two IDE hard drives : a 40GB and a 120GB. I want to install Ubuntu on the 40, and set the 120 up as a slave that I can save my files on.

Is there any way to set this up while installing the OS, like in the partitioner? If so, how exactly would I do that (e.g. what type of filesystem, etc.)

---

### Post by freebird54 on 2007-05-05
Yes, you can do this.  NO, there is no set of instructions - because there are so many possibilities :)  To do this, use the manual partitioning mode when setting up the system. (it is still in a GUI, and quite easy to understand.  The hard part is deciding what you want the end result to be.  Here are a couple of possibilities:

You could set up the 40 as
1 GiB swap (or 1.5 times your RAM)
10 GiB /  (root)
29 GiB /home

and second drive /data   

 OR

1 GiB swap
39GiB /  (root and home combined)
and second drive all for data.

The choices are endless :)

Option A is useful, as it allows a re-install without messing up your /home directory in the future.  Option B is easier to understand.  However, option C can be almost anything you imagine...
[http://www.psychocats.net/ubuntu/index](http://www.psychocats.net/ubuntu/index)
I suggest using the (default for Ubuntu) ext3 file system for reliability whatever setup you end up with.

Other considerations - you might want to leave some space on the second drive for other OS versions.  Perhaps you want to try out Kubuntu, or Xubuntu, or a new update - without risking your 'working' setup.  Perahps you might like to leave a space for a partition where you store backups (images of your working system perhaps)  in a convenient manner.

Here is a link that might help with the decisions:

[http://ubuntuforums.org/showthread.php?&t=282018](http://ubuntuforums.org/showthread.php?&t=282018)

and another:

[http://www.psychocats.net/ubuntu/index](http://www.psychocats.net/ubuntu/index)

There are a number of other interesting things covered in the second one.

Hope this helps!

---

### Post by eyesrglazed on 2007-05-05
So when I'm looking at the manual partitioning screen, I see things like bootable flags, if the drive should be logical/extended, etc. Can anyone tell me roughly what I should set this stuff as?

---

### Post by freebird54 on 2007-05-05
There is a limit of four primary partitions on any 1 drive.  If your plans will exceed this, then you need to create an extended partition as 1 of the four.  Within this extended, you can have more.  Think of an extended partition as a container.

Most of the other 'flags' etc are for specialized circumstances, which you should not run into.  For instance, if you have more than 1 Windows partition, there had better only be 1 visible (not hidden) at a time, or Windows chokes.  Not an issue with linux. You don't need Linux to be on a primary, nor do you need to flag one as the 'active' partition.  Not relevant for the most part.

If you want to post what partition scheme suits you, we could give an 'order of operations' if you want - but it is pretty simple really.

Is there anything currently on the drives that you wish to keep?  Or are we starting with a clean slate?  That is really the only thing that matters, because any mistakes otherwsie have no consequences - you just redo the partitions till you have them the way you want them....

---

### Post by eyesrglazed on 2007-05-05
Clean slate.

Here's the options I need to set for the partitions :
Type : Primary/Logical
Size
Location : Beginning/End
Use as : ext3, etc.
Mount point

I'd like to set it up as follows :
38GB for main OS (Ubuntu)
2GB for swap
120GB for other files (2nd Hard drive)

So, there's the partition sizes. I'm not entirely sure what the type should be for each. I know all of the partitions should be ext3. The mount point? No clue, except I believe the first partition, which contains the Ubuntu installation, should be /, right?

---

### Post by freebird54 on 2007-05-05
Depending on your memory, you might want to set your swap as the first one.  (if you have less than 1Gb, that's the fastest ple for it).  When you select type as swap, it will automatically set the filesystem for you.  For so few partitions, you might as well kepp them all primary.  Select ext3 as the filesystem whenever it is NOT swap.  Yes, set the main (36) as / .  You will need to allow the fresh partitions to be fotmatted, but that is just a matter of ensuring that the checkbox beside each partition is marked in for formatting when you assign them their names/types after creation during the install.

Fire away - it is surprisingly straightforward really...

---

