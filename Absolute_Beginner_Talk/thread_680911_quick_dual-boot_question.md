---
title: "quick dual-boot question"
date: 2008-01-28
forum: Absolute Beginner Talk
---

### Post by anxi3ty on 2008-01-28
First off Im a complete newb to ubuntu and to linux for that matter, but not a complete newb when it comes to computers or the way they operate. I have an understanding of all of the hardware that makes up a computer and how it all goes together.  I have an understanding  of all windows based operating systems from 5.1 to vista. Also I am no stranger to the dos based command prompt. But enough of that to my question.

At the moment I have windows xp pro (x86) on my primary 120gig sata drive. All of the games that I play for that os are installed under a program files folder that is on a secondary 150 gig sata drive. My question is if I installed ubuntu to the secondary drive with out splitting it with a new partition, will leaving the windows files affect the operation of ubuntu or visa versa?

thanks aheada time:)

---

### Post by oldos2er on 2008-01-28
Ubuntu won't install on an NTFS drive, which I'm assuming is what your 150GB drive is formatted as.

---

### Post by bumanie on 2008-01-28
You would not be able to do that (if I understand you), because linux uses a different file system to windows. Therefore to be able to install ubuntu, you need to have partition/s formated to the ext3 file system - ubuntu/linux won't install on ntfs.

---

### Post by emarkd on 2008-01-28
Why would you not want to break off a new partition or two?  It's usually a pretty painless procedure.

---

### Post by anxi3ty on 2008-01-28
Like I said I am a newb to linux so... What do I have to do to install it properly for the fastest operation and smoothest install? Should I just dedicate the drive to ubuntu and reformat it?  I have the ubuntu 7.10 (x64) iso... Which is the one Im guessing i need for a p4 (3.0 630) rite?

---

### Post by oldos2er on 2008-01-28
Is the P4 a 64-bit processor? If so, you have the right iso.

---

### Post by cgarman on 2008-01-28
The P4 should not be a 64 bit processor.  There might be an alternate install on the disk, or you can just download the Torrent or whatever.   Anyway, during the installl you can make a partition to put Ubuntu on or just do it from windows before the install.  I did this just this weekend.  I have XP pro on an 8 gig drive and some files on a second 8 gig drive.  I just made a new partition in windows and then formatted it during the Ubuntu install.  Don't worry, I also have a 250 gig SATA and a 320 gig SATA on the machine as well.  I do alot of video editing and it is easier to keep the OS on a separate drive than the programs and my archive.  I did have some other issues, but right now everything is running fine with Ubuntu.

---

### Post by anxi3ty on 2008-01-28
Your rite oldos2er and cgarman. The second core is emulated. The p4 is not a "true" 64-bit chip but it does have 64-bit computing supported which may have had me confussed sorry. 

"Intel® Extended Memory 64 Technology&#934; (Intel® EM64T) can improve performance by allowing the system to address more than 4 GB of both virtual and physical memory. Intel EM64T also provides support for 64 bit computing to help handle the applications of tomorrow."

That being said I think you are rite to recomend the x86 version to be the best one to use. Even if the x64 version did work it would prollie be slower. Just like xp pro x64 was much slower on my system compared to the x86 version. Okay im gonna delete the games and move em back to the windows drive then burn the ubuntu 7.10 (x86) version to disk and give it a whirl.

thanks again all

---

### Post by cgarman on 2008-01-28
Yeah, that is what I thought.  I am running a Pentium D 805 2.66 gHz OC'ed to 3.6 or so.  It is still 32 bit/64 bit emulated.  The 64 bit ubuntu will run, but not very well.  That was some of my problems earlier this weekend.  Loaded 7.10 32 bit and all is fine so far.  I just have to get Nvidia glx to run...

---

### Post by anxi3ty on 2008-01-28
I have a xfx nvidia 6800 gs. I hope it all works out, but if it boots Ill be happy lol. Being my first try with linux Im sure Ill have problems, but from what I see the rewards will be worth the trouble. If it all works out the first thing i want to try to install is Compiz Fusion. That looks like it is sooo cool.:)

---

### Post by cgarman on 2008-01-28
I haven't even gotten that far.  I finally got my Nvidia 8400 running this evening.  That was all I had time for.  I will look into compizfusion later this week.  Hope yours goes well.

---

