---
title: "Do I need more RAM?"
date: 2006-08-18
forum: Absolute Beginner Talk
---

### Post by xx75 on 2006-08-18
Hi all,

In an attempt to find out why my system locks up on a regular basis (but very randomly) I have found that it can be caused by RAM, whether faulty or otherwise. I have done a memtest on my 512MB RAM and it passed. I also learned along the way the 'free' command but unfortunately am unable to interperate the results enough to know if there is a problem.

I have just run that command and here are the results -

             total       used       free     shared    buffers     cached
Mem:        515972     508772       7200          0      55992     242812
-/+ buffers/cache:     209968     306004
Swap:      1510068          0    1510068


It doesn't seem that there is much free at this particular moment.
Is this alarming?
Do I need more RAM?

Any help is appreciated.
Thanks
xx75

---

### Post by Cone on 2006-08-18
It might depend on what you're doing, how long it's been since you've closed the browser (especially firefox), among other things.

Something to consider might be switching to the XFce desktop environment as it is rather lightweight relative to GNOME and suggested for systems that have trouble with GNOME as far as I've seen.

Hope it helps,
~Cone

---

### Post by TheOtherShoe on 2006-08-18
This can happen if you do not have a swap partition, or if your swap partition has not been activated.

To see if your swap partition is activated run this command:
```
swapon -s
```
I have found that once in a while a swap partition needs to be re-initialized to get it working again. You can do that using the GNOME Partition Editor under System > Administration. You may need to install it first with this command:
```
sudo apt-get install gparted
```

---

### Post by xx75 on 2006-08-18
Cone-

My firefox browser was started only a minute or so before the test.

If I have to I will switch to xfce, but I would rather find the problem.

Thanks for your suggestion though.

---

### Post by 23meg on 2006-08-18
Murphy law: you can never have enough RAM.

On a serious note, tweaking the swappiness value in sysctl may help. Do a forum search for "swappiness" and you'll find some leads.

---

### Post by xx75 on 2006-08-18
TheOtherShoe -

I have done what you suggested and got the following -
Filename                        Type            Size    Used  Priority
/dev/hda5                       partition       1510068 0       -1

Is this good?

Thanks
xx75

---

### Post by xx75 on 2006-08-18
Thanks 23meg

doing the search now.

xx75

---

### Post by TheOtherShoe on 2006-08-18
> **xx75 said:**
> TheOtherShoe -

I have done what you suggested and got the following -
Filename                        Type            Size    Used  Priority
/dev/hda5                       partition       1510068 0       -1

Is this good?

Thanks
xx75

It looks like your swap partition is active; but the fact that it says Used = 0 is suspicious. If that value remains zero under different loads then it means that the swap is not being used for some reason.

I don't know what could cause this. But 23meg's suggestion of looking into swappiness seems prudent to me. You might also try re-initializing the swap partition too, just in case.

---

### Post by avtolle on 2006-08-18
It could well be that with 512mb RAM, the system hasn't needed to access the swap partition. I say that not to discourage the OP from following the suggestions (all of which are good), but to point out why so much RAM is used: it's there, so it's used, for caching, etc., to improve system performance. There are more than a few threads on the Forum dealing with this question, i.e., heavy RAM usage, why so much RAM is used, etc. I encourage you to do a search and read the much-superior (compared to my feeble attempt) explanations therefor. I suspect "not enough RAM" may not be the cause of the random system lock-ups, although without more information, it is something to look at. Posting of any error messages, etc that appear at the time the system locks up would be helpful.

---

### Post by Contrid on 2006-08-18
> **TheOtherShoe said:**
> This can happen if you do not have a swap partition, or if your swap partition has not been activated.

To see if your swap partition is activated run this command:
```
swapon -s
``` I have found that once in a while a swap partition needs to be re-initialized to get it working again. You can do that using the GNOME Partition Editor under System > Administration. You may need to install it first with this command:
```
sudo apt-get install gparted
```

Hey there,

How do I know whether the swap partition is fine by using that command? I see the following :

Filename                                Type            Size    Used    Priority
/dev/hda5                               partition       2096440 0       -1

I'm not sure if that's right...please help

---

### Post by TheOtherShoe on 2006-08-20
> **Contrid said:**
> Hey there,

How do I know whether the swap partition is fine by using that command? I see the following :

Filename                                Type            Size    Used    Priority
/dev/hda5                               partition       2096440 0       -1

I'm not sure if that's right...please help

swapon -s lists the active swap partitions. You have /dev/hda5 listed, so it looks like everything is working fine.

avtolle has a point that it is normal for the swap not to be used when the machine is not under a very heavy load. My reason for suspecting a swap problem in xx75's case is that a swap partition failing to activate has caused a very similar problem for me twice. xx75, your swap partition is active, so it is very likely that something else is wrong. An easy way to eliminate the swap as the source of the lockup problems is to check whether the Used value from swapon -s is still zero when a lockup occurs. If it is, then the swap partition is the problem, if not then it is something else.

---

### Post by Copter on 2006-08-20
Hi!

With 512mb of RAM Ubuntu should work just fine. On my computer with 512mb configuration swap wasnt used very often. After running couple of apps (eg. Opera, amaroK...) most (>90%) of the memory was used. Quiting those apps did not force the system to free the memory that was used by them. I think Linux is quite smart here and it tries to use as much of provided RAM as possible to work as fast as possible.

Funny thing is that when I got another 512mb chip of RAM (1gb total) after running similar number of similar apps I have also >90% of the memory used _BUT_ the system works almost 2 times faster then before. I mean here mostly times needed to open specyfic apps or windows not numerical calculations. I have never seen swap used since then.

hope it helps,
Copter :]

---

