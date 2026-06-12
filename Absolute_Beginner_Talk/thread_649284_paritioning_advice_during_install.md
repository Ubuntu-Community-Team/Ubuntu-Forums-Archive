---
title: "paritioning advice during install"
date: 2007-12-24
forum: Absolute Beginner Talk
---

### Post by ubantunovice on 2007-12-24
I read the "complete guide to instalation in Ubuntu" on this forum but could not find the answers I need so I hope someone will advise me.

This is a desktop with a single HD that has 3 existing partitions
C: XP system partition (NFTS)
E: data partition (NFTS)
F: data partition (NFTS)
about 50G free space at the end

I want to install Ubuntu 7.1 as a dual boot alongside the XP partitions. When I tried to install Ubuntu from the live CD, I got as far as the step for partitioning (I think it is step 4) and then was stumped:

- I obviously did not want the default step to use the entire disk!

- The option to use the "guided install using free space" sounded good but seemed to want to take up the entire free space which seems a waste. It did not "guide" me as to how much to use of the available space.
I wish the "guided install using free space" option did indeed ask me how much of the free space to use and for what for, but it did not and after asking me about my name it warned me it was going to write the partitions so I backed out.

- The 3rd option to manually partition then seemed the one I needed but the nomenclature stumped me.  Here is what I was presented with for the /dev/sda drive:

/dev/sda1     (type nfts)   (mount point /media/sda1)     size 13472
/dev/sda5     (type nfts)   (mount point /media/sda5)     size 21040
/dev/sda6     (type nfts)   (mount point /media/sda6)     size 38420
free space                                                                        size 50001

I obviously want to put the new Ubuntu partitions in the free space, but how many partitions should I create there and of what size each?

Don't I need one partition for Ubuntu, another for Home and still another for swap?  If so how much should I give to each in a starter trial Ubuntu system?

Thanks.

---

### Post by LinuxIsInnovation on 2007-12-24
You need 2 partitions, 1 for Home and other for swap. The root is the / mountpoint. First format the home partition in ext3 filesystem and then edit it to assign the / mount point. Format the small swap partition in swap filesystem.

---

### Post by LaRoza on 2007-12-24
> **ubantunovice said:**
> 
- The 3rd option to manually partition then seemed the one I needed but the nomenclature stumped me.  Here is what I was presented with for the /dev/sda drive:

/dev/sda1     (type nfts)   (mount point /media/sda1)     size 13472
/dev/sda5     (type nfts)   (mount point /media/sda5)     size 21040
/dev/sda6     (type nfts)   (mount point /media/sda6)     size 38420
free space                                                                        size 50001

I obviously want to put the new Ubuntu partitions in the free space, but how many partitions should I create there and of what size each?

Don't I need one partition for Ubuntu, another for Home and still another for swap?  If so how much should I give to each in a starter trial Ubuntu system?

Thanks.

Create a large EXT3 partition as / (root) and a small one (about 512 MB) as swap.

---

### Post by Pogeymanz on 2007-12-24
Most people do three partitions, as you mentioned. Make the swap 1 to 2 times the amount of RAM your machine has. Home can be probably half of your free space if you are going to load it up with music and movies.

Some people also have /usr and /tmp as different partitions. /tmp as 256 MB - 512 MB and /usr as 10 gig.

I'm no authority, though.

---

### Post by chris4585 on 2007-12-24
like the other guy said, there should be two new partitions, the ext3 for your home / which ubuntu will install on that, then the swap you need maybe 512mbs of space for that, think of that as virtual ram

---

### Post by ubantunovice on 2007-12-24
Thank you both.  What should be a reasonable size for the Home partition? (I'll make the swap one 512 as advised).

Are the partitions "root" and "home" synonymous?

Thanks again for the rapid reply.

---

### Post by Boelcke on 2007-12-24
Besides all that good advice, I'd say that my Ubuntu root partition never gets over 10 gigs.  In fact, 10 is excessively large, but I keep doing it anyway.  I'd:

/ = 10 gigs
/home = 20 gigs
swap - 2x your memory
plus, you might want to make a /shared partition with the remaining 10 or so.  Depending on what you're doing, or who you talk to, there's some issue with sharing space between XP and ubuntu on an NTFS drive.  I'd make
/shared = 10 gigs
as a drive that's accessible between both operating systems.

---

### Post by LaRoza on 2007-12-24
> **ubantunovice said:**
> Thank you both.  What should be a reasonable size for the Home partition? (I'll make the swap one 512 as advised).

Are the partitions "root" and "home" synonymous?

Thanks again for the rapid reply.

I don't think you need a separate home, because you already have partitions for data.

Root is used for / and home is /home.

You will have a problem during the install, make the freed space one big extended partition and make two logical drives in it. 

You might find this easier with GParted Live CD, see the link in my sig.

You can only have 4 primary partitions on a single hard disk.

You don't need a large swap, that is outdated advice. I don't think the others are taking into consider partition limits here, so don't follow their advice. There are no issues with using NTFS with Ubuntu 7.10, so you can use them for your data.

---

### Post by LinuxIsInnovation on 2007-12-24
I made a correction. Home is not root. The above post is correct.

---

### Post by ubantunovice on 2007-12-24
> **LaRoza said:**
> I don't think you need a separate home, because you already have partitions for data.

You don't need a large swap, that is outdated advice. I don't think the others are taking into consider partition limits here, so don't follow their advice. There are no issues with using NTFS with Ubuntu 7.10, so you can use them for your data.

Would it be wise to mix data files created in Ubuntu in the same data partition with those created in Windows XP?  Could they really be used interchangeably across OSs?  Years ago I tried Linux and seem to recall that one needed a special file utlity to read the other system's files but should not write across file systems.  But I do not really remember well and maybe that is no longer the case.

Thanks for the input.

---

### Post by p_quarles on 2007-12-24
> **ubantunovice said:**
> Would it be wise to mix data files created in Ubuntu in the same data partition with those created in Windows XP?  Could they really be used interchangeably across OSs?  Years ago I tried Linux and seem to recall that one needed a special file utlity to read the other system's files but should not write across file systems.  But I do not really remember well and maybe that is no longer the case.

Thanks for the input.
Like LaRoza said, Ubuntu works very well with NTFS these days. It comes preinstalled with the utility you mentioned, which is more stable now than it was even a year ago. 

The only reason not to use the NTFS data partition is if you were getting rid of Windows entirely, instead of dual-booting. NTFS partitions need to be defragmented from time to time, and there are no NTFS defrag programs in Linux (that I know of  -- and I've looked). Since you're keeping Windows around, you're good.

---

### Post by LaRoza on 2007-12-24
> **ubantunovice said:**
> Would it be wise to mix data files created in Ubuntu in the same data partition with those created in Windows XP?  Could they really be used interchangeably across OSs?  Years ago I tried Linux and seem to recall that one needed a special file utlity to read the other system's files but should not write across file systems.  But I do not really remember well and maybe that is no longer the case.

Thanks for the input.
Yes. I do it. And have had no problems on the Windows side.

Ubuntu 7.10 is the first Ubuntu to have this by default, so it is transparent. The partitions will be added to fstab and mounted when you boot.

No problem.

---

### Post by ubantunovice on 2007-12-25
> **p_quarles said:**
> Like LaRoza said, Ubuntu works very well with NTFS these days. It comes preinstalled with the utility you mentioned, which is more stable now than it was even a year ago. 

The only reason not to use the NTFS data partition is if you were getting rid of Windows entirely, instead of dual-booting. NTFS partitions need to be defragmented from time to time, and there are no NTFS defrag programs in Linux (that I know of  -- and I've looked). Since you're keeping Windows around, you're good.

Thank you very much.

---

