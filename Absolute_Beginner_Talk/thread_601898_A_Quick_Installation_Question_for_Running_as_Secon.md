---
title: "A Quick Installation Question for Running as Second OS"
date: 2007-11-03
forum: Absolute Beginner Talk
---

### Post by naceguy122 on 2007-11-03
I've got two hard drives. One (set as Master) came in the computer and contains Windows XP. My highest priority for this Ubuntu installation is to preserve this drive in its entirety. The second drive (set as Slave) is from an old computer and contains Windows ME. None of the data on this drive needs to be kept. If I run the installation and choose the second drive, will it simply install on that and not touch the first one at all? I would also like to give Windows access to this drive, but from what I know I can't give Ubuntu access to my Windows drive without a reformat, so I don't want to try. I'm assuming Windows will still be able to access the Ubuntu drive, but correct me if I am wrong. Also, how easy is it to choose which drive to boot off of? Is it a simple selection on the boot screen, or is there more to it than that? Thank you, and hopefully soon I can come back here from Ubuntu!

---

### Post by bluedragon436 on 2007-11-03
As far as installing Ubuntu on your secondary harddrive it isn't that hard at all...When it comes up to installing Ubuntu just select the second harddrive and it will erase everything off of that harddrive if you choose too...and your second harddrive will be your Ubuntu drive....now as far as being able to do a dual boot that way I am not sure how that will work, I think it will pretty much always start with teh XP drive since your computer will see that drive and see that there is an OS on it and start up without even looking at the second drive...but I could be wrong on that one...but you can go thru your BIOS and select it to look at the second HD when u want to run Ubuntu only...kind of a PITA but as far as I know this will be the only way to do it like that....

---

### Post by naceguy122 on 2007-11-03
I've been reading around and it seems that to configure the dual boot, I will have to add some Ubuntu boot files to my Master drive (XP). It doesn't sound too incredibly complicated, but if anyone knows anything about it and knows the simplest and **_safest_** (high priority) way to do it, please help me!

---

### Post by carlosjuero on 2007-11-03
> **naceguy122 said:**
> I've been reading around and it seems that to configure the dual boot, I will have to add some Ubuntu boot files to my Master drive (XP). It doesn't sound too incredibly complicated, but if anyone knows anything about it and knows the simplest and **_safest_** (high priority) way to do it, please help me!
The LiveCD installation will take care of adding the boot manager; not much to it :)

---

### Post by ntu on 2007-11-03
I would take out the Xp hdd and install Ubuntu on the remaining hdd; then put the xp hdd back in and boot your two OS's using bios. I swap between 3 OS's this way. I think this is the safest way to go.

---

### Post by Duck2006 on 2007-11-03
You can install ubuntu on the second hard drive. To boot the OS you want you have to load a boot loader on the MBR of the first drive or some thing like BCDEasy or wingrub and change your boot.ini file to point the loader to the linux OS.
Have a read of this.

[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

---

### Post by naceguy122 on 2007-11-03
> **carlosjuero said:**
> The LiveCD installation will take care of adding the boot manager; not much to it :)

And this will leave the rest of Windows alone and still allow it to run fine? I do have my important stuff backed up on CD and the original Windows/Included Software (most of which I don't even use any more...) DVD, so in the event of unforeseen circumstances, I'm covered, but I don't want to delete stuff on purpose.

---

### Post by carlosjuero on 2007-11-03
> **naceguy122 said:**
> And this will leave the rest of Windows alone and still allow it to run fine? I do have my important stuff backed up on CD and the original Windows/Included Software (most of which I don't even use any more...) DVD, so in the event of unforeseen circumstances, I'm covered, but I don't want to delete stuff on purpose.
Yep, it will detect your windows installation and install just fine with Windows as a boot menu option on startup. When I installed Ubuntu on my second HDD, I let the LiveCD do its thing and it came away perfectly. Just be sure to specify the proper drive for Ubuntu to reside on (likely /sdb1 - the main drive will be something like /sda1)

---

### Post by naceguy122 on 2007-11-03
OK, I guess I'm ready to give it a shot. Hopefully I can return with Ubuntu in an hour or so and post my results.

---

### Post by carlosjuero on 2007-11-03
> **naceguy122 said:**
> OK, I guess I'm ready to give it a shot. Hopefully I can return with Ubuntu in an hour or so and post my results.
Good luck :D - I am sure it will go swimmingly; my install was just about painless (darn ATI graphics cards :( )

---

