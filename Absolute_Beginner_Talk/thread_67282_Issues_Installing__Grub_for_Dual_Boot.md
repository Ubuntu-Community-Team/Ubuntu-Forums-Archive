---
title: "Issues Installing / Grub for Dual Boot"
date: 2005-09-19
forum: Absolute Beginner Talk
---

### Post by ddemers on 2005-09-19
I am at the '[!!] Partition Disks' part of the Installation... and ran into a wall.  It doesnt show me my current partition layout of my harddrive. Currently I have a harddrive like this

numbers are approx.
Partition 1:  Windows XP 60gigs
Partition 2:  RedHat 9.2 20gigs.
Partition 3:  Empty 20gigs
Partition 4:  NTFS 20gigs for files.

at the Partition screen it shows:

IDE1 mastger (hda) - 120.0 GB ST3120024A ]  (*,) 
 

From screenshots of how to install I see that all the partitions are showing fine, why is my Hard drive not?  I go back to the install menu, click on Install Grub... and it just brings me back to this screen.

Anyone have any hints?

Any

---

### Post by SilentCacophony on 2005-09-19
Did you perform any partitioning yet?

It should have asked you if you want to *erase entire disk* or **manually edit the partition table**. In your case, maually editing is the choice to make, else you wipe the entire drive for an ubuntu-only install.

The grub setup should only be gotten to after you set up the partitions, and it will auto-detect other bootable partitions.

---

### Post by ddemers on 2005-09-19
[QUOTE=SilentCacophony]Did you perform any partitioning yet?

It should have asked you if you want to *erase entire disk* or **manually edit the partition table**. In your case, maually editing is the choice to make, else you wipe the entire drive for an ubuntu-only install.

The grub setup should only be gotten to after you set up the partitions, and it will auto-detect other bootable partitions.[/QUOTE]

  
No I didnt perform and partioning yet. I do have a ghost image of my XP installation (Which was done a few days ago), but I would rather complete a dual boot install without having to revert back :).

It did ask me if I wanted to wipe the disk, so I choose Manual install, but my issue is that its not showing me the currently partition layout of the hard drive, just showing the 120 lump sum...  Basically I already have a partition I want to use, thus I am confused as to why I have to partition it again.  

I guess my fear is that I dont want to ruin my current partion layout for Windows.  After reading your reply I am thinking that I can just make a partion of 30 gigs or so, then later down the road it will show my current partion layout and I can pick which one to install Linux on?

[B]Edit:  Should also mention that when I choose to Manually edit, I go to the next screen where it prompts me to 

-COnfigure Software Raid
-Configure the Logical Volume Manager
-Guided Partitioning (which are just options to whipe my hd)
-Help on Paritioning

-> IDE master (hda)

When I choose the hard drive, which I am assuming its to partition,I go to the next screen  which tells me 'You have selected an entire device to patition.  If you proceed with creating a new partition table on the device, then ALL current partitions will be removed.  [/B]

---

### Post by SilentCacophony on 2005-09-19
> Edit: Should also mention that when I choose to Manually edit, I go to the next screen where it prompts me to

-COnfigure Software Raid
-Configure the Logical Volume Manager
-Guided Partitioning (which are just options to whipe my hd)
-Help on Paritioning

-> IDE master (hda) 

It should have listed any existing partitions directly after that bottom line. I can't imagine why it wouldn't, unless the mbr or the disk had been wiped.

That would be where you tell it how it should mount each partition, and which filesystem to use. Usually you'll neead a root partition and a swap partition, at least, and I'd think 20-30 gigs would be quite enough, as mine is 4 gigs.

Anyway, perhaps you should verify the contents of the HD with something else before continuing.

---

### Post by ddemers on 2005-09-19
[QUOTE=SilentCacophony]
Anyway, perhaps you should verify the contents of the HD with something else before continuing.[/QUOTE]


I am corrently booted into Windows XP, coping my Ghost image from my NTFS file partion to my external USB Drive encase I break everything...lol

I went to the Disk Management console and it shows 

C:  53.19GB NTFS
58.60 Free Space (I removed the RedHat partition as it didnt work)
D:  19.53GB NTFS

-- I could have sworn I only had a 120 gig hard drive... the totals dont had up... umm.  Ive never see this before.

---

### Post by SilentCacophony on 2005-09-19
That's good. I feared you somehow wiped your drive.

I'd use whatever windows partitioner you have to partition the empty space into ext3 (or any filesystem, really, but don't forget a swap partition.) That way, the mbr will be updated, possibly uncorrupting it if that was the problem.

Perhaps run a check on the disk. 

Try the install again, and hopefully it was a fluke. I've not heard of anyone having that problem before.

---

### Post by ddemers on 2005-09-19
I ran the install CD on my notebook and it showed the proper partition order.  I am currently copying all the files from my NTFS partion to my external so I can boot to a floopy and just use FDISK to clear everything, then I will reimage my Windows install and hopefully I can get up and running.  Thanks for the help, thought I was going crazy :P

---

### Post by rajsarkar on 2005-09-20
[QUOTE=ddemers]I ran the install CD on my notebook and it showed the proper partition order.  I am currently copying all the files from my NTFS partion to my external so I can boot to a floopy and just use FDISK to clear everything, then I will reimage my Windows install and hopefully I can get up and running.  Thanks for the help, thought I was going crazy :P[/QUOTE]
 As advised by SilentCacophony, you may again proceed with installation. This time you may get the partition table in order. I am also surprised, never heard of such problem. Let us know what you see during installation this time. 

-Raj

---

