---
title: "2 Partitions or 3 Partitions?"
date: 2006-08-03
forum: Absolute Beginner Talk
---

### Post by cheway on 2006-08-03
Hi all,

I'm just coming to the end of my Linux honeymoon (Windows was deleted last night from the dual boot I had) - my intention now is to wipe the entire disk and start all over again.

Right now, I have two partitions - 1 gig of swap, and the rest is the ext3 (root?).

However, I hear that it's good to have a third partition for the home folder, is this right? I understand that it's so you can easily wipe the OS without touching the documents, music, etc - but at the moment, there is a '/home' folder on the ext3 partition anyway! How is making an actual home partition any different?

---

### Post by nixclusive on 2006-08-03
> **cheway said:**
> ...t's good to have a third partition for the home folder, is this right? I understand that it's so you can easily wipe the OS without touching the documents, music, etc - but at the moment, there is a '/home' folder on the ext3 partition anyway! How is making an actual home partition any different?

Making an actual home partition will mount that partition on /home. It would still look to be same, just that the actual data is contained in a different partition....tip: go ahead and make that home partition.

---

### Post by cheway on 2006-08-03
Ok then, I see what you're saying, I'll do that.

Now, who wants to recommend some partition sizes to me?

I have 120 gig hard disk in my laptop, which has 1 gig RAM, so I was thinking...

-2 gig swap partition
-10 gig ext3 root (is 10 gig a bit overkill?)
-and the rest for my home parition (ext3 of course)

What do you reckon?

---

### Post by Drakkor on 2006-08-03
As you can see, on hard drive 2, I have 3 partitions,a 20G root,35G media/data,and a 1.5G swap,so if I have to reinstall the OS all my media and data on the 35Gb partition is not affected in anyway. :)

---

### Post by cheway on 2006-08-03
Hmm, so 10 gig might not be enough then

So what is the extended partition all about? I see that you have your swap under this, what's the advantage of that?

---

### Post by wpshooter on 2006-08-03
> **cheway said:**
> Hi all,

I'm just coming to the end of my Linux honeymoon (Windows was deleted last night from the dual boot I had) - my intention now is to wipe the entire disk and start all over again.

Right now, I have two partitions - 1 gig of swap, and the rest is the ext3 (root?).

However, I hear that it's good to have a third partition for the home folder, is this right? I understand that it's so you can easily wipe the OS without touching the documents, music, etc - but at the moment, there is a '/home' folder on the ext3 partition anyway! How is making an actual home partition any different?

It is **my understanding** that it is different, in that, if you make a separate partition for /home and when you need to reinstall your O/S then you can do so with out interrupting the information in /home.  I think also it would make backing up the info in it simpler.

---

### Post by OffHand on 2006-08-03
1GB Swap is more than enough, trust me. Unless you are doing insane stuff the swap is almost never used (or just a few MB).

10 GB for the / is fine and give the rest of the space to /home.

---

### Post by Drakkor on 2006-08-03
The "extended partition" is not really a partition,it's just to differentiate between the primary and logical partitions. :)

---

### Post by cheway on 2006-08-03
Woah, slow down cowboy, what IS the difference between primary and logical partitions? #-o  Do I need to use a logical partition when I reinstall everything?

---

### Post by anaconda on 2006-08-03
well

10GB /root partition can easily become too small! If you install lots of programs, (or fewer BIG programs), because all the programs you install go to /root partition (and ofcourse all of ubuntu) Some people here have made 10GB /root partitions, and gotten those full...

to /home goes your own settings, and your personal data, like the documents you write, movies you download your music etc..

Personally I keep /home in the same partition than the rest of ubuntu, BUT I have a separate data partition, where I keep my movies, pictures, documents, music, books, and anything personal..And all BIG data. So it is like a home partition, without the personal settings etc.. This way it is easier to use my data partition between the operating systems I use.. dont have to use same /home with 2 linux distros, which would need different personal settings anyway..

Ok too much rambling already, but if you have 120GB hard disk (and all to linux), you might want to give root partition 30GB, 1GB is quite a lot for swap, but not much from your disk. so who cares.. And the rest to your /home partition.
(I would make the rest to a data-partition which has nothing to do with the OS, eg. not home.. but you do as you wish..)

---

### Post by stoft on 2006-08-03
Seeing as everyone else has an opinion, here's mine: 20GB for /, /swap = RAM size + a few MBs, /home on a separate partition. Look around here, google etc. for details on howto do it all. Simply put (corrections/improvements welcome):
1. backup valued data, including everything under /home
2. partition your drive (with QT Parted e.g., resizing the old partitions, creating the new)
3. copy /home from your backup to the new partition
4. change fstab to point to the new location

Just a small comparison, My kubuntu is on a 6GB partition and after having installed important things like Opera, build-essentials, python programming stuff etc, about 2GB left. How much space you need is very personal but, it doesn't have to be a lot but if you've got the space a little extra can't hurt. Remember to clean apt's cache once in a while and you'll have space to spare.

---

### Post by anaconda on 2006-08-03
Oh and if you think  that 30GB is too big, then you can always make a data folder to it, and fill it up, so no space wasted..

And the difference between logical and primary partitions is that all logical partitions are in one primary partition (called an extended partition) there is no limit to the number of logical partitions you can make, BUT the maximum number of primary partitions is always 4. In linux the difference between primary and logical is small, because you can eg. install linux to whicever you want. Windows needed (or used to need) a primary partition to install to... 

I would use ONLY primary partitions if I would need 4 or less partitions.
because if your extended partition gets corrupted (eg. from boot sector) you lose all your logical partitions.. ANd data recovery would be more difficult than from primary partition. Because you would have to go through the whole extended partition to sniff whre each logical partition starts and ends.. 

But usually most people dont differentiate between primary and logical partitions.. so you dont have to either, just remember that primary is better and if you need more than 4 partitions make 3 primary ones and the rest to an extended partitions, and not windows style.. 1 primary for windows, and all the rest to an extended partition..

---

### Post by cheway on 2006-08-03
I see what you're saying - definitely a good idea for someone with more than one operating system. However, I think that I'm going to stick to making a home partition.

Ok, so after installing a fresh copy of the Ubuntu system, which actions actually increase its size? Because all of the programs and whatnot go into the home directory right? Is it just the updates? Surely 10 gig is overkill in this case?

Right, I've just been to my root folder, and in the name of science I have selected everything EXCLUDING the 'home' folder - and the file size has come to 12.5 GB (some contents unreadable) - is this relevant in any way? I think that 10 gig for root is perhaps underkill as opposed to overkill.....

---

### Post by anaconda on 2006-08-03
yep 10GB is underkill.

All the programs you install go to / not to home. To /home goes your personal settings and your personal data.. not neccessary wery much unless you download movies, music etc..

---

### Post by cheway on 2006-08-03
That's the thing mate, I have about 30 gig of music, and I keep a lot of movies and series on my hard disk as well, which I intend on putting into my home directory.

Ok, as of now, I have all the programs I need pretty much - just need to install limewire, azureus, and something that can read guitar tabs - I think those are the only biggies. With 12.5 gig used already, I think I'm going to go for a 20 gig root partition, as stoft said.

Thanks a lot everyone, I've learnt a lot this evening.

---

### Post by Drakkor on 2006-08-03
Yeah, cheway  since you've got what a 160 GB Drive, maybe go for 30 gigs root partition,as you saw from my screenshot,which is a 20 GB partition,and it's already 55% used up.But I have almost everything I need there,but who knows,lol  :p

---

