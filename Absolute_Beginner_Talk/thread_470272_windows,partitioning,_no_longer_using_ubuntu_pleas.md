---
title: "windows,partitioning, no longer using ubuntu please help"
date: 2007-06-10
forum: Absolute Beginner Talk
---

### Post by madhatter43 on 2007-06-10
I am not even sure if this is the correct place to post this, please let me know if it isnt.

a few months ago i decided to install Ubuntu because i wanted to try it out and see if it was worth converting from windows. but  also did not want to uninstall windows(xp SP2 home edition) but i read that one could partition your hard rive and just keep Ubuntu on one half of your hard rive and windows on the other and just choose from grub which operation system to use when booting up your computer. well the first time i burned the Ubuntu install i installed it and partitioned and everything went fine, but after the first time i restarted the computer, as it booted up the computer it skipped grub and went straight to my f8 or f12 (i don't remember which) system restart. after it ran the system restart i found only windows installed so i re-installed Ubuntu a second time and it all worked out fine. however i decided that Ubuntu wasn't for me so i just ran another system restart and found only windows installed when it was finished. but i recently realized that my previous 140 gig hard rive (i believe this is how big it was) is only 78 gigs now. i am fairly unfamiliar with partitioning, and i lack alot of computer skills, but im not totally illiterate and i can figure out alot. any help would be much appreciated

---

### Post by Bohlio on 2007-06-10
I think you can use the LiveCD, Run gparted, and with that, Delete whatever ext3 partitions you have, and delete your swap partition. Then, With the same tool, Expand your Windows partition to fill up the empty space. That should reclaim your hard drive for the slug we call windows :-P I am just guessing here, I haven't done it before.

---

### Post by madhatter43 on 2007-06-10
do you mean i should burn another copy of the live cd? would that mean at the stage i would normally partition my hardrive for ubuntu i would delete  all the ext3 and swap partitioned pescies and give them back to windows? what is gparted? im on the gparted website now, and they have a live cd as well, is that what you mean? sorry im sortof unknowing about what you mean

---

### Post by bren on 2007-06-10
hi madhat

use the livecd you have 

boot ubuntu from the cd

now go system | admin | gnome partion editor

now do what the previous guy said

bren

---

### Post by madhatter43 on 2007-06-10
i lost my old live cd, so i have to download a new one, but thank you alot for helping me out

---

