---
title: "Partitioning Hard Drive"
date: 2007-04-25
forum: Absolute Beginner Talk
---

### Post by bwallum on 2007-04-25
Hi

I'm trying Ubuntu again after a lay off. After 4 weeks with Edgy I had a command line only interface.

So, once bitten, I return and think that I would like to set up a partition to run Ubuntu and fall back on Windows when I had to do some real work in a hurry. I really, really want Ubuntu to win by the way and I understand that you only have a small team. Their performance is marvellous in the circumstances.

So, I have followed the 'official route' to ensure minimum of problems. The first one encountered is partitioning a bit (44GB) of a 120GB hard drive with little use and a non system drive.

I downloaded the Feisty CD, checked it, no errors. I ran the CD from the CD drive to see if it was ok. Great, it was stable.

Using GNOME Partition Editor I sliced off 44Gb as format swap, NO HELP HERE TO ADVISE WHICH FORMAT TO CHOOSE FOR INSTALLING UBUNTU! The naive user has to guess!

Then I check by shutting down and rebooting in Windows. Throws an error message and wants to check integrity of hard drive, does that and passes, hard drive now confirmed by Windows as 44GB short as anticipated. Great!

Now I shut down and get back into Ubuntu. Now go to System/Administration/Install. Told that no room for root! TRY TELLING ME THAT EARLIER PLEASE! THERE IS NEITHER OPTION NOR ADVICE TO PARTITION FOR ROOT!

So here I am, not willing to risk another 4 weeks of downward spiral. The help systems are totally chaotic, many are not there at all where they should be ALONGSIDE THE FORMS IN AN APPLICATION and Ubuntu looks like its about to collapse because nobody has the time to put in proper help. It is not good enough to say try this, try that, point to out of date info and expect the new user to have your enthusiasm in all things technical. They just get screwed up with the installation and leave it, possibly coming back later, very wary. Is that what you are really trying to achieve?

Can we just forget the next 6 monthly release and try some CONSOLIDATION instead. You will get MORE NEW USERS this way. Get the HELP properly running.

If you can also find time to help me get my partition sorted and tell me what file format to pick from the GNOME Partition Editor for 'root' I would be most grateful.

Kind Regards
Bob Wallum

---

### Post by ImpelGD on 2007-04-25
> **bwallum said:**
> If you can also find time to help me get my partition sorted and tell me what file format to pick from the GNOME Partition Editor for 'root' I would be most grateful.

ext3.

You may find [http://psychocats.net/ubuntu/index.php](http://psychocats.net/ubuntu/index.php) and [http://psychocats.net/ubuntu/partitioning](http://psychocats.net/ubuntu/partitioning) useful.

---

### Post by mikewhatever on 2007-04-25
[http://psychocats.net/ubuntu/partitioning](http://psychocats.net/ubuntu/partitioning)
[http://psychocats.net/ubuntu/installing](http://psychocats.net/ubuntu/installing)
These are very well known how-tos on planning partitions and installing. Hope they are step by step enough. If there is something you don't understand, do ask. There is no need to go alone into the deep waters.

To install Ubuntu, you need to setup at least two partition, root (mounted as /) and swap (mounted as swap). The size of swap should be roughly 1.5-2 times the size of RAM. The rest of the unallocated space you took from the Windows partition should go to the root one. There is also an option of resizing hda1 and using the free space, a good choice if you find the how-tos too confusing.

---

### Post by bwallum on 2007-04-25
Thank you gentlemen, a very quick response. May I ask you you to implement that advice in GNOME Partition Manager, particularly as it is critical to a new starter. Please tell the new starter how they should partition the hard drive and which file formats they should choose for the partition. It is not a question of the advice is out there somewhere, it is a question of the advice being to hand for the naive user when they need it.

I used to code c++, I am too slow now compared with a younger (18-22) man. I have however delivered very large international systems using very bright people with intellects greater than mine. The one mistake they all make is that the user will have their knowledge. They can't think dumb (which is normal/advanced to the masses).

Count me in for any project management, mentoring role (professional business oriented coach to individuals and teams). I have volunteered but no take up so far. Test me please.

Away to implement your advice

Kind Regards
Bob

 

Count me in for

---

### Post by mikewhatever on 2007-04-25
I think most of us here are simple Ubuntu users with relatively little knowledge of Ubuntu. Some are young, others are older, some are fast and others slower, for all, it takes some time and effort to learn something new. There might be some gurus around too. 
It seems that there is no lack of tutorials on the web. There may be too many, so that a new user is overwhelmed. That is the disadvantage of the community support.

---

### Post by bwallum on 2007-04-25
Chaotic is the term I would use. Dating the advice would help. "Sorry. not yet implemented, Please visit [http://gparted.sf.net](http://gparted.sf.net) for more information and support." is the response one gets from using the help menu in Gparted (GNOME Partition Editor). I'm sure proper help will come, I am just trying to get there soonest with this posting. 'Help' is a bigger issue than coding in every system I've worked on.

Don't underestimate yourself, 'simple Ubuntu user' is an oxymoron. 

It's great to get such a rapid and sound response. 

Best Regards
Bob

---

