---
title: "Dual boot installation questions"
date: 2006-12-03
forum: Absolute Beginner Talk
---

### Post by robster3004 on 2006-12-03
Hi, I am about to attempt to install Ubuntu 6.06LTS on my computer, which already has Windows XP installed.  i want to keep XP and have it dual boot with windows.  After reading the graphical installation guide I still have a few questions.  

I only get options to either wipe my hard drive or manually partition it.  Now when I go to manually partition it and create a partition it says I need to make 2, one for the swap and one for the main partition, however GParted only allows me to make one partition saying I cannot further partition my drive.  Is it necessary to have these 2 parts, or can I just continue and install onto 1 partition?

The other question is when it moves to the next screen about which partitions are used for what I become confused, as I do not understand what this part means with all the hda1,2,3 etc on the left hand side.

Any help is greatly appreciated

---

### Post by atoponce on 2006-12-03
BEFORE partitioning, you need to defrag your Windows partition, and move all the data to the front of the partition.  In fact, defrag 3, 4, 5 or more times.

After defragging, the LiveCD with the graphical install should give you 3 options.  One to wipe the drive clean, one to automatically partition, and the third to manually partition.  I would recommend using the automatic partition method.  It will keep your Windows data in tact.

---

### Post by robster3004 on 2006-12-03
I've already defragged my HD multiple times, yet only get 2 options, wipe, or manually partition

---

### Post by atoponce on 2006-12-03
:) I just noticed that you are trying to install Dapper.  Not Edgy.  OK.  In that case...

You can have as many partitions as you like.  You don't NEED the swap partition, but it's highly recommended.  When running low on RAM, the OS uses SWAP.  I'd recommend it.  For the SWAP, set the partition size to the same amount as your RAM.

So with that, not sure why it's not allowing you to do 2 partitions, unless your telling gParted to give the whole new partition to SWAP.  Do you have any more information?

---

### Post by robster3004 on 2006-12-04
I dunno its really strange, is there a way I can easily partition my drive in windows, then tell you what partitions I have before I go back to installing Ubuntu, so you can let me know what I need to do on the option screen after, with all the partitions?

---

### Post by rsambuca on 2006-12-04
Don't get too frustrated!  You can only have up to four primary partitions on one hard drive.

Keep doing what you were doing, but when manually partitioning the drives from the live CD installer, make one extended partition for linux, and inside the extended partition you can make two logical partitions one will be for the root "/" system (format this as ext3), and a small swap partition (formatted as linuxswap).  A lot of people like to add a third partition inside of the extended partition for your /home directory (ext3).  The /home directory is where all your settings and personal files are stored, so if you ever have to reinstall the operating system, you just leave your /home directory intact, and all of your previous settings are restored.

---

### Post by bulldog on 2006-12-04
Maybe some info about your hard disk comes in handy as well.
How big is it in GB? Because installing on a 10GB hard disk is something else as a 200GB disk :D 
How many partitions do you have for windows?
How large are they?
Can you make enough free space for Ubuntu?

---

### Post by robster3004 on 2006-12-05
Sorry for taking a while to reply, its that time of year where the uni work just keeps piling up, lol.

> **rsambuca said:**
> Don't get too frustrated!  You can only have up to four primary partitions on one hard drive.

Keep doing what you were doing, but when manually partitioning the drives from the live CD installer, make one extended partition for linux, and inside the extended partition you can make two logical partitions one will be for the root "/" system (format this as ext3), and a small swap partition (formatted as linuxswap).  A lot of people like to add a third partition inside of the extended partition for your /home directory (ext3).  The /home directory is where all your settings and personal files are stored, so if you ever have to reinstall the operating system, you just leave your /home directory intact, and all of your previous settings are restored.


How would I go about doing the logical partitions inside of an extended partition?


> **bulldog said:**
> Maybe some info about your hard disk comes in handy as well.
How big is it in GB? Because installing on a 10GB hard disk is something else as a 200GB disk :D 
How many partitions do you have for windows?
How large are they?
Can you make enough free space for Ubuntu?

I have a Maxtor 6L160M0 HD, which is 145 GB.  According to GParted I have 3 partitions already, 1 big one, and 2 tiny ones, cant remember off the top of my head what they were.  I have 75GB (more or less) free on my HD so space is no problem.

---

### Post by Chinkostu on 2006-12-05
theres the problem, whats on those smaller partitions?

you could get a second hard drive (say a cheap 40gig) and install ubuntu on that if theres important stuff on those "tiny ones" :)

---

### Post by rsambuca on 2006-12-05
Quite often those little tiny partitions are recovery stuff for off the shelf systems.  I have the same thing on mine, so I just left them just in case.  Not a problem, though, as you can make as many logical partitions as you want inside of the extended partition.

I don't have the program in front of me right now, but if I recall when setting up your partitions using the liveCD, you will have to first shrink your WindowsXP partition to make room for your ubuntu.  Then in the free space you now have, create an extended partition instead of a primary partition.  Next, create a logical ext3 partition inside of the new extended partition, and then create a logical linux-swap partition to use for your ubuntu swap.  As mentioned previously, if you wish, you can also create another ext3 logical partition for your /home directory if you wish, but it is not necessary.

---

### Post by bulldog on 2006-12-05
I should suggest to download the gparted live cd and boot from it.
It's small 25MB and much easier to use.

[http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828](http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828)

---

### Post by scc4fun on 2006-12-05
> **bulldog said:**
> I should suggest to download the gparted live cd and boot from it.
It's small 25MB and much easier to use.

[http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828](http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828)
Using the GParted CD, you can use the documentation from the GParted page on sourceforge.
[http://gparted.sourceforge.net/larry/resize/resizing.htm](http://gparted.sourceforge.net/larry/resize/resizing.htm)
[http://gparted.sourceforge.net/larry/generalities/gparted.htm](http://gparted.sourceforge.net/larry/generalities/gparted.htm)
You'll need to print it out if you want to see them while working with GParted.

---

### Post by robster3004 on 2006-12-05
> **Chinkostu said:**
> theres the problem, whats on those smaller partitions?

you could get a second hard drive (say a cheap 40gig) and install ubuntu on that if theres important stuff on those "tiny ones" :)

No idea tbh whats on them, whatever Dell (its a Dell Dimension 5100) put on them :-? 

I'll have a go creating logical partitions as soon as I get some time, and report back :)

---

