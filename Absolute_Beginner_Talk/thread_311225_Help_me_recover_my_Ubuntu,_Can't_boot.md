---
title: "Help me recover my Ubuntu, Can't boot"
date: 2006-12-02
forum: Absolute Beginner Talk
---

### Post by habtish on 2006-12-02
I have been using Ubuntu edgy on an 80GB HD, Ubuntu living in a 10GB partition and the rest an NTFS partiotion. I wanted to install another instance of Ubuntu to test somethings without worrying about destorying my current install so I decided to resize my 65GB partition and ready it for a fresh install.

I booted form a Gparted LiveCD and resized 5GB from the 65GB NTFS. This partition was then showing up as "unallocated", and I thought it would be best to name it something so I know where to tell Edgy to install. I used Device>label disk, thinking this was the feature... it showed a warning window which I stupidily never read and told it to create.

Well, this formated my whole HD including the 10GB partiotion where I have my current ubuntu install. I can not boot into Ubuntu as the process stops at (unknows root file system). 

I went back to the Gparted Livecd and tried using Fdisk to recover my partitions... but I don't remeber the exact cylinders and block sizes where one partition stopped (hbd1) and where the other started (hdb2 - ubuntu installed). 

How can I recover my old partition table? Please help...

---

### Post by mthakur2006 on 2006-12-02
I had the same problem ... seems like a bug...
I could not recover my ubuntu partition, though.
Can you boot into windows?
If not, get the windows rescue disk and delete the ubuntu partition....seems wierd saying that but I couldn't see any way out so I had to do that :)
My apologies....can't be of anymore help :(

---

### Post by habtish on 2006-12-02
I Don't think it's a bug.. I just did not read the warning and messed my partition tables. There are some apps out there that can recover the tables but they all come at at a cost... I can delete my ubuntu partition and re-install.. am just fightining so hard because I will be losing a lot.. and I mean a lot of stuff...

It's sad that this thread has been out for more than half a day and noone has even bothered to offer some ideas.... many thanks mthakur2006

---

### Post by Sef on 2006-12-02
> How can I recover my old partition table? Please help...

Get [TestDisk]("http://www.cgsecurity.org/wiki/TestDisk").  The cost is $0.00.   


> It's sad that this thread has been out for more than half a day and noone has even bothered to offer some ideas.... many thanks mthakur2006

We are all volunteers here, so at times your question may not get an answer for a while.  If you don't have patience, then here is the fastest [Ubuntu support]("http://www.ubuntu.com/support/paid") available.

---

### Post by moshuptrail on 2006-12-02
I suspect the reason you are not getting much help is that there is not much help anyone can give you.  If it truly "formatted" your partitions, it probably destroyed any hope of recovering the data - even if you could re-create the original partitions.

---

### Post by Sef on 2006-12-02
> I suspect the reason you are not getting much help is that there is not much help anyone can give you. If it truly "formatted" your partitions, it probably destroyed any hope of recovering the data - even if you could re-create the original partitions.


Not true.  Read my first post (#4.)

---

### Post by habtish on 2006-12-03
> **Sef said:**
> Get [TestDisk]("http://www.cgsecurity.org/wiki/TestDisk").  The cost is $0.00.   

We are all volunteers here, so at times your question may not get an answer for a while.  If you don't have patience, then here is the fastest [Ubuntu support]("http://www.ubuntu.com/support/paid") available.


Thanks for the headsup on TestDisk. It was able to recover my partition tables. I do apologize if I came off as accusing the community here. I do understand everyone here is a volunteer and have gotten countless advices from people here. I was just frustrated at aspect of losing all of the stuff I had under the ubuntu partition and also because I know how fast this forum moves and if it is not answered within 12 hours, then it moves to the 4th page and never gets answered... My apologies again

Sef, would you advise against resizing an NTFS partition?? Someone was telling me it was not a good idea

---

### Post by rsambuca on 2006-12-03
I have resized my NTFS partition a few times now, and have never had a problem using the GParted live CD.  I would strongly recommend defragmenting the NTFS partition a few times before resizing though.

---

### Post by AlanRogers on 2006-12-27
I've read this thread with interest. I've destroyed my Windows machine by trying to install a dual-boot Ubuntu install from the 6.06 LTS DVD included in the Official Ubuntu Book. The machine has two 80GB hard drives, both of which were throughly defraged before the install was attempted.

I tried to create a spare partition on each, one for root and the other for home, with a swap partition. After checking and rechecking the amendments to be made before commiting, it returned an error of 'Unable to create Linux Swap partition' after which ALL partitions are unrecognisable, unreadable and unbootable.

Is TestDisc likely to be able to solve my problem or is there something else I should try in the interim. The important data is on the 2nd drive, so I'm tempted to reinstall Windows on the 1st drive and WinUnDelete all that data, but that'll be a major PITA. Any clue would be very much appreciated.

Oh, and before anyone says/asks,[LIST]
[*]Yes, I should have a backup
[*]No, I don't have a backup
[*]Yes, I did read the instructions
[*]Yes, I am a bit of a twit
[/LIST] :oops:

---

