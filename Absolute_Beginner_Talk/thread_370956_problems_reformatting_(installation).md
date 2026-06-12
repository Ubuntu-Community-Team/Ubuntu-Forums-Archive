---
title: "problems reformatting? (installation)"
date: 2007-02-26
forum: Absolute Beginner Talk
---

### Post by mr32123 on 2007-02-26
I was trying to install Ubuntu 6.10 yesterday on my desktop.  It would be a dual boot set up.  However when I came to the repartitioning phase it took an unbelievable amount of time (think in the time range of 3-4 hours).  Finally i decided there has to be something wrong and scrapped it.  Rebooting back into winxp i found that nothing had changed, no new partitions were created, no data was lost or corrupted, etc.  Everything ran normal. 

So why is ubuntu not repartitioning and installing itself?

---

### Post by houstonbofh on 2007-02-26
> **mr32123 said:**
> I was trying to install Ubuntu 6.10 yesterday on my desktop.  It would be a dual boot set up.  However when I came to the repartitioning phase it took an unbelievable amount of time (think in the time range of 3-4 hours).  Finally i decided there has to be something wrong and scrapped it.  Rebooting back into winxp i found that nothing had changed, no new partitions were created, no data was lost or corrupted, etc.  Everything ran normal. 

So why is ubuntu not repartitioning and installing itself?
With that information, anything we say would only be guesses.  But hey...  I like guessing!

How old is the WinXP install?  Did you defrag it?  Does it have a lot of free space.  After you compress it will it still have a lot of free space?  My guess is that gpartd was trying to find some room on the partition.

---

### Post by energiya on 2007-02-26
> **houstonbofh said:**
> Did you defrag it?  Does it have a lot of free space.

These are very important. Don't forget to defragment and check is you have enough space for the new partitions.
> **mr32123 said:**
> So why is ubuntu not repartitioning and installing itself?
Ubuntu gives the user the power of choise, not like M$. Win

---

### Post by mr32123 on 2007-02-26
lets see, since i somehow never had problems with it, i never reinstalled... so about 7 years (yeah miracle huh?)

I did not defragment, i wasn't aware this was so important, even though they "suggest" it in some help books. Half the drive is empty, so about 20 gigs is free. Thats definately enough for ubuntu.

---

### Post by Maestro23 on 2007-02-26
> **mr32123 said:**
> lets see, since i somehow never had problems with it, i never reinstalled... so about 7 years (yeah miracle huh?)

I did not defragment, i wasn't aware this was so important, even though they "suggest" it in some help books. Half the drive is empty, so about 20 gigs is free. Thats definately enough for ubuntu.

Defrag of a Windows drive is very important, since windows spreads bits/pieces of files everywhere.  One would really see this after a long time of installing/uninstalling programs.

---

### Post by houstonbofh on 2007-02-27
Yep.  Defrag first.  When you compress the drive, make sure you leave %25 free, or it gets real hard to compress. (read slow)

---

