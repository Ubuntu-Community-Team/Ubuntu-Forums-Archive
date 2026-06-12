---
title: "[SOLVED] Going to daul boot need advice on file systems and partitions."
date: 2008-02-07
forum: Absolute Beginner Talk
---

### Post by travismoore on 2008-02-07
Well i have my PC up and working again after it died(or i killed it) not sure which.

So I got VMware and had a go on Ubuntu and i have to say its awesome and it took me less that 5 minutes to realize it =D

Anyway i need to know about file systems and partitioning so here it goes.

Ext3 vs ReiserFS ?

Also I have a 80GB hdd (primary) and 500GB hdd (secondary).

I've heard many things about different ways of going about this but i am still unsure. I would like to have the 80GB as free as possible so i can re-install windows if it gets sluggish(although i dont intend on using windows much. I heard i can store the /home somethere else? Also i want to use 500GB for all storage(or as much as possible).

So i know it should be on the 80GB: 40GB windows and 38-39GB ubuntu with 1-2GB swap.

What i need to know is what to do with the 500GB can i access NTFS from ubuntu (i.e my music ect on windows) or do i need FAT32? Also just how i should partiton the 500GB out.

Oh and how does ubuntu feel about motherboards onboard(shared) graphics? ( i am planning on getting a new card but dont have the cash atm)
(SiS Mirage Graphics)

Also i already have windows taking up 3GB on the 80GB and 50GB on the 500GB (both are NTFS) can i install with out messing them up and do i need to de-frag them?


Cheers,

Travis

---

### Post by Rocket2DMn on 2008-02-07
Ext3 is the default, you should probably just go with that for your root partition.  You CAN access ntfs from Ubuntu since there is the ntfs-3g driver (comes preinstalled in Gutsy).  You can also use FAT32, but it's not necessary and it has the 4GB file size limit.  I wouldn't even bother touching your 500GB drive if you already have it setup how you like it.
You can create a separate partition on your 80GB drive for /home if you'd like.  Perhaps something like 15GB for root and 25GB for /home (though you have a separate data partition already).  The 2 purposes of having a separate /home directory are so 1) you can reinstall without losing your settings and 2) so you can reinstall without having to move your data back from another drive.  Many people find this very convenient.
Your onboard graphics should work, if you have problems, start a new thread for it and we will help you troubleshoot it (it's fairly easy).
Welcome to Ubuntu!

---

### Post by travismoore on 2008-02-07
Thanks!

Would it be worth putting the /home on the 500GB?

And how easy would it be to reinstall windows if needed without affecting ubuntu?

Also how easy is this to do in the ubuntu set up?

How and will compiz run on my shoddy graphics?

---

### Post by Rocket2DMn on 2008-02-07
I wouldn't take all 500 GB for /home, that seems like overkill to me.  You can reinstall windows at any time, you will just have to recover GRUB - [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)
Ubuntu setup is pretty straightforward, partitioning is the toughest part.  Not sure how compiz will run, you'll just have to check it out for yourself.

---

### Post by travismoore on 2008-02-07
I wasnt thinking the whole 500GB but just a section like 50-60GB?

Cheers for the link but I run XP, mainly because vista is not stable highly anoying and slow lol

Oh yea and is it worth defraging windows?

---

### Post by Rocket2DMn on 2008-02-07
Yes, if you resize a drive, you will HAVE to defrag.  It is convenient to install windows first otherwise you need to recover grub as shown.  That link I sent you isn't just for vista, the part you would probably want is [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows#head-bf3232f10ddf1b078de064622ccbb25225cdb3c0](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows#head-bf3232f10ddf1b078de064622ccbb25225cdb3c0)
You could certainly use 50-60GB for /home on your second hard drive (I hope it's an internal drive...).
So if you are going to keep your current XP setup and add Ubuntu, defrag your hard drives at least once (maybe even twice!), then boot from the LiveCD and resize your partitions with System->Administration->Partition Editor - it is convenient to set your partitions before you install, but you can also do it during the install, it's your call.

---

### Post by travismoore on 2008-02-07
Yep both are internal.

Cheers for all the help im going to go install now, wish me luck =D

thanks,

Travis

---

### Post by Rocket2DMn on 2008-02-07
GOOD LUCK!  Welcome to Ubuntu :)
PS: please have your important stuff backed up before you start, fiddling with partitions can be dangerous, and you never know...  Shouldn't be a problem, but sometimes things happen (most typically people accidentally overwrite partitions they don't intend to).

---

### Post by travismoore on 2008-02-07
I'm not 100% sure how i can back-up my stuff because i dont have another hard-drive and DVD's are far to small.

---

### Post by Rocket2DMn on 2008-02-07
You should always have a backup drive.  I would suggest investing in a good external USB drive - they are not terribly expensive and definitely worth the investment (500GB drive would be good).  You could probably go ahead and install and be just fine, but if you want to play it safe, get a backup drive first, backup all your data, then install Ubuntu.  Alternatively, if you want to install now, don't put /home on your second drive and put all your data on there - then don't touch this drive during the install.
My suggestion would be to just go get an external USB drive, then install, since you really should have one anyway.  Having good backups is extremely important, regardless of your operating system.

---

### Post by travismoore on 2008-02-07
Yea well i just fixed my pc so im strapped for cash so i will have to just go the linux install on the 80GB and leave the 500GB but can i move it at a later date?

---

### Post by bill516 on 2008-02-07
If you are trying to figure out partitions, here is the best site I have found for that issue and a number of others:

[http://www.psychocats.net/ubuntu/](http://www.psychocats.net/ubuntu/)

Once there you will see a list of topics on the left side of the page.  About four topics down you will find "Planning Partitions."

The entire site was very helpful to me when I started out a few months ago.

Whatever you do clean up your drive (or drives) before you do anything else.  Get rid of the junk and defrag.

Then, using an external drive (or whatever) copy off all of your Windows material, or at least those "I can't live without 'em" files.

From what you say that 500 Gig drive is suff8iciently large enough to partition and use part of it for your windows backup?  Just a thought.

Go for it.  Ubuntu will be a good learning experience and the people on these forums really are terrific about helping.

BTW, I run XP and Ubuntu 7.10 from a 100 Gig (nominal) HD on a laptop.  My problems, when I have them, are user related!  Forums have helped me a number of times.

Have fun!

---

### Post by Rocket2DMn on 2008-02-07
You can move your /home later if you want.  Right now you may not want to even set a /home partition and just have it as part of the root partition (so during install you just have root partition + swap).  Then later you can move /home to a separate partition based on this tutorial - [http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

### Post by travismoore on 2008-02-07
Cheers, i will have a go =D

I don't see how you mean partiton to back-up?

---

### Post by Rocket2DMn on 2008-02-07
Long story short: You should always back up all your important data on a second device, like an external hard drive (or internal if you still have space for it).  This means if your primary hard drive fails, either in hardware or software, you won't lose your important stuff.  Failure will happen, it's just a matter of when (regardless of your OS).

---

### Post by travismoore on 2008-02-07
Alright well cheers I'm off to install cya!

---

### Post by Ghuloomo on 2008-02-07
About your NTFS , don't touch it. Before you could only read form NTFS files, but now the problem is totally solved. After installation go to Applications -> Add/Remove and search for NTFS Configuartion Tool

---

### Post by travismoore on 2008-02-07
> **Ghuloomo said:**
> About your NTFS , don't touch it. Before you could only read form NTFS files, but now the problem is totally solved. After installation go to Applications -> Add/Remove and search for NTFS Configuartion Tool

I dont get what u mean?

---

### Post by karlo on 2008-02-07
> **Rocket2DMn said:**
> You should always have a backup drive.  I would suggest investing in a good external USB drive - they are not terribly expensive and definitely worth the investment (500GB drive would be good).  You could probably go ahead and install and be just fine, but if you want to play it safe, get a backup drive first, backup all your data, then install Ubuntu.  Alternatively, if you want to install now, don't put /home on your second drive and put all your data on there - then don't touch this drive during the install.
My suggestion would be to just go get an external USB drive, then install, since you really should have one anyway.  Having good backups is extremely important, regardless of your operating system.

I definitely agree with this person's idea! I'm now planning to invest for it. Although what happens if the backup external hard drive crashes? How long will it last? It it necessary to use FireWire?

---

### Post by Rocket2DMn on 2008-02-07
> **karlo said:**
> I definitely agree with this person's idea! I'm now planning to invest for it. Although what happens if the backup external hard drive crashes? How long will it last? It it necessary to use FireWire?

External hard drive are just as capable of crashing as internal drives.  However, the whole purpose of having backups is *redundancy* - if your backup drive crashes, either fix it ASAP or get a new one so you always have your data in more than 1 place.  The likelihood of your primary drive and your backup drive failing at the same time is much more limited.  Personally, I have multiple backup drives in separate locations so even if my apartment building burns down, my data is still safe (up to a certain backup date, anyway) - however, this is overkill for most people.
An external drive should last for years, and it is not necessary to use firewire.  Firewire is faster and more efficient, but can also be more hassle to setup - USB works perfectly fine for most people.

---

### Post by Ghuloomo on 2008-02-09
> **travismoore said:**
> I dont get what u mean?
If you have any NTFS filesystems you can't write on them when using ubuntu. You can open the files in that partition, see them, read them, but if u edit them, and save, it gives u an error. Shortly: Writing is not allowed.

But if u install "NTFS Configuration Tool" problem is solved

---

