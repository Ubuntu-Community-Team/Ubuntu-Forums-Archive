---
title: "Workaround for an iBook G4?"
date: 2005-08-09
forum: Apple PPC Users
---

### Post by ronin.chitown on 2005-08-09
Hey all:

I'm trying to figure out how to use Mac on Linux to run OS 9 on my iBook G4 from a clean disk.  The problem at the moment is figuring out how to get OS 9 on the laptop so that MOL can boot off of it.  Is this possible?

My approach involves four partitions:

1 - 4 gig Newworld Boot
2 - 4 gig EXT3 swap
3 - 12 gig HFS + for Tiger
4 - 32 gig HFS + for OS 9

First I'd do Tiger, then 9, then Ubuntu.  

Will it work?

---

### Post by leverknight1 on 2005-08-10
[QUOTE=ronin.chitown]Hey all:

I'm trying to figure out how to use Mac on Linux to run OS 9 on my iBook G4 from a clean disk.  The problem at the moment is figuring out how to get OS 9 on the laptop so that MOL can boot off of it.  Is this possible?

My approach involves four partitions:

1 - 4 gig Newworld Boot
2 - 4 gig EXT3 swap
3 - 12 gig HFS + for Tiger
4 - 32 gig HFS + for OS 9

First I'd do Tiger, then 9, then Ubuntu.  

Will it work?[/QUOTE]
 install 9 first if you can boot off the 9 cd start the disk utility program (if you are runnig a newer machine that cant boot off of 9 then you have to create a boot cd with 10s disk utility on it because the installer at leasty for the version i have wont let you use the program under the install cd.) format your hard drive by clicking the initalize button and then select the linuxppc format scheme click on the linux portion and drag it so that the mac and linux parts are fairly equal or however much you want as long as it is enough to install both systems.

once that is done install 9 then boot off the OSX disk and install that and then boot off the linux cd and go to the manualy edit partion table option. after it loads delet all the linux partions they should all be under the one marked hfs+ in the middle if they aren't dont delete any that say apple or macintosh. then once there is a big chunk of free space at the bottom of the table go up to guided partion and select the use largest free space option then the option that installs all in one partion.

if the install fails you need to go through that again to make sure that it does it properly.

once the partioning is done then install like regular and go through the rest of the linux install and it should recognize the OSX partion in the bootloader.

i plan on making a guide i have it writen i just need to get the time to sit and type it up.

---

