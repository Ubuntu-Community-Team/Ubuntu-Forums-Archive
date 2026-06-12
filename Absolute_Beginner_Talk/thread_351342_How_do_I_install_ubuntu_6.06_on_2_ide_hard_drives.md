---
title: "How do I install ubuntu 6.06 on 2 ide hard drives?"
date: 2007-02-01
forum: Absolute Beginner Talk
---

### Post by g_mac_1 on 2007-02-01
I want to ditch Windows and try Ubuntu 6.06.  I've been given an old socket 462 based PC in bits with a 4GB and 30GB hard drive.  If I set the jumpers on one as master and the other as slave does Ubuntu pick them up as 1 disk and prompt to partition or is there something else I have to do?
Any help would be appreciated
Thanks
George

---

### Post by Tux Aubrey on 2007-02-01
I have a master/slave set-up and Ubuntu detected each drive and gave me the choice of where to install and what to do about partitions.

---

### Post by crispy_420 on 2007-02-01
You could do some custom partitioning during install and set your 4GB HD to be system files and the 30GB to be your /home directory.

As far as slave/master, I would go 4GB as master to go along with what I said before. Each one will be seen as it's own disc (eg. hda & hdb).

Does that help or were you looking for something else?

---

### Post by logos34 on 2007-02-02
> **g_mac_1 said:**
> I want to ditch Windows and try Ubuntu 6.06.  I've been given an old socket 462 based PC in bits with a 4GB and 30GB hard drive.  If I set the jumpers on one as master and the other as slave does Ubuntu pick them up as 1 disk and prompt to partition or is there something else I have to do?
Any help would be appreciated
Thanks
George

They'll be recognized as separate disks.  Set one jumper as master and other as slave, or both as cable select. 

Crispy420's suggestion of putting your system and config files on the smaller drive would be just fine if it were a bit bigger...a 4gb drive is just way too small...a DVD holds more than that!...I have what I consider to be a lean install and just the system files and applications come to about 5gb...you won;t have room to add anything...i threw out an old 3.7gb quantum fireball (udma66) because it was just too small and slow to be worth the power to run it...I'm all for teaching old hardware new tricks but in this case you really need to start looking for a rebate sale on a new hard drive...then put the sys files on the 30gb drive and make the new drive /home.

---

### Post by Ocxic on 2007-02-02
if you would like to combine the drives into one, i would suggest LVM it's simple, and better then raid in you situation, it is an option during partition-ing in setup

---

### Post by xpod on 2007-02-02
> i threw out an old 3.7gb quantum fireball (udma66) because it was just too small and slow to be worth the power to run it...

I installed a 3.2g slave drive about a week before i`d even heard of ubuntu(just to see if i could)
So when i did come across Ubu that following week thats where it went:) 

3 or 4 lots of updates later of course and i was staring at the XP master drive with a slightly worried look upon my face:( 
Of course now theres 2 x 40g drives in here and the only XP is a virtual one i dont know why i`ve got.

You could always put DSL or similar on that 4g thing and dualboot:)

---

### Post by g_mac_1 on 2007-02-05
Using just the single drive sounds nice and straight forward but I think I'll try LVM first.  I definitely want to make use of that old hard disk while it's got some life in it.
Thanks for all the advice everyone
George

---

### Post by crispy_420 on 2007-02-05
I'm not sure about LVM to combine the drives as one. It sounds alot like RAID 0 ("fake raid") in windows. You have old hardware to be honest, no offence. Then if one drive fails than you lose all. It happened on my windows comp in RAID 0 with two raptors.

And my guess you switched over to Ubuntu for security and safety, wouldn't that throw that away?

---

### Post by g_mac_1 on 2007-02-06
Thanks, so it's hardly worth it then.  I'll just install the larger of the hard disks then get a better drive if I get into Ubuntu more and see what it has to offer.
George

---

### Post by crispy_420 on 2007-02-07
Not sure of your local prices, but hard drives have gotten cheap in the last year. You can easily get 100GB for less than $50 (US).

But now after your last post I have a new suggestion. Install to 30GB drive and use the 4GB for media/data storage until you replace it. 4GB is a decent amount of mp3/ogg files. Or maybe a bunch of guides & howto's to help you with Ubuntu?

---

