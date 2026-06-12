---
title: "trying to reload ubu"
date: 2007-11-16
forum: Absolute Beginner Talk
---

### Post by ub9876 on 2007-11-16
I am reloading ubu from the cd that was mailed to me.
I want to over write the existing ubu install. Windows xp
is on the other side of the harddrive. its working fine.
ubu is unstable already,2 weeks. 
I boot from cd and select manual instead of the other partition options.It shows this
/dev/sda1     media  85000 mb  used  20000........not exact..
dev/sda3      media    71699mb   used    15000.....
dev/sda5      swap      3076 mb     used     ...
dev/sda2                     263mb    used     .......

is the first one windows???it  is the biggest..???
I selected the second down but it said ..need to select for root or something...
it doesnt let you select more than 1...
what should I do..?? I dont want windows messed with at all
can I if needed erase the whole ubu partition and ???
or do the guided install???

---

### Post by uclalinux on 2007-11-17
Use a liveCD, and install, when if ask for the drive do manual.  

You will see a drive that is NTFS, that is windows, don't do anything to that one. 

you will want to delete all the other drives. 

when they are gone, we will make 3 new partition

1. a new partition 50MB, in ext2,ext3 or jsf file type any one, it does not matter. Set the "Mount point" to the "/boot". ALSO under this ones options, make sure the boot box it marked, when this happens the ntfs partition will lose its boot box but thats what we want. 

2. a new partition 1000MB, the file type should be "Swap", and set to the "SWAP" - mount pount

3. a new partition size rest of drive, make it EXT3, and set the mount point to "/"

---

