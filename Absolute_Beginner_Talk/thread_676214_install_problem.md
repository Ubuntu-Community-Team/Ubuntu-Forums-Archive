---
title: "install problem"
date: 2008-01-23
forum: Absolute Beginner Talk
---

### Post by thebazman on 2008-01-23
hi
Been using linux now for about 7 months and always been able to fix any problems by looking at this forum (the best imo). 
But im tearing my hair out at this problem. at this moment in time im using the opengeu live cd as i cant seem to install any distro apart from elive. 
i can use any live cd distro no problem but when i try to install i get through everything no problem until it tries to write ext3 to the partition then it freezes at 5% all the time.
i have no problem installing elive 

thanks in advance

---

### Post by thebazman on 2008-01-23
hi
i forgot to mention, when i go through to the partition part in the installer it always comes up install 1.5 gb at 50%. that is half of my swap, its not recognising the partition with all the space which filesystem is elives . i delete elive and tell the installer reformat in ext3 but it freezes 5% into the install every time.
ive also tried gparted but that also freezes when reformating the partition with ext3 at 5%

thanks in advance

---

### Post by thelatinist on 2008-01-23
Umm...what "other" distribution are you trying to install with the OpenGUE Live CD?

---

### Post by thebazman on 2008-01-23
im not trying to install with opengeu live cd. thats just the one im using to write this.
iv tried most of ubuntu based distros and a few others but cant install it always freezes at 5%.
cheers

---

### Post by thelatinist on 2008-01-23
The problem, then, is a partitioning problem not an installation problem.  Namely it is a problem with gparted.  Have you tried editing your partition table with some other utility (cfdisk, maybe?)

It might be worthwhile to checking for physical defects on the device using the badblocks command.

---

### Post by thebazman on 2008-01-23
ive never used cfdisk. there is that option along with gparted when making partions before installing elive but with gparted i know what to do.
its strange that i can install elive gem and elive unstable no problem

---

### Post by thelatinist on 2008-01-23
> **thebazman said:**
> ive never used cfdisk. there is that option along with gparted when making partions before installing elive but with gparted i know what to do.
its strange that i can install elive gem and elive unstable no problem

I would boot into a live cd and run

```
badblocks /dev/sda#
```

replacing /dev/sda# with the actual device ID.

---

### Post by thebazman on 2008-01-24
i tried doing that but it returns, badblocks no file or directory while trying to determine drive size

thanks for replying

---

### Post by njparton on 2008-01-24
I had a similar problem a couple of months ago.  I took an old hard drive quite happily running windows, deleted all the partitions and then tried to install ubuntu. After 2 days of trying varying things I gave up and tried another hard drive which worked first time.

Something in ubuntu (installer/partitioner/ext3 filesystem?) doesn't like dodgy hard drives.

Moral of the story - try another hard drive :)

---

### Post by thebazman on 2008-01-24
hi
i had mint and ubuntu on my hard drive upto about 10 days ago then i used restricted drivers which would would work then wouldnt back and forth so i thought id reinstall cleanly. but then decided to try something else and what a mistake that was as im now in this predicament.
maybe ur right about the drive and the ubunt installer but im not ready to give up on them just yet. im sure someone with knowhow will have the answer.
i just hope they see this post 

cheers

---

### Post by njparton on 2008-01-24
OK, well a long shot would be to download "super F disk" and securely delete the whole drive.

It will take a while but all remnants of any data on there will be gone.  It's an overnight job. Also use it to delete the MBR.

---

### Post by thebazman on 2008-01-24
i will probably have to do that 

cheers

---

