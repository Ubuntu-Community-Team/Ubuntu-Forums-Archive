---
title: "swap partition or swap file"
date: 2007-10-22
forum: Absolute Beginner Talk
---

### Post by fourscore on 2007-10-22
Can we use a  swap file instead of  swap partition.   If  yes   how do we setup  one.

---

### Post by realvz on 2007-10-22
what do you mean by swap file...
are you referring to the page file that windows uses?

---

### Post by hyper_ch on 2007-10-22
as far as I know you can only use swap partitions - but I haven't looked much into that so far.

---

### Post by Sunforge on 2007-10-22
You can create a swap file:
 
[http://www.cyberciti.biz/faq/linux-add-a-swap-file-howto/](http://www.cyberciti.biz/faq/linux-add-a-swap-file-howto/)
 
The only reason you'd have a separate swap partition is for performance and protection, which is a good thing on a hard working server where you can move your swap partition to, say, a mirrored volume of disks.
 
It's a moot point if you need either partition or a file if you have more than 1 Gb of RAM on an average PC under average use. 

More than 2 Gb of RAM and there are quite good arguments to do away with swap altogether:

[http://ubuntuforums.org/showpost.php?p=1255511&postcount=43](http://ubuntuforums.org/showpost.php?p=1255511&postcount=43)
 
Best way to find out what suits you is to play around with your settings and see what happens: if you've got RAM to play with, that is.
 
Be sure to make a backup before breaking anything :-P

---

### Post by realvz on 2007-10-22
what are your reasons for opting for swap file...when swap partition just works fine...

---

### Post by kerry_s on 2007-10-22
> **fourscore said:**
> Can we use a  swap file instead of  swap partition.   If  yes   how do we setup  one.

yes!
**sudo apt-get install swapd**

this is a fantastic auto swap file program, what it does is create a swapfile only when you need it and deletes it when no longer needed, this way you get no wasted space. you can tweak the settings if you want in /etc/swapd.conf
i ran without a swap and only used that program on a 256ram system with no problems. on this install i do have a 512 swap partion and i still have swapd install just in case. :)

here's my settings->
```

# swapd.conf - config file for swapd
#
# Copyright 2000 Neven Lovric <nlovric@jagor.srce.hr>
#

# Memory limit in kilobytes.
# When the total amount of free memory gets below this number, swapd creates
# a new swap file.
# 16384 or more recommended
memlimit 85660

# Pause between memory checks in miliseconds.
# When the total amount of free memory is above <memlimit>, swapd will pause
# for <pause> miliseconds before checking memory again.
# 1000 should be ok for most systems
pause 1000

# Swap file size in kilobytes.
# >= 64, 4096 recommended
swapsize 131072

# Maximum number of swap files.
# No more than <maxswaps> swap files will be used.
# 0 = unlimited (as many as the kernel will allow)
# 8 = maximum number of swaps in the default kernel
maxswaps 0

# Timeout in seconds.
# If the last created swap file is unused for <sec> seconds, it will be
# removed. The last created swapfile is considered unused when there are
# more than <memlimit> + <swapsize> kb of free memory (physical + swap).
# 60 is nice
timeout 60

# Swap directory where all the swap files are kept.
swapdir /swap

# PID file (where the currently running swapd stores it's PID so a new swapd
# can find it)
pidfile /var/run/swapd.pid

# Full path to mkswap.
mkswap /sbin/mkswap


```

---

### Post by realvz on 2007-10-22
thanks Kerry_s...you taught me something new today..

I love linux

---

### Post by hyper_ch on 2007-10-22
I still see not a reason why to use a swap file...

Imagine you use up all your partition space and then a program would require swap. It can't be provided anymore...

---

### Post by realvz on 2007-10-22
> **hyper_ch said:**
> I still see not a reason why to use a swap file...

Imagine you use up all your partition space and then a program would require swap. It can't be provided anymore...

Yes...unless i have 10GB Harddrive..i would definitely go for a swap partition

---

### Post by hyper_ch on 2007-10-22
well, downloading movies through torrent uses up your disk pretty quickly ;)

Just to be on the safe side I would create a partition... so you have your swap anytime.

---

### Post by kerry_s on 2007-10-22
> **hyper_ch said:**
> I still see not a reason why to use a swap file...

Imagine you use up all your partition space and then a program would require swap. It can't be provided anymore...

there's no difference between a swapfile and a swap partion, a swapfile can be created at any time to give you more swap, a swap partion is fixed, you lose that space whether you use it or not. speed wise there both the same if using just 1 drive.

---

### Post by hyper_ch on 2007-10-22
kerry_s

There is a difference: If you use 100% of your disk space, you can't have a swap file anymore when needed. I tend to think then the system will crash...

And having 1-2GB swap partition never hurts ;)

---

### Post by kerry_s on 2007-10-22
> **realvz said:**
> Yes...unless i have 10GB Harddrive..i would definitely go for a swap partition

then you end up with dead space, you can use all your space and all your ram with out no limits using swapd. if you have 512 to a 1gig of ram swap rarely gets used. ram is faster you want to use as much of that as possible.

---

### Post by realvz on 2007-10-22
> **hyper_ch said:**
> kerry_s

There is a difference: If you use 100% of your disk space, you can't have a swap file anymore when needed. I tend to think then the system will crash...

And having 1-2GB swap partition never hurts ;)

absolutely...why take risk anyway???

---

### Post by kerry_s on 2007-10-22
> **hyper_ch said:**
> kerry_s

There is a difference: If you use 100% of your disk space, you can't have a swap file anymore when needed. I tend to think then the system will crash...

And having 1-2GB swap partition never hurts ;)

if you use 100% of your disk a swap partion is not going to help.

---

### Post by fourscore on 2007-10-22
Tks for all the replies.   
I just saw this  FAQ  - [https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq) -   which states   " The hibernation implementation currently used in Ubuntu, swsusp, needs a swap or suspend partition, and can not use a swap file on an active file system"
Seems like  will have to stick to the swap partition.

---

### Post by kerry_s on 2007-10-22
> **fourscore said:**
> Tks for all the replies.   
I just saw this  FAQ  - [https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq) -   which states   " The hibernation implementation currently used in Ubuntu, swsusp, needs a swap or suspend partition, and can not use a swap file on an active file system"
Seems like  will have to stick to the swap partition.

yeah if your going to use hibernate and suspend you want a big swap. those never worked for me so i don't use them.

---

