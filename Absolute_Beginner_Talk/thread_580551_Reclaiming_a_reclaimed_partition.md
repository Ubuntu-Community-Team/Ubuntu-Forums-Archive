---
title: "Reclaiming a reclaimed partition"
date: 2007-10-18
forum: Absolute Beginner Talk
---

### Post by soapboxdevil on 2007-10-18
A good while ago, after hearing so many good things about it, I opted to give Ubuntu a try with the live install CD.  I believe it was Edgy.  Things went relatively flawless.  I had to get some minor support to get my wireless card working but the install was otherwise fantastic.  Not a week later Feisty was released and I had the system automatically update to the newer version.

This broke everything.  After spending hours on forums and support sites trying to get my wireless, sound, and video card working properly I gave up.  I used the Disk Manager in XP to reclaim the partition previously housing a busted Ubuntu install for Windows use once again.

Now Gutsy has been released and the live CD worked like a charm.  Everything but sound was working right from the CD and I'd much rather go without sound than my internet and a properly functioning video card.  I'm wondering if there's a way to reclaim my reclaimed partition for a fresh Gutsy install.

I tried the 'manual' partition option when attempting to install but was stuck trying to figure out how to use only that smaller partition I'd already created.  Any help would be super as I'm truly ready to give Ubuntu another shot (but not at the expense of having to create yet more partitions.)

Thanks to anyone with advice.

---

### Post by mrvertigo on 2007-10-18
couple routs here, one defrag windows and resize your partition, 
you said theres a smaller partition you created? ........... why not there?
Buy a cheapo 40 gig or less drive from a comp resale shop and install on that to alleviate some xp loss headaches

theres more but i'm tired anybody elce got any ideas?

---

### Post by soapboxdevil on 2007-10-18
Well I have an 80Gig which I'd installed Ubuntu on a while ago.  I made a 10Gig partition for this.  Ubuntu broke and I got lazy and I reclaimed the partition for Windows.  I now have a 70Gig partition (of which only 12 is remaining) and the 10Gig partition that USED to be Ubuntu but is now an empty windows formatted partition.  I'd like to use that one again for a fresh Gutsy install.

I'd tried to install Gutsy to this partition via the Live CD installation but was lost as to how I'd accomplish this.  The only option it seemed to give me was to repartition the 70Gig partition, which I'd prefer not to do.  I saw no options to reclaim that previously partitioned 10Gigs, though I'm sure I must just be missing something.  I'd personally rather not have to buy an extra drive just to test out Gutsy.  I would just really, really like to re-use that 10Gigs.  It's only for testing purposes anyway to see if Gutsy and Ubuntu are right for me. 

Thanks for the options.  I'll keep looking into it.

---

### Post by mrvertigo on 2007-10-18
ok, when the partition screen comes up hit advanced and you'll be looking at a visual representation of your drive in bar form and you'll see at the far right a 10 gig peice deleet that partition, create a new one that is about 1.5 times your current ammount of ram then create annother out of the rest. the one that is 1.5 times your ram is your swap partition, so format it as swap and dont mount it the other one format as ext3 and mount it as /

you could get more involved and create more partitions but to make things easy this is the best way.

---

### Post by soapboxdevil on 2007-10-19
Thanks millions.  This worked perfectly.  I'm now test rockin' Ubuntu.  Thanks again!

---

### Post by mrvertigo on 2007-10-19
no problem!

---

### Post by soapboxdevil on 2007-10-19
Though now I seem to have an issue with the whole shebang locking up within a few minutes of booting.  If I hover my mouse over any of the top screen menu options I lock up and have to hard boot.  I'd gotten an error during installation but it was phrased as if it wasn't a big deal (I believe the error message said to look into it after installation so I'd assumed it wasn't a biggie).  I may re-download, re-burn and re-install over this current installation to see if that remedies things, but this must wait until I'm home from work.

At least now I don't have to lose anymore disc space though.  I'd thought things seemed too good to be true when the live CD worked pretty well.  I'm giving myself the weekend to figure it out and if I can't then Ubuntu is certainly not for me as I don't have the free time to dedicate to get the Masters Degree in Linux development just to get things working properly.  

I appreciate the assistance with the one problem, but now I've got the whole can of worms to deal with.  If I have the patience for it, I may actually get to use it for a couple of hours this weekend.

---

