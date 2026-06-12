---
title: "triple boot?"
date: 2008-07-23
forum: Arch and derivatives
---

### Post by eeezzzeee on 2008-07-23
Hey guys,
I was wondering if I installed Arch into free space on my hard drive if I could use the same /home and /swap that I use for my Mint install?
Currently I have a dual boot winxp and mint on a 320 gig hard drive. I have a 20 gig partition for xp and a 90 gig ntfs partition for saving my files when xp messes up and I have to do a reinstall. I have Mint on basically the same config 20 gig / and 90 gig /home. I think I have a 1 gig swap I can't remember casue I am not on my computer right now. I have 40 gig free space on my hard drive that I have never formated or partitioned. I have got an itch to install Arch on it to learn more about linux. I have successfully installed arch in virtualbox a couple of times (some more succesful than others) and wanted to try the 64 bit on my computer. Basically I am wondering since I already have the /swap and /home partitions on my hard drive if I would be able just to make a / partition with the space I have free, and not bork my system doing so? Any problems that you guys can see that I should expect if I try this?
It seems all the info I found about this was in relation to setting up a triple boot from scratch without having partitions already set up, and I really don't want to have to set up everything from scratch again.
Thanks

---

### Post by eeezzzeee on 2008-07-23
While waiting for any replies I manually went through every thread in the arch fourms here instead of just running searches, and acutally found some answers. It is not recommended to use the same /home and i found a explanation for a triple boot in this thread 
[http://ubuntuforums.org/showthread.php?t=709184](http://ubuntuforums.org/showthread.php?t=709184)
If I could figure out how to delete this thread I would, I guess the old RTFM should also apply to Forums as well. If anyone does have any suggestions or sage advice for me before I try this feel free. Thanks.

---

### Post by basenvironment on 2008-07-23
if you create a new (different) user then sharing /home is usually okay

sharing swap is fine

---

### Post by fwojciec on 2008-07-23
Well done on finding the relevant info yourself -- that skill will come useful when you're running Arch :)

But basically what you've found is correct.  You don't want to share /home because you do want to be able to configure each OS separately.  You can share swap without problems though.

Good luck, and have fun!

---

### Post by hessiess on 2008-07-24
if you want to share your data between OS,s you can make a partition and mount it as /home/a/ALL or something. becouse this would not contain config files its OK.

---

