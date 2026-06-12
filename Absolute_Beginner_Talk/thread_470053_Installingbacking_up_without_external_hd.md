---
title: "Installing/backing up without external hd"
date: 2007-06-10
forum: Absolute Beginner Talk
---

### Post by eZtaR on 2007-06-10
Hello there :)

I've been thinking allot about making ubuntu my main OS for the past month or so and i've been prepping my system for it aswell. but one question remains:

I would like do back up some documents, music etc. (about 30 GB out of the 80 on my HD) when i install ubuntu, **BUT** don't have an external harddrive or any burnable media to burn the data out on. So i'm thinking about formatting the free space (about 6 gigs) on my HD for the linux file system (which i don't recall the name of or how it works) and installing ubuntu on that. Then moving some of my data from the NTFS partition to the linux-partition, then extending the linux-partition by the amount of data i've moved, then copying more data, then extending and so on.

Could this be possible and how? (I'm thinking a bootable disc with partition magic on it)
Would there be and easier way of doing this?

---

### Post by KingJohn on 2007-06-10
This is doable, and gparted is exactly the tool to do it with - a bootable CD with a partition editor on it.

Frankly, though, if you're only looking to save 30GB of data out of the 80 on the disk, why not start with a 40GB linux parition, install Ubuntu, and simply copy everything in one pass?

And you don't have any other drives available?  Not even something like a 30GB iPod, that you could use as data storage?  Where do you keep your backups, anyway, in case the disk crashes?  It may be advisable to actually spend the $40 and buy a second 80GB drive, install Ubuntu on it, copy all the data, and then wipe the first disk entirely.

(This, of course, assumes that you're running a Desktop and have room for a second HDD.  If you've just got a single-disk laptop, then buying a different drive isn't a good option unless you're also going to buy a USB enclosure to play disk-swap with.)

---

### Post by eZtaR on 2007-06-10
> **KingJohn said:**
> This is doable, and gparted is exactly the tool to do it with - a bootable CD with a partition editor on it.

Frankly, though, if you're only looking to save 30GB of data out of the 80 on the disk, why not start with a 40GB linux parition, install Ubuntu, and simply copy everything in one pass?

And you don't have any other drives available?  Not even something like a 30GB iPod, that you could use as data storage?  Where do you keep your backups, anyway, in case the disk crashes?  It may be advisable to actually spend the $40 and buy a second 80GB drive, install Ubuntu on it, copy all the data, and then wipe the first disk entirely.

(This, of course, assumes that you're running a Desktop and have room for a second HDD.  If you've just got a single-disk laptop, then buying a different drive isn't a good option unless you're also going to buy a USB enclosure to play disk-swap with.)

I'm on a laptop and i've asked all my mates if they had any hotplugable storage i could borrow and no one did (note to self: get more nerdy friends :P)

But i've been looking into an app called [ntfsresize](http://man.linux-ntfs.org/ntfsresize.8.html) you think that could do the job for me, so i don't have to reboot to boot the partitioning-software all the time? :)

---

### Post by KingJohn on 2007-06-10
gparted uses ntfsresize as part of it's functionality, but, beyond that, I know nothing about the app, sorry.   I honestly can't tell you if it will do what you need it to, or not.

Why can't you just do everything in one reboot?  80GB HDD + 30GB critical data leaves you with 40GB for Ubuntu's partition, with 40GB for Windows, meaning your critical data +10GB for the OS itself.  That's plenty - and that means you only need two rezises, one to create the Ubuntu partition, and one to delete the Windows partition and expand the Ubuntu one after you're done tossing the media around.

(Worst case, you've got a laptop and it's only 30GB of data.  Can one of your friends spare the disk space on their own machine for a few hours?  If so, go to their house, plug into their network, and have them share a folder for you.  Drop all your stuff into that folder, across the network.  Wipe your whole machine, install Ubuntu, mount the folder again as smbfs, and copy it all back to your machine.)

---

### Post by eZtaR on 2007-06-11
> **KingJohn said:**
> gparted uses ntfsresize as part of it's functionality, but, beyond that, I know nothing about the app, sorry.   I honestly can't tell you if it will do what you need it to, or not.

Why can't you just do everything in one reboot?  80GB HDD + 30GB critical data leaves you with 40GB for Ubuntu's partition, with 40GB for Windows, meaning your critical data +10GB for the OS itself.  That's plenty - and that means you only need two rezises, one to create the Ubuntu partition, and one to delete the Windows partition and expand the Ubuntu one after you're done tossing the media around.

(Worst case, you've got a laptop and it's only 30GB of data.  Can one of your friends spare the disk space on their own machine for a few hours?  If so, go to their house, plug into their network, and have them share a folder for you.  Drop all your stuff into that folder, across the network.  Wipe your whole machine, install Ubuntu, mount the folder again as smbfs, and copy it all back to your machine.)

Thanks for the help dude :) Seems i'm gonna do some cleaning tomorrow (big moving day :D) and then do as you advise :)

PS. I've booted the livecd and it doesn't seem to let me resize the ntfs partition, but wth i'll see how it looks tomorrow after install :)

---

### Post by KingJohn on 2007-06-11
You should be able to resize the partition, up to the amount of free space and down to the amount of data.  Just make sure that you've got enough free space on the drive to free up - if you want to make the Windows partition 20GB smaller, you need to have 20GB free space on the Windows partition.  GParted won't let you lose data like that.

---

