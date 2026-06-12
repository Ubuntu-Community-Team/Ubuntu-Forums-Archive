---
title: "Separate Partitions"
date: 2007-07-15
forum: Absolute Beginner Talk
---

### Post by tarek on 2007-07-15
Hi, I want to create a separate home partition for a fresh FF. Hard drive is 60GB and 1128 RAM

As far as I know (please correct me if I'm wrong) there are three partitions: swap, root and home.

48 GB > home
10 GB > root (Ubuntu OS)
2   GB > swap

I have four questions:

Am I missing a something?

Is 10 GB enough for a standard Ubuntu installation and for future upgrades?

Is 2 GB swap small/large/good?

Which ones should be primary or logical?

Thank you,
TK

---

### Post by starcraft.man on 2007-07-15
> **tarek said:**
> Hi, I want to create a separate home partition for a fresh FF. Hard drive is 60GB and 1128 RAM

As far as I know (please correct me if I'm wrong) there are three partitions: swap, root and home.

48 GB > home
10 GB > root (Ubuntu OS)
2   GB > swap

I have four questions:

Am I missing a something? [COLOR="Blue"]- Nope, you got the 3 essentials. If you further want to partition out things like /boot and such that's up to you but not required.
[/COLOR]
Is 10 GB enough for a standard Ubuntu installation and for future upgrades? [COLOR="Blue"]- More than enough.[/COLOR]

Is 2 GB swap small/large/good? [COLOR="Blue"]- Too much IMO, you got a GB RAM which is pretty good. 1 GB swap is more than enough to me, any more and it seems like wastage. In all likelihood unless you do really intensive things like VMs and such you probably won't need all that. Easiest way to see what you need is to open the system monitor (System > Administration) and go to the resources tab, then watch your physical and swap memory usage. The best test is to open whatever your usually doing and monitor how much you go through... then round up to nearest 256 increment.[/COLOR]

Which ones should be primary or logical? [COLOR="Blue"]- You can make them all logical, Linux doesn't have a need for primary partitions.[/COLOR]

Thank you,
TK

That's it, blue's my answers. Best of luck with that :).

---

### Post by southernman on 2007-07-15
>  Am I missing a something?You've pretty well got it covered IMO.

>  Is 10 GB enough for a standard Ubuntu installation and for future upgrades?In essence, that should be plenty. Unless your a super power user and want to install all things known to Ubuntu / Linux... your good with 10GB.

>  Is 2 GB swap small/large/good?Should be plenty however, (I didn't say but!) unless your going to be doing some very graphic intensive work (eg gaming, multimedia ripping, video / audio encoding) You can get away with just 1GB of swap. Use that extra GB for your /home.

>  Which ones should be primary or logical?Unless your planning to dual boot (doesn't appear that you are, but ya never know) you could set all three up as primary. At the very least, keep your /home in a primary and put / and swap on an extended partition. Examples below:

Use primary only -
(dev/hda1 ) / = 10GB 
(dev/hda2) /home = 45GB 
(dev/hda3) swap = 1GB 

Use of Primary and Extended - 
(dev/hda1) Extended Partition
----> (dev/hda5) / = 10GB
----> (dev/hda6) swap = 1GB
(dev/hda2) /home = 45GB

*sidebar - While the label on your hdd may say it's a 60 giger, you won't get that much in reality... which surely you know already. So, with that said, adjust the size of your /home partition accordingly.

Out of 100 people, you may get 99 ways of doing it... and each will have it's merits. If I were setting up the box for you, I'd opt to use a combination of extended and primary.

Your mileage may vary... enjoy! :)

---

### Post by anewguy on 2007-07-16
Hi tarek!    I'm going to offer 1 suggestion, but others may disagree with me.   In the big box world it was normally required, and hence I would think at least a good idea, to make your swap at least twice the size of your installed memory.  I have been away from things too long to remember the exact reasons why right now.  You look to have plenty of disk space to spare the little extra.  You might even want to consider more so that if you add memory you won't have to go back and change the size.

Just a suggestion, and thanks again for your help!!:)

---

### Post by tarek on 2007-07-16
Thanks everyone :)

I use this pc to develop in java, cpp, etc. + running virtual machines + watch movies, internet, etc. 

So I decided to leave the swap as 2 GB (better for virtual machines) and root as 8 GB and home as 50 GB.

Here's the plan:

Primary 50 GB home
Primary 8 GB root
Extended 2 GB swap

Does the order of partitions matter?

Thanks.
TK

---

