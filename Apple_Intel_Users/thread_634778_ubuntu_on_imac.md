---
title: "ubuntu on imac"
date: 2007-12-08
forum: Apple Intel Users
---

### Post by rwltrz4 on 2007-12-08
If I use bootcamp to partition my drive how much space shuld i give for ubuntu 5,10, 15?

Also will I be able to "unpartition it" if I decide I just want one drive again?

Will it void out my applecare?

I just go through boot camp menu right (where is asks you the questions and such?

 Then install  ubuntu cd and install?

Will desktop effects work in ubuntu (beryl, etc) cause they didnt in parallels.

---

### Post by Levo75 on 2007-12-08
5.10 doesn't work on my iMac.

Just go for 7.10, it has compiz fusion built in!

---

### Post by rwltrz4 on 2007-12-08
now i am having problems install went haywire and failed due to not enough space at target? anyhoo will try again but please someone tell me how do I delete a volume in disc manager and get thngs back to just the osx volume, i have my main volume and one that is from install called:

linuxswap but it is grayed out and not mounted or will not mount, just want it gone, want 1 volume now till i figure out this, i thought linux was easy,lol, this is a hassle why cant you just install ubuntu?

---

### Post by tiiim on 2007-12-08
Ubuntu is simple to sort out, its not "easy" but if you dont mind sorting stuff out deff worth it, however to make things back to normal is simple as well

If you have 10.5 its simple.

Log onto live cd, run gparted from terminal and delete ubuntu so its just free space. You might need to de activate the swap before you can delete it, its in a menu somewhere in gparted.
Once you just have os x and free space boot back into into 10.5
Open up disk utility and there is a tab there for partitions or something like that.. you see your hard disk with os X and a lot of free space, simply drag your os x partition to cover the whole disk and then apply, 10.5 will extend the partition on the fly. Dont resize your HSF+ in linux allow Apple's OS to do that :)

If you have 10.4 then i think disk utility is not as good in which case you have to dive into OS X terminal and resize the partition manually.. scary if your not used to a command prompt and dangerous if you do it wrong:(

---

