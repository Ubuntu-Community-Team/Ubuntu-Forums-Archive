---
title: "Partition hangs at 33%?"
date: 2008-02-13
forum: Apple PPC Users
---

### Post by Neppo1345 on 2008-02-13
I'm running a Mac Mini, 120 gb hd, 512 ram, 1.25 ghz processor.

Originally tried booting fedora on the mac, but I've been having trouble getting a good dvd image...

So, decided to go with ubuntu (since I'm currently dual booting it and XP on my laptop).

Needless to say, select use guided partitioning (use the whole HDD), partitioner starts, and then hangs at 33% every time.

Figured it was the original 40gb hdd in the mac, so I swapped it out with a 120 i had laying around and the problem persists...

Any insight would be helpful.

Thanks,

-Tim

---

### Post by VCF on 2008-02-13
I bet it has something to do with the PRAM having remembered your old drive as 33% of 120GB is 40GB.  

At  boot time hold down alt-apple-P-R and wait for three consecutive startup chimes.

---

### Post by Neppo1345 on 2008-02-13
EDIT:

GREAT...just decided to run a cdrom integrity check...and it failed.

Should have done this first, but of course I didn't.

Best course of action? Burn a new iso, or download a new iso?


No dice. Still hangs at 33%.

I bought the thing used and it wouldn't even boot osX correctly. So when it kept hanging up with ubuntu I swapped the drive out. So it's clearly not the drive.

I'm clueless.

---

### Post by VCF on 2008-02-13
> **Neppo1345 said:**
> EDIT:

GREAT...just decided to run a cdrom integrity check...and it failed.
Best course of action? Burn a new iso, or download a new iso?
No dice. Still hangs at 33%.

I bought the thing used and it wouldn't even boot osX correctly. So when it kept hanging up with ubuntu I swapped the drive out. So it's clearly not the drive.


The advice I've gotten from lots of people around here is to burn very slowly from the ISO at 1x or 2x.  You can should check the download against it's MD5 checksum to see if it downloaded correctly.  That would be listed on the page you downloaded from.  I download and burn from Windows and use the winMd5Sum program myself.  You may have a wonky CD drive in it (just like my iMac, had to swap it out and then everything was cool) that may be why osx (DVD?) doesn't load.  

Hopefully you've zapped the PRAM, it seems to work for many people (or it may be like a magical incantation..)

---

### Post by Neppo1345 on 2008-02-13
Well, I redownloaded the alternate iso, and it's still giving me a checksum error. Is there anywhere else that I can download it from?

If the cd cdrive was bad, I would think it wouldn' stop reading at the same point every time. 

Am I right?

---

### Post by VCF on 2008-02-13
> **Neppo1345 said:**
> Well, I redownloaded the alternate iso, and it's still giving me a checksum error. Is there anywhere else that I can download it from?

If the cd cdrive was bad, I would think it wouldn' stop reading at the same point every time. 

Am I right?

Good point on the cd drive,  if you got to the point of loading Unbuntu to starting and running the partitioner the CD must have been reading OK.

Check this page for download mirrors:

[http://www.ubuntu.com/getubuntu/downloadmirrors](http://www.ubuntu.com/getubuntu/downloadmirrors)

I have been using the University of Waterloo (Canada) computer club, which has been normaly good although it is slow today.

---

### Post by Neppo1345 on 2008-02-14
Well, I've downloaded and tried three different copies of gutsy, I even went and downloaded a copy of 6.06 and tried that...they all hang during partitioning.

The hdd is brand new, so it's gotta be something else...

Suggestions?
Bring it to the apple store and see if they can diagnose it?

I know NOTHING of macs.

---

### Post by stream303 on 2008-02-14
If you don't mind dedicating the whole disk to Ubuntu, are you using "use whole disk" when you reach guided partitioning instead of the default of partitioning free-space and see how that goes?

Urban legend:  I haven't verified this, but my friend swears it fixed his problem.  I'm doubtful, but he used the OSX setup disk and partitioned it there with OSX defaults.  THEN he ran the ubuntu installer and used the whole disk for partitioning.  YMMV.

My personal favorite right now is the FEISTY 7.04 "alternate" text-based installer.  If you are interested, you can nab it here:

[http://cdimage.ubuntu.com/ports/releases/feisty/release/](http://cdimage.ubuntu.com/ports/releases/feisty/release/)

You don't have any other disks hanging off that mini externally right?

---

### Post by stream303 on 2008-02-15
I just performed a few new installations and saw that I just had to be patient when the partitioner hangs at 33%.  It's working, it just takes time to create that ext3 partition.

The thought did come to me that instead of just a gas-gauge bar, an old-school set of spinning slashes layered over each other would help us wait ( \ - / ) and detect real lockups.  Man, sometimes I would swear that I could see the red/blue gas gauge moving when it wasn't. :)

Try it again, and walk away, cup of coffee etc..

---

