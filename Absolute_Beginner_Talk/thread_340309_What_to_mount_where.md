---
title: "What to mount where?"
date: 2007-01-17
forum: Absolute Beginner Talk
---

### Post by dumo on 2007-01-17
I'm trying to install 6.06 since 6.10 doens't know how to install itself, but then again, neither do I.
I've searched these forums and attempted to read the very unuserfriendly community instructions, but not surprisingly, there's nothing very helpful. So here I am.
I have 2 hard drives, one with XP installed, and the other with a crapload of misc files on it. I did plan ahead and partition my 2nd harddrive into 4, so now i have 2 partitions for linux. 
I don't want to format either drive (ie save all my data and have a dual boot system) but I don't know what I'm supposed to mount on each partition  - I have a total of 6.
I set one to "/" and one to "swap", but I am unsure if I am supposed to mount /windows to my XP partition and leave the rest blank, or leave them all blank, or leave them with /media, which is the default. 
Help?

---

### Post by tagginannie on 2007-01-17
> **dumo said:**
> I'm trying to install 6.06 since 6.10 doens't know how to install itself, but then again, neither do I.
I've searched these forums and attempted to read the very unuserfriendly community instructions, but not surprisingly, there's nothing very helpful. So here I am.
I have 2 hard drives, one with XP installed, and the other with a crapload of misc files on it. I did plan ahead and partition my 2nd harddrive into 4, so now i have 2 partitions for linux. 
I don't want to format either drive (ie save all my data and have a dual boot system) but I don't know what I'm supposed to mount on each partition  - I have a total of 6.
I set one to "/" and one to "swap", but I am unsure if I am supposed to mount /windows to my XP partition and leave the rest blank, or leave them all blank, or leave them with /media, which is the default. 
Help?

This Wiki should help you 
"Windows Dual Boot " [https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

Suzy

---

### Post by aysiu on 2007-01-17
As long as you have one partition as / and one partition as swap, it doesn't matter where you mount the rest of your partitions and drives. In fact, those mount points you can also change post-installation.

It's **very** important, though, that you set / and swap to be reformatted and the others *not* to be reformatted.

You can find an illustrated dual boot guide here:
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

---

### Post by randomnumber on 2007-01-17
I am not truly sure your situation but I think you are getting stuck on the install where setup partitions for install. ?

You need:(this is from memory so I may not be exact)
/ (root)
/swap

You will need to reformat the above partitions. 

/media is just where all other partitions etc are mounted so that you have access to them

I am not sure if this helped you, if not please describe your situation a little more.

---

### Post by anaconda on 2007-01-17
And remenber that 1GB swap-partition is big enough!! 

Just said it so that you wont use your other big partition for swap...

---

