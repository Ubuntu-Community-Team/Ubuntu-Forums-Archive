---
title: "Manual install no Windows"
date: 2007-08-13
forum: Absolute Beginner Talk
---

### Post by durkhrod chogori on 2007-08-13
I got here Mint and want to install Feisty but keep room for more OS.

I went to Gparted and this is my current config:

[[IMG]http://img453.imageshack.us/img453/9919/screenshotrw4.th.png[/IMG]](http://img453.imageshack.us/my.php?image=screenshotrw4.png)


Now, my plan is to keep Mint, Ubuntu Feisty and either another distro or FreeBSD (bearing in mind that my total disk capacity is 100GB). So that will be roughly 33 GB to each of them.

Could you give me some info on how to rig Feisty using the above info?

I am a total beginner when it comes to partitioning and not keen to stuff up what I got if I try on my own. I get confused with the process of organizing home, root and swap. Need a detailed steps if possible. :)

Thnx for helping.

DC.

---

### Post by Arthur Archnix on 2007-08-13
I'd resize current partition to 4.69, delete the swap and extended partition, create two others ext3 partitions at 4.69, create an extended partition using the rest, create a swap partition at the end of between 512MB and 1Gig, and then make the balance ext3.

The first 4.69Gig partition I'd install ubuntu to, putting / and /home on it. I'd mount the two empty paritions to /mnt/some_OS and /mnt/another_OS.

THe large partition I'd put to /mnt/myfiles

And swap to swap.

This makes it easy to share files and settings between OS's. Also, if you're inclined to do so, easy to image an OS that you've got working great and burn it to a disc using partimage. 

Good luck!

---

### Post by durkhrod chogori on 2007-08-13
You said:

**Resize current partition to 4.69**

Which one is that in my screenie?


**delete the swap and extended partition**

As above

**create two others ext3 partitions at 4.69,**

That means resizing the 90.27GB space, right?

**create an extended partition using the rest**

Under which name?

**create a swap partition at the end of between 512MB and 1Gig, and then make the balance ext3.**

Very confusing. Could you please further explain?

**The first 4.69Gig partition I'd install ubuntu to, putting / and /home on it.** 

Only 4.69 GB to Ubuntu. I think that's way to small.

**I'd mount the two empty paritions to /mnt/some_OS and /mnt/another_OS.**

Need specific details, please.

**THe large partition I'd put to /mnt/myfiles**

**And swap to swap.**

???


Thanks for popping in but I am a beginner. Very confusing. :(

Cheers.

---

### Post by Arthur Archnix on 2007-08-13
Ok, I'll try again. sda is what ubuntu calls your harddrive.  When you make a partition on it it gives that partition a name, sda1, sda2, and so on. I took a closer look, you've got an OS on there called "Mint" on sda1 and it's already over 5 gigs.

Resize sda1 to be 7 or 8 gig. 

Delete /dev/sda5 and /dev/sda2

Create a new partition, make it primary, ext3, and make it the same size as /dev/sda1 (MINT). Repeat to create the third partition (probably /dev/sda3)

Now create a forth partition using all available space, but make this one extended. Now click inside that partition and create a new partition of about 512 to 1 gig in size and make this linux swap.

Now create your last partition and make this take up all the space that's left.  Make it ext3.

Now write down the names of things. You have sda1 and MINT on it. sda2 which is where Ubuntu will go. sda3 which is where FreeBSD may go. Write down the name of swap, right now in the picture its sda5, but what about after you make all those changes?

Now you'll have to assign mount points. These are connections made by the OS telling it where to put the various sda volumes it finds. Ubuntu is on sda2, so we want root to go there ( the / ). Swap should go to the sda# you wrote down above.  That's really all you have to do at this point, but it you llike, you can tell it to put /dev/sda1 to /mnt/mint/ and dev/sda3 to /mnt/freebsd and dev/sda#? to /mnt/myfiles

---

### Post by durkhrod chogori on 2007-08-14
Tnnx for the more detailed info.

:)

---

