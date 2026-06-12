---
title: "partition &quot;magic&quot;"
date: 2007-06-25
forum: Absolute Beginner Talk
---

### Post by zygoat_D on 2007-06-25
hay guys let me first say that i did some searching already and couldn't find what i was looking for. i did however find how to get me logitec mx 5000 working and that info was very helpful.

this is what i am hoping to do, you can tell me if im insane or if i can do it or if i can do something close.


i have xp on a two partition hd. i have a 10gb root partition for windows and a roughly 390gb partition for all of the programs ans such(so i can reinstall windows if need be and not lose all my sh*t). the large partition is only about 25% full. i do NOT want to reinstall windows if it is at all avoidable. i would ideally like to put Ubuntu at the very end of the physical drive by creating a partition at the end of the 390gb partition.i really don't want to lose any of my data, and ive got a pretty large amount to try and back up. is it possible to do this or at the very least create a partition in the empty space of the 390gb partition without losing any of my data on it, and still leaving free space there as well.

---

### Post by drowner on 2007-06-25
It certainly is possible.

you should defragment several times first.

If you really DONT want to backup you dont HAVE to, but it is highly recommended

There is no need to create the partition BEFORE installin ubuntu if you dont want to.,.. the ubuntu installer can do it for you. Some people have reported problems with using partition magic.

---

### Post by zygoat_D on 2007-06-25
i am not actually using partition magic i just wanted to work some "partition magic" if you know what i mean.;)  my drives are always de-fragmented. im kinda anal about it. so how do i go about actually doing it, do i do a manual creation in the install menu or what. is it possible to actually place the Ubuntu partition at the end of the pre-existing partition.

---

### Post by drowner on 2007-06-26
I assume youve not installed Ubuntu yet?

The ubuntu installation will partition things as necessary.

I'm pretty sure ubuntu will stick itself at the end of the HD anyway.

There are two excellent guides for installing a dualboot system:

[http://psychocats.net/ubuntu/installing](http://psychocats.net/ubuntu/installing) <-- aysiu's wonderul page, for the graphical liveCD

[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/) <--- herman's similarlyl wonderful page for using the 'alternatecd' (text based)

But, you sound like someone who takes care with their computer, so if you would rather do it yourself, you can create a partition (either using a program called gParted on the liveCD, or another program that you have or would like to use) at the end of the drive and leave it unformatted. you can tell the ubuntu live installer to install into that empty space.
__________________

---

