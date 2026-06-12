---
title: "vista/ubuntu. Getting ubuntu onto 2nd partition?"
date: 2007-08-07
forum: Absolute Beginner Talk
---

### Post by nijuu on 2007-08-07
Hi All,
Trying to install ubuntu on a system with Vista installed on the first partition of the 2nd HD (No OS  on the first HD - but i want to keep it as my file storage drive). Questions are :

- on the 2nd HD - vista is on the first partition, and ive formatted the 3rd and 4th as ntfs - can i install ubuntu on the 2nd partition only ?.Reason being i have data on the 3rd and 4th partitions.
- ive actually tried install ubuntu on the 4th partition however on reboot only vista boots up - the ubuntu installer doesnt recognise Vista is on the HD during the install process.
- on reboot - vista does come up with the error mentioning some changes were made, choose a boot option etc.. does that mean GRUB did attempt to install at some stage?. 

thanks for any advice. Have had a decent search for more information - but i dont want to stuff this up as it took long enough to get vista on:).
thanks
N

---

### Post by bren on 2007-08-07
yes you can install ubuntu on the 2nd partition if it is big enough (note this is me with xp quoting the situation for vista but i don't see that it should be different for vista).    The partition should be big enough!  Maybe 10G is fine, maybe 15GB is better.   You also need a further small partition the same size as your RAM called SWAP.      It may be easiest to create this ahead of time in VISTA.

the way to install is to insert the LiveCD, click on install on the desktop.
After a few screens you get to the partitions screen - choose the MANUAL option and installl to your chosen parition

you may need to tweak GRUB after install.

when you have installed boot the liveCD again, open a terminal and post the results of "sudo fdisk -l" to this forum and you will get advice on final configuration of GRUB

hope that helps

bren

check out "hermanzone" and "pyschocats" on google for great ubuntu install resources

---

### Post by nijuu on 2007-08-07
Thanks for that.
I actually ended up repartitioning the 120gb 2nd HD into Vista 1st part, shrink the vista partition and left the rest unallocated for ubuntu.
Ran through the ubuntu setup repartitioned my main directory and swap file.
rebooted. Still no GRUB. Vista boots up into its boot manager (most likely cause i was fiddling with easybcd which has since been removed).

Using the suggested terminal program and sudo details are as follows :

/dev/hdd1  1 - 10769
/dev/hdd2 10770 - 14471
/dev/hdd3 14472 - 14593

thanks
Nigel :)

---

### Post by Computer Guru on 2007-08-07
Grab [EasyBCD 1.61 Beta]("http://neosmart.net/forums/showthread.php?t=642"), and add a Linux entry specifying "GRUB isn't installed"

---

### Post by nijuu on 2007-08-07
Comes up with 
root (hd1,1) ---> correction partition to which i installed kubuntu
Error 19 unable to mount partition.

Im actually going to remove the other HD which is actually drive 1, reformat Vista from scratch then try and install kubuntu again. thanks anyways

---

### Post by Computer Guru on 2007-08-09
Sounds like an issue with the partition's bootsector.
Maybe a improperly-mounted filesystem, incorrectly installed GRUB, or something like that?

---

