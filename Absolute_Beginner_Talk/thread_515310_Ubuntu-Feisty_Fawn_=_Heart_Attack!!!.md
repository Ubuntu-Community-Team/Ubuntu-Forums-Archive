---
title: "Ubuntu-Feisty Fawn??? = Heart Attack!!!"
date: 2007-08-01
forum: Absolute Beginner Talk
---

### Post by 6Realms on 2007-08-01
Hello Everybody!  Just got back on with my PC after experiencing the loss my Windows XP while attempting to install Ubuntu onto my 2nd Hard Drive.  Nobody has mentioned the fact that this is par for the course 80% of the time, when trying to install "Fiesty Fawn".  I'm not upset, I look at this as part of the "Learning Process", when working with Computers.  Starcraftman; Without you and your support, I would not have gotten this far, to you I'm thankful.  Something to pass on to all of you is that if your a subscriber to, "Smart Computing"  Magazine, You get a "Toll Free" Telephone Number off their Web Site with live one on one support to walk you through your toughest times.  I wanted to share this also with you all.  My next mission will be to "Again" installing "Fiesty Fawn" on my 2nd hard drive.  Thank you.  Sincerely, 6Realms:rolleyes:

---

### Post by pollywog on 2007-08-02
I've never had any problem setting up dual boots w/ feisty or edgy. I will however say that I liked how edgy partitioner had a manual option that took the user straight to gparted for partioning. before I install ubuntu I use my gparted disk: [http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828](http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828)
to manually resize the windows partition, leaving the ubuntu designated space unallocated initially. Then choose the option to install in the largest continuous free space during the ubuntu install. The only issue that I have had with dual booting w/ 2 hard drives is Grub being written to the wrong hard drive, causing boot up errors. I was able to fix that by going into BIOS at boot up, and changing the boot order of the hard drives. Good Luck- P.W.

---

### Post by Tux Aubrey on 2007-08-02
> this is par for the course 80% of the time

Really?  I have installed Ubuntu (Breezy, Dapper, Edgy and Fiesty, as well as Edgy Xubuntu, Ubuntu Studio and Fluxbuntu) at least 15 times on six different machines and never had a complete failure of the type you are talking about.  I can't believe that it is very common at all.  But I do hope your next attempt is successful.

With some distros that do have known installation problems it often helps to partition the drive/s manually before doing the installation.  Use a live CD with gparted installed or just get yourself a copy of Rescue Disk (its a worthwhile download anyway) and you can do it graphically.

---

### Post by pat7089 on 2007-08-02
I also have installed Ubuntu several times on dual-boot machines, and never had a problem with Windows XP. What I did was use a second hard drive, like you described, but to ensure that I did not install anything in the wrong place, I unplugged the Win XP hard drive when doing the install.

---

### Post by Steve1961 on 2007-08-02
I've installed Ubuntu many times on my own, friends and customers computers.  I've never had any issues like this when dual booting.  However, I always do the partitioning before attempting installation and I use the alternative CD.

---

### Post by Lord Illidan on 2007-08-02
Neither did I when installing Fiesty Fawn...and I got lots of partitions on my pc. Sounds more like a mistake you did.

---

### Post by Seisen on 2007-08-02
This might help set up Ubuntu and Xp on two different hard drives.

[http://ubuntuforums.org/showthread.php?t=179902]("http://ubuntuforums.org/showthread.php?t=179902")

---

### Post by philinux on 2007-08-02
I had a similar problem with installing Feisty on a second hard drive. GRUB or something buggered up the MBR on my windoze disk. But was recovered with FDISK. After that a friend helped me by changing the connections to the hard drives and making Feisty the primary drive. After that no probs.

---

### Post by Circus-Killer on 2007-08-02
now, before i a say anything, let me just say i could be wrong.

but by the sounds of it, it sounds like the OP just clicked 'next' a bunch of times without reading what was going on. so when it came to partitioning, and 'use entire disk' was already selected, the user just pressed next. i find that a lot of first timers do this.

just a thought, i could be wrong, but it never hurts to state the obvious, since its the obvious things that people overlook the most.

---

### Post by 6Realms on 2007-08-02
First of all, "Many Thanks To All Of you", for all your replies and feedbacks.  I know what your mean about 1st timers, but I tried to set my partitoning  to, 11%, don't know if it worked with everything that went wrong but I do remember setting it at 11%.  Thank's a good idea, you gave about unplugging the XP HD before installing Ubuntu 7.04 on the 2nd HD.  I have a friend who's tech-savy, coming over today to install, Fiesty Fawn, This time I'll just watch him and he'll help me understand what is beaning done so I'll learn.  How can I change my set around and make my Ubuntu my primary HD, I know my friend will know but I still like receiving input and feedback from my [YOU Guys] community.  The last thing is, What is;  "GPartitioning"  and where can I get a, "Rescue Disk"?  Again thank you very much.  Sincerely, 6Realms:KS

---

### Post by LaRoza on 2007-08-02
I think you mean "GParted", see my sig, it is the greatest thing.

---

### Post by Raineer on 2007-08-02
GParted is literally the greatest thing there is, for any OS.

You asked about a Rescue Disk, which I would state is mainly the original install disk, since it is bootable and allows you to make changes to your system even if it is unbootable.

It wouldn't be a bad idea to have something that backs up xorg.conf, menu.lst and other key files that can get fudgered up.  These could easily be restored later on.

---

### Post by matt_risi on 2007-08-02
Ya know what really grinds my gears?

Helpee: I had a problem with x. Can I get some help?
Helper: I've never had a problem with x! Nope, never ever.

Help the guy, don't tell him that you've never experienced his problem.

---

### Post by LaRoza on 2007-08-02
> **6Realms said:**
> First of all, "Many Thanks To All Of you", for all your replies and feedbacks.  I know what your mean about 1st timers, but I tried to set my partitoning  to, 11%, don't know if it worked with everything that went wrong but I do remember setting it at 11%.  Thank's a good idea, you gave about unplugging the XP HD before installing Ubuntu 7.04 on the 2nd HD.  I have a friend who's tech-savy, coming over today to install, Fiesty Fawn, This time I'll just watch him and he'll help me understand what is beaning done so I'll learn.  How can I change my set around and make my Ubuntu my primary HD, I know my friend will know but I still like receiving input and feedback from my [YOU Guys] community.  The last thing is, What is;  "GPartitioning"  and where can I get a, "Rescue Disk"?  Again thank you very much.  Sincerely, 6Realms:KS

The links seemed to help, and the OP asked about GParted, so what is wrong?

-EDIT You, the poster above this, responded without offering help.

---

### Post by Tux Aubrey on 2007-08-02
The rescue disk I was referring to is [THIS ONE ]("http://www.sysresccd.org/Main_Page")- the Swiss-Army-Knife of Linux disks (and it can rescue Windows as well).  

But others rightly pointed out that Gparted is on the Ubuntu LiveCD and most other LiveCDs as well.  BTW, the Knoppix Live CD has a range of great tools.

Strangely enough, I was installing another distro last night and the install failed right at the end.  I went back and partitioned the HD with the LiveCD tool and redid the install without a hitch.

---

### Post by 6Realms on 2007-08-02
Yep!  I'll confess I didn't have a strong enough hold on, "Knowing on what I was doing.  My friend came over and helped me get Ubuntu installed properly and I'm very happy with that.  I can now declare myself an "Official Ubuntu-Fiesty Fawn User".:)

---

### Post by 6Realms on 2007-08-02
Your Right It helps to know the reason for the problem.  Could somebody please tell me what a, "gpartition" is?  I feel so awkward knowing sooo! little about, Ubuntu 7.04.  I actually don't know where to begin so I'm just trying to tackle the events as they come up to me.  Again, Many Thanks.   6Realms

---

### Post by pollywog on 2007-08-10
I don't think that there is someting called a "gpartion", rather the program some of us were recommending is called "gparted" which is the gnome partion editor. It is free and can be downloaded as a " live disk" bootable iso that can be downloaded at:
[http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828](http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828)
burn it to cd like you did your original ubuntu iso image. If your computer doesn't like the latest version (mine doesn't), pick an earlier release and try again. -P.W.

---

