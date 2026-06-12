---
title: "I've got the &quot;first time&quot; jitters!"
date: 2005-09-08
forum: Absolute Beginner Talk
---

### Post by marzboy on 2005-09-08
9-8-2005

Holy Emulators, I can't believe I did it!  After having been a longtime Winxx user I've now decided to step up to the plate and join the folks on Planet Linux! Reading Linus Thorvald's autobiography was the catalytic force.  I'm by no means new to PCs or computers, but installing Ubuntu Linux for the first time is causing me some apprehension.  One axiom that I've learned after having been in the IT field for sometime  is to take things slowly, step-by-step, and not to assume anything.  If you run into a snag - take a break and grab a cup of Joe, or just chill out and pick up the gauntlet later on.  That having been said, I'm faced with waiting for the October release of Ubuntu to arrive - or I was thinking that I might just attempt a download of the current version.  I'm running Windows XP Home Edition on my laptop, and did a little research on the partitioning features of XP.  What I'm not sure of is how to coordinate the download/install and the partition:  Does one partition first and then install?  If I did in fact partition the hard drive first,  does there exist a facility in the Ubuntu download (or CD) to direct the install to the area partitioned for that purpose?  Y'know . . . really, I'm asking this question for ALL of us newbies - folks who are really enthused about Linux and want to get rockin' & rollin' and join the team . . . but who are initially afraid that the install itself will not work and we'll blow it on opening night! 

Any feedback/words of encouragement would be greatly appreciated.   Thanx & God Bless.               Msrz

---

### Post by matthew on 2005-09-08
First off, welcome! As I read your post I think you have the right attitude and you are going to do very well. Humility and taking things slowly while listening and asking the right questions make this process pretty easy--you have to think, but it is definitely do-able.

My recommendation is to start with the current release, Hoary, simply because it is stable. However, you seem to be a person willing to take calculated risks and since you won't start of with anything vital running on your linux partition, you probably wouldn't have any major problems installing Breezy either...so I guess I'm waffling a bit on this one. I usually wouldn't recommend a development release for a newbie, but you also don't seem to be the type to post "I tried x and it didn't work and now I think linux is horrible and will unless you tell me how to fix it without giving you any information whatsoever about my setup." So, you have my advice on that one. Do as you will...I trust your judgment.

I would start by partitioning your hard drive. Before you do that, go into XP and defragment the drive. Back up EVERYTHING. Check your backup. It isn't likely that anything will be lost, but it could be, so check your backup method again and make sure it worked. You've done that? Good. Ok. Resize your XP partition as you wish. You can leave the rest of the space unformatted if you want. The Ubuntu installation process can format/partition the rest for you easily.

Start the installation with the cd. Make sure you put Ubuntu on two partitions, a smaller one (say 10 Gb) for the root directory (aka /) and the rest of the space in /home. This will allow you to change/upgrade your linux installation without changing/losing your settings or files.

There is a lot more I could tell you, but instead I will refer you to the links in my signature and just try to reassure you--if you pay attention to what you are doing and go slowly and thoughtfully like you described you will be successful.

Finally, if you get stuck or have any problems whatsoever, come back and start a new thread. These forums are some of the best anywhere and they alone make Ubuntu a great choice for your first entry into the linux world.

---

### Post by az on 2005-09-08
[https://wiki.ubuntu.com/forum/installation/Partitioning](https://wiki.ubuntu.com/forum/installation/Partitioning)


I would say just take the default and only create one partition and put everything there.  Just free up some disk space using the partitionner in the Ubuntu installer and then use "guided partitioning" to let the installer create the rest (two partitions, actually, one real one and one swap.)

---

### Post by poofyhairguy on 2005-09-08
Welcome.

[QUOTE=marzboy] If I did in fact partition the hard drive first,  does there exist a facility in the Ubuntu download (or CD) to direct the install to the area partitioned for that purpose? [/QUOTE]

Yes, you must chose to "manually edit partition table" in teh Ubuntu isntaller.

This will tell you how to burn the CD:

[http://xmastree.34sp.com/ubuntu/burn/](http://xmastree.34sp.com/ubuntu/burn/)

Basically, it must be not a normal CDrom. Since you value your data, I would look at this as well:

[http://www.tipmonkies.com/2005/06/23/linux-filesystems-and-partitioning-a-primer/](http://www.tipmonkies.com/2005/06/23/linux-filesystems-and-partitioning-a-primer/)

Good luck, we are here to help.

---

### Post by Kyral on 2005-09-08
Hooray for new guys that don't go "OMG! This isn't like Windows, Linux suxxors"

Cookie for you! :D

---

### Post by weasel fierce on 2005-09-09
Hope everything works like a charm :) 

Its a big big world out there.

---

