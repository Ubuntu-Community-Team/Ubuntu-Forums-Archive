---
title: "How big my partition should be??"
date: 2007-12-18
forum: Absolute Beginner Talk
---

### Post by taekr on 2007-12-18
I have a dell laptop with 80GB and 2GB Ram. 

I have been testing Ubuntu 7.1 for the last 4days. and now I have decided to move from Windows to Ubuntu.  I plan to use Virtual Box to install WinXP to run some of my favorite programs. I don't play games except Starcraft occasionally. Haven't figured out how I can play it yet but even if I can't, it's fine. 

I didn't know much about Ubuntu or Linux when I first installed it. On the first installation of Ubuntu, my harddisk was partitioned as following:

C Drive - for Windows and programs   (25GB)
D Drive - my personal data (My documents) (20GB)
E Drive - Temporary data storage (25GB)   <- I download stuffs like moves, musics.. and transfer to the external storage later on. 

To experience Ubuntu, I cloned C drive so the system can be back to where it was and formated C drive to install Ubunut (first trial).

My plan is to have a similar structure with Ubuntu. What I'm thinking is 

/Root 20GB
/Home 20GB
/Swap 2GB or 4GB (which one should be?)
/Storage --> the rest (just like E Drive Above) 

I have been reading for a guildline for partitions for few hours. But i thought it would be better to ask with my settings. 

Questions I'd like to ask are:

1. How big root should be? Are all the programs are stored in this partition? Will it run of space? I have been studying all my available hours to study Linux for 4 days but it's not long enough to understand this far yet.

2. What is the better size for Swap partition for 2GB RAM?

3. Is it better to have a separate partition for Temporary downloading? I do this because it's neat and organized and also faster for the computer to locate the data. 

I will really appreciate your advice. 

Cheers,

---

### Post by macogw on 2007-12-18
1.  5-10GB is good for /  (it's not /Root, just / ) ...10GB lets you install more stuff and be lazier about cleaning up apt's cached .debs (.deb is like Setup.exe  ..oh and I've gotten very close to filling mine when it was 7GB when I didn't empty the cache, but never with 10GB.  emptying the cache involves running "sudo apt-get clean" to clear them all or "sudo apt-get auto-clean" to clear the outdated ones).  I think the entire repository fits into about 20-25GB, so it'd be really hard to even get close to filling 20GB.

2.  They used to say 2x the amount of RAM you have.  Really, you're not going to need more than 2GB (and certainly not 6GB) unless you're doing some crazy video editing or rendering or something.  If its a desktop and there'll be no hibernation, you probably don't even need swap.  If it's a laptop and you want to hibernate, though, swap is where the image of your memory goes when it hibernates, so it should be at least 2GB then, maybe *slightly* more just in case you manage to start swapping.  Swap isn't called /Swap because it's not actually mounted, so it has to reference based on /

3.  /tmp (not /Storage) doesn't need to be separate.  Some do it for security--they set it to mount noexec, which means nothing can be executed from there.  /var or /var/log is more common to separate since it could potentially fill up with log files, but that's more of something you do for servers since when a server gets attacked by a botnet, it produces massive amounts of logs.  I really doubt your personal computer will be attacked by a botnet.

And it's /home not /Home  Linux is case-sensitive

---

### Post by Humph on 2007-12-18
I asked pretty much the same question a couple of months ago.

I was advised:

/ (root) 10GB
/home *remainder*
swap 2GB

Being an XP user at the time 10GB for a "system" partition seemed a bit on the small side, so I opted for 20GB. I have used 3.49GB to date, so 10GB would have been just fine.

---

### Post by taekr on 2007-12-18
Thanks for the advice 

10GB is enough??? Wow.. that's small..

There was a misunderstanding. 

/Storage is just a partition to hold data I download from the internet.  The name is something i just made up. I plan to leave a partition (the rest) to store data. I didn't mean that I would have a separate partition for /tmp.

---

### Post by macogw on 2007-12-18
oh ok.  Probably should put that in /mnt/storage then.  That'd be the more um....standard place to put it, I think.  External storage is usually mounted under /media/ and hard disk partitions that aren't part of the main system usually go under /mnt/  (mnt is as in the consonants of the word "mount"...get it?  it's whatever's mounted.  if you haven't learned the word mount yet, it's like when you plug a flash drive into Windows and it sees it and sets it up and goes "ok that's gonna be F:\"  and then unmount is like when you click "safely remove hardware" in bottom right to take out your flash drive)

---

### Post by taekr on 2007-12-18
/root --> 10GB
/swap --> 2GB

then...

will it be mass if I assign the remaining to /home??? 

I download stuff a lot from the internet. I move them around a lot too. 

Will it be wise to have a partition to download and keep stuffs?

---

### Post by Humph on 2007-12-18
> **taekr said:**
> 10GB is enough??? Wow.. that's small..

Yup! Scary, isn't it? :)

---

### Post by macogw on 2007-12-19
> **taekr said:**
> /root --> 10GB
/swap --> 2GB

then...

will it be mass if I assign the remaining to /home??? 

I download stuff a lot from the internet. I move them around a lot too. 

Will it be wise to have a partition to download and keep stuffs?

I usually just put that stuff inside my home drive.  If you want other users on the computer to have access to it too, though, having a separate directory for it is probably good.  Whether you just download stuff to your home drive or give it its own place is totally up to you though

---

### Post by taekr on 2007-12-19
I think my explanation has not been clear. 

/root --> 10GB
/swap --> 2Gb
/Home --> 20GB
and the remaining (80GB - 32GB = 48GB) will be a partition for some other data.   

and Plus I have 300GB external harddisk where I back up data. 


Q: will it be necessary to have 48GB partition for other data??  what do you think?

---

### Post by Sef on 2007-12-19
> /root --> 10GB
/swap --> 2GB

You don't need 2 GB swap.  As Macogw said, you don't need swap if you have 2 GB ram, unless for the reasons that were listed in post #2.

> 10GB is enough??? Wow.. that's small..

10 GB / is big for GNU/LInux.  

> will it be mass if I assign the remaining to /home???


Yes, it will be one partition.

> I download stuff a lot from the internet. I move them around a lot too.

Will it be wise to have a partition to download and keep stuffs?

I just download everything to my desktop.

---

### Post by click4851 on 2007-12-19
I like the seperate /home partition in case I bork something and need to reinstall. Install everything except home and bob's your uncle.

---

### Post by taekr on 2007-12-19
Thank you very much for all the advice!!!!

My plan is 

/root  10GB   (few GB is something I can spare ^^)
/swap 2GB  (laptop)
/home 30GB
a partition (remaining) for Bittorent downloading

---

