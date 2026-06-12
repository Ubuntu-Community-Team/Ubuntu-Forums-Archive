---
title: "Swap Size?"
date: 2006-08-25
forum: Absolute Beginner Talk
---

### Post by superwazn on 2006-08-25
i read the swap partition should be 2-1.5x the size of your RAM, but also something about if its too big it can be a waste. does "too big" mean more than 2x your RAM, or is too big mean more than it will use? i'm wondering because my RAM is 1GB, i know what swap is used for and i think having a 2-1.5GB swap wont be fully used.

---

### Post by Paul133 on 2006-08-25
I'm pretty sure "too big" means that it's a waste. It's almost always a waste when it's more than 2x your RAM. I don't think there are any problems with a very large swap, but it wastes space!

---

### Post by superwazn on 2006-08-25
thats what i mean, even though the drive i have is gigantic, i want to conserve it as much as i can, so should i make the swap smaller so im not wasting half of it? maybe make it 500mb or 750? also, how much does ubuntu need to run? i also want to make that partition as small as comfortably possible

---

### Post by taurus on 2006-08-25
How much swap does Ubuntu need depends on how much RAM do you have and what do you plan to run on your machine?  If you plan to do a lot of multimedia stuff, then you need a lot of RAM and large swap space but if you only do some basic stuff like web browsing, watching movies, listening to music, runnig OpenOffice, then 512MB of swap should be enough...

---

### Post by superwazn on 2006-08-25
im still wondering how big of a partition i should give to ubuntu. the drive i have now has 100gb of stuff, so i give 1gb to swap and then how much for ubuntu? 5gb? 10?

---

### Post by taurus on 2006-08-25
Again, if you have 1GB of RAM, you don't need 1GB of swap space.  512MB of swap space is plenty!!!  Also, it depends what's your plan for Ubuntu!  If you depends to store a bunch of movies and mp3s, then you need a large partition for it so give it as much space as you can and you don't have to worry about space later...

---

### Post by superwazn on 2006-08-25
i'm sorry, i dont think i have been asking a very clear question. i'm trying to install ubuntu on my external hard drive, that has 200gb unused space and 1 partition in ntfs format. i think what i mean to ask "how should i add/re-partition this disk so i can run ubuntu from it and still have all my files?"

---

### Post by Fedz on 2006-08-25
For swap I gave it 1GiB ... as for partition I divided my drive in half (which is 85GiB).

I was attempting to dualboot using Grub but, something went wrong and I now I can't dualboot. It boots straight into Ubuntu ... not bothered as such as I'd backed-up everything onto DVD before installing Ubuntu but I have a partion I can't access (AFAIK).

I prefer Ubuntu anyway :D

Kind regards

---

### Post by Jerome36 on 2006-08-25
So you want to know how much you should set asside for the main/root partition of Ubuntu?  Well Ubuntu needs at least 2 or 3 gigs, but it's going to depend on what you want to do with it.  If you plan on putting media, like music and what not, in Linux, you'll want to give it more.  If you are going to dual boot, with Windows, you can always have Ubuntu read the Windows partition, and view your files that are in Windows.  Really, it's up to you.

I recently setup my Sister's computer to dual boot, and her hard drive is only 12 gigs.  I split it in half, so Windows got 6 and Ubuntu got 6.

---

### Post by Fedz on 2006-08-25
> **Jerome36 said:**
> If you are going to dual boot, with Windows, you can always have Ubuntu read the Windows partition, and view your files that are in Windows.  Really, it's up to you.

Hi how do I go about doing this?

In Ubuntu I can see the partition but, how do you access it and can I copy files from that partition to Ubuntu?

Tia

---

### Post by superwazn on 2006-08-25
ok, so 512mb for swap, and since i will be doing a fair bit of multimedia, give 7-10gb for ubuntu. just wondering, but, besides OS function, what is the space you give ubuntu for? wouldn't another partition full of data be just as easily accesable? thats how i was running windows...

---

### Post by Crosbie on 2006-08-25
My Ubuntu setup is using just under 6 Gigs for the root system and 4 for the /home partition.

---

### Post by SleepJunkie on 2006-08-25
To try to answer both questions:

If you have a gig of RAM, 512MB will be fine, if you have the space, make it more, it doesn't really matter.

I set up my partition like this.

/dev/hda1 - boot 512MB
/dev/hda2 - xp 80GB
/dev/hda3 - swap 1GB (I have 512MB RAM)
/dev/hda5 - / 5GB
/dev/hda6 - /home about 28GB

I still have about 40GB unformatted space on the drive.




> **Fedz said:**
> Hi how do I go about doing this?

In Ubuntu I can see the partition but, how do you access it and can I copy files from that partition to Ubuntu?

Tia

[http://www.ubuntuforums.org/showthread.php?t=217009](http://www.ubuntuforums.org/showthread.php?t=217009)

---

