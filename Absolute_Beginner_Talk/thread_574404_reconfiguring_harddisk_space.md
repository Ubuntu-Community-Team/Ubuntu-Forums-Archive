---
title: "reconfiguring harddisk space"
date: 2007-10-12
forum: Absolute Beginner Talk
---

### Post by zaprenki on 2007-10-12
Hi there...
Before I begin, I would like to apologize for the relatively big post, I just want to be as accurate and descriptive as possible.
I 've installed Ubuntu 7.04 and now I'm spending happy time playing with it :)
The initial hard disk setup was a 200 GB hard drive with WinXP Pro installed. I used Partition Magic and created 2 extra partitions for Ubuntu, a 1 GB swap partition and a 3 GB ext3 partition where the root filesystem was installed.
After a successful install I realised that the 3 GB partition was not enough, as 2.5 GB were already occupied by the system, leaving me with only 500 MB of free space. So I used Partition Magic once again and extracted 3 more GB from the Win XP partition, creating a fourth partition.
My original purpose was to join the two 3 GB partitions to a 6 GB one, where the root filesystem could be mounted. I searched Ubuntuforums thoroughly but couldn't find a way to do this. Booting from Ubuntu LiveCD and using the partition manager does not allow me to resize the existing ext3 partition, neither does Partition Magic. So I followed another solution that I found, and moved the /home directory to the newly created 3 GB partition.
The problem is that even this solution is practical for keeping my settings and files after new installations, it doesn't help much with free space issues, as the root filesystem still has only 500-600 MB free, and program installations write their files in / and not in /home. So I'm stuck with an almost full / partition and an almost empty /home partition with not much use for it.
Could anyone suggest a more viable solution on how to reconfigure my disk space and partitions? I would like to grow the / partition to 5-6 GB while /home partition could be left with 1-2 GB. The WinXP partition has about 45 GB free and I can use Partition Magic to create as free space as needed.

Any help would be greatly appreciated, thanks in advance...

---

### Post by kronk on 2007-10-13
I always err on the side of caution when it comes to partitions. Even more so in a multi-boot envirionment.

Is there anything in particular that prevents you from erasing the linux partitions and starting again reseting the partitions with your partition magic to your new requirements and reloading ?

Not the tidiest of solutions I know however as above "caution" sounds like it's the key here !

---

### Post by zaprenki on 2007-10-15
Well you 're absolutely right, only the wrong partitioning scheme was caused not by the lack of caution but the lack of knowledge...
Anyway, erasing and reconfiguring the partitions means that the installation will be lost together with any files and personal settings. Let alone all the update files, totalling about 200MB. So the solution you recommend is kind of a last -and desperate- resort.
By the way, is there any way to keep the update files so that I don't have to download them again? Maybe they are stored in some directory?

---

### Post by ThrobbingBrain66 on 2007-10-15
Updated packages are kept in /var/cache/apt/archives (unless you've cleared them wiith 'sudo apt-get clean')

Seems you've made a bit of a mess with your partitions trying to do all this :)

It's also possible to copy all the hidden (.packagename) folders inside /home (you have to hit ctrl+h to see them) to a USB drive.  Those folders contain all of your settings.  After a reinstall, just copy them back over.

---

### Post by zaprenki on 2007-10-15
OK, I've found the update packages in /var/cache/apt/archives/. How can I use them after a new installation? I just copy them to the same folder and then what? Will update manager recognize them and skip their download?
Also I couldn't find any hidden (.packagename) folders inside /home. What are these folders?

---

### Post by logos34 on 2007-10-15
> **zaprenki said:**
> Could anyone suggest a more viable solution on how to reconfigure my disk space and partitions? I would like to grow the / partition to 5-6 GB while /home partition could be left with 1-2 GB. The WinXP partition has about 45 GB free and I can use Partition Magic to create as free space as needed.

Use PM to shrink winxp down a few more gigs.  

Download the latest [Gparted livecd (0.3.4)]("http://gparted.sourceforge.net/livecd.php").

Then use it to expand /home left into the freed up windows space.  Shrink /home on the right a few gigs.  Delete the /swap.  Expand / to the left into the freed up space.  Shrink it from the right  by 1 gig and put swap there, at the end of the disk.

If I got the layout wrong post a screenshot of gparted.

---

### Post by indytim on 2007-10-15
Adding to what Logos34 suggested:

1.  Defrag your NTFS partition first.
2.  Using GParted Live, follow Logos34 scheme BUT, do one task at a time to completion within GParted Live.  In other words, DON'T stack multiple tasks up in GParted Live.

I did a similar activity a while back.  In my earlier learning experience, I stacked tasks in GParted.  Upon execution, I ended up frying my partition table.   This resulted in a complete re-format and re-installation from scratch of 4 different ops.

Happy Partitioning!

IndyTim

---

### Post by zaprenki on 2007-10-15
Thanks for the replies, I'm really impressed by your will to help me on such short notice...
Below follows the partition scheme:

the order of partitions on the disk is this:
**sdb1 | sdb4 | sdb2 | sdb3**

and this is what they represent:
[B]sdb1: WinXP ntfs partition - 185GB/65GB free
sdb4: Linux ext3 /home partition - 2GB/1.5GB free
sdb2: Linux ext3 / partition - 3GB/0.5GB free
sdb3: Linux swap partition - 1GB[/B]

Is it true that I should make the changes with gparted on partitions one at a time? Reboot then or just apply the one change before creating the next?

---

