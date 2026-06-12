---
title: "cant partition"
date: 2007-07-08
forum: Absolute Beginner Talk
---

### Post by makinde on 2007-07-08
i like ubuntu but im not ready to replace whndows just yet. But when im installing there're 2 options not 3, neither of them being dual boot. How can this be solved?

---

### Post by steve.horsley on 2007-07-08
What are the two options offered?

---

### Post by overdrank on 2007-07-08
> **makinde said:**
> i like ubuntu but im not ready to replace whndows just yet. But when im installing there're 2 options not 3, neither of them being dual boot. How can this be solved?

Hi do you not have the manual, resize, or use entire drive as choice's?

---

### Post by makinde on 2007-07-08
> **overdrank said:**
> Hi do you not have the manual, resize, or use entire drive as choice's?

I have "guided - use entire disk" and "manual"

---

### Post by overdrank on 2007-07-08
> **makinde said:**
> I have "guided - use entire disk" and "manual"

Ok then you should be able to choose manual and resize your windows partition and make room for Ubuntu. :popcorn:

This link has some screen shots that may help you.
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

---

### Post by makinde on 2007-07-08
> **overdrank said:**
> Ok then you should be able to choose manual and resize your windows partition and make room for Ubuntu. :popcorn:

This link has some screen shots that may help you.
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

much obliged, although it's nearly midnight here so i'll try tomorrow

---

### Post by overdrank on 2007-07-08
> **makinde said:**
> much obliged, although it's nearly midnight here so i'll try tomorrow

Good luck!:KS

---

### Post by makinde on 2007-07-09
k this is confusing can anyone give or make a guide on how to partition manually?

---

### Post by tetsura on 2007-07-09
1. Resize your windows partition to leave however much free space you want for linux
2. Create an ext3 partition for your main linux partition, this will be '/'
3. Create a linux swap partition, i believe this is supposed to be half of your physical memory, for example if you have 1gb of ram, make your swap 512mb.
4. Then install linux to the newly created linux partition.

I wouldn't do what I've said unless someone else confirms it though, i don't want to be responsible for screwing up someone's pc lol, but I'm fairly sure this is what I did.

---

### Post by makinde on 2007-07-09
Ok I thought i was up to grips on this but apparently not, I'll upload a screenshot and if anyone can, could you point out what to do?

[http://http://img512.imageshack.us/my.php?image=screenshotlk2.png]("http://http://img512.imageshack.us/my.php?image=screenshotlk2.png")

---

### Post by az on 2007-07-09
I think you should just defragment your Windows partition and try the installer again.  It should offer you the option of guided partitioning while shrinking the windows partition.

---

### Post by makinde on 2007-07-09
I defragmented my hard drive but it didn't do anything to the partitioner

---

### Post by az on 2007-07-09
I hope you mean "defragment" instead of "formatted"...

How much free space is there?  (I cannot see the image you posted...404...)

---

### Post by makinde on 2007-07-09
ah sorry about that didn't notice i said that. Yeah i meant defragment. here's the image again [http://img129.imageshack.us/img129/668/screenshothd6.png](http://img129.imageshack.us/img129/668/screenshothd6.png), by the way I found this, shuld I use it first? [http://img407.imageshack.us/img407/5599/screenshot2um5.png](http://img407.imageshack.us/img407/5599/screenshot2um5.png)

---

### Post by makinde on 2007-07-10
ok this isn't to do with ubuntu, but for some reason windows no longer works, I might just use the whole hard disk after all

---

