---
title: "Extremely Disappointed.."
date: 2007-10-23
forum: Absolute Beginner Talk
---

### Post by Culgan on 2007-10-23
I am so angry right now.. I just installed the new version of Ubunutu and it completely destroyed years and years worth of music I collected because the installation program couldn't format the correct drive.

I have two drives hooked up to this computers, A 250gig Maxtor (master) which formerly had all my music and a LOT of other important stuff, and a 320gig Seagate (slave) which I wanted to use for this. Well, during the installation it even asked me what drive I wanted to format, so of course I chose the Seagate, and even checked to be sure it was correct several times. Well, it installs and guess what! It installed on my Maxtor instead of the drive I TOLD IT TO. 

What now, is there any way to recover my files or is that it?

---

### Post by rudeboyskunk on 2007-10-23
I know how you feel.  I did something similar a month ago (but it was my fault).  10 years worth of writings, GONE.

But to be honest, that's why it's always recommended that you back up your data.  For a long time I would remove hard drives that I did not want affected by a separate install.

There are programs that recover lost data, because it's not truly lost, but I don't know if there are any for Linux.

---

### Post by Dr Small on 2007-10-23
Yes, always prepare for the worst, incase something would go wrong, as it did in your case.
Always backup important data before installing Ubuntu, and if you have two drives, unplug the second one that you are not going to install Ubuntu on, so you do not accidentally install it to the wrong drive, or corrupt that one also.


Dr Small

---

### Post by Pumalite on 2007-10-23
You can recover data from any hard drive these days, but the deed is VERY expensive.

---

### Post by rudeboyskunk on 2007-10-23
If you pay your local police station $10,000, they could get everything off using an electron microscope.

---

### Post by shad0w_walker on 2007-10-23
You might have more luck with a software tool for recovering data. If it just formatted its highly likely that it is recoverable. Most data is easily recovered unless you overwrite it, there maybe some which is overwritten by the installed files but hopefully thats a fairly small amount.

[http://ubuntu-rescue-remix.org/](http://ubuntu-rescue-remix.org/)  <- You may want to look at this as a possible way of recovering the data.

---

### Post by Culgan on 2007-10-23
Every other time I've done this, I always disconnected all the other drives but the one I was going to install it on, except for this time. And I am pretty sure it wasn't my error, I am almost positive selected the correct drive to format. Why would it format the wrong drive?

---

### Post by nynoah on 2007-10-23
Well first thing don't do ANYTHING else with the hard drive.  I would then look for a program that might be able to recover your lost data.  I doubt it was written over, I bet just the location files were written over.

---

### Post by bodhi.zazen on 2007-10-23
I am so sorry for your loss.

You should disconnect the drive asap. You can try this link helps ...

[http://ubuntuforums.org/showthread.php?&t=401093](http://ubuntuforums.org/showthread.php?&t=401093)

Otherwise, as the saying goes, if you did not back it up you must not care about it ...

It is a HARD LESSON to learn , but it is not a matter of *if* something will go wrong, but *when, and how will you recover?*

You can try these links as well :

[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

	[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)
		How to testdisk : [http://www.debian-administration.org/articles/420](http://www.debian-administration.org/articles/420)
	[http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)
	
	gpart: [http://www.linux.com/feature/57748](http://www.linux.com/feature/57748)

[http://mirror.href.com/thestarman/asm/mbr/DataRecovery.htm](http://mirror.href.com/thestarman/asm/mbr/DataRecovery.htm)

---

### Post by louieb on 2007-10-23
[SystemRescueCd]("http://www.sysresccd.org/Main_Page")
[TestDisk - CGSecurity]("http://www.cgsecurity.org/wiki/TestDisk")

[Rescue FAQ - Knoppix Documentation Wiki]("http://www.knoppix.net/wiki/Rescue_FAQ")

TestDisk come on the system rescue CD There are post on this forum saying  it work for them and saying it didn't work for them.

---

### Post by mandrill on 2007-10-23
> **Culgan said:**
> Every other time I've done this, I always disconnected all the other drives but the one I was going to install it on, except for this time. And I am pretty sure it wasn't my error, I am almost positive selected the correct drive to format. Why would it format the wrong drive?

I have had this happen  couple of times, you would think I would remember....my 1st ubuntu install did the same thing, but I think I remember there's like a final little checkpoint....

If it makes you feel any better, (it won't) I just did a new OS install on my windows box, left my slave attached, and it formatted that, too -  wiping out 300gb of music. is was all recoverable, but without the titles, etc....HOWEVER! try TestDisk - it will recover the entire partition *intac*t. How you re-configure from there is of course predicated upon what your configuration needs are. Look here:
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)  good luck!

---

### Post by Culgan on 2007-10-23
Thanks for your replies everyone. I'm going to try some/all these things to get my music back. I have a lot of really rare/hard to find (most importantly awesome) stuff that I don't want to lose.

---

### Post by Jose Catre-Vandis on 2007-10-23
Because I am stupid (I don't mean you too :)), and forever reconfiguring my box, I also occasionally overwrite a partition, in fact I did it just last week, in preparing for Gutsy :).

I use Acronis Director Suite to recover lost partitions, it is oh so easy and does a great job.

It is apparently also to be found on the well known Hirens CD so I have read, not that I would know where to find it!

---

### Post by dynamethod on 2007-10-23
> **Culgan said:**
> I am so angry right now.. I just installed the new version of Ubunutu and it completely destroyed years and years worth of music I collected because the installation program couldn't format the correct drive.

I have two drives hooked up to this computers, A 250gig Maxtor (master) which formerly had all my music and a LOT of other important stuff, and a 320gig Seagate (slave) which I wanted to use for this. Well, during the installation it even asked me what drive I wanted to format, so of course I chose the Seagate, and even checked to be sure it was correct several times. Well, it installs and guess what! It installed on my Maxtor instead of the drive I TOLD IT TO. 

What now, is there any way to recover my files or is that it?


why didnt you back it up before hand?

---

### Post by Culgan on 2007-10-23
A little late for that. Never figured it would be an issue, I figured with all the fuss about Ubuntu that it would all go smoothly and properly. In hindsight of course I should have backed it up and most of all just disconnected it during the install. But now I'm more concerned about getting it back

---

### Post by Pumalite on 2007-10-23
For the future: it's a matter of good practice to always backup before any install of any OS.

---

### Post by Maestro23 on 2007-10-23
> **Pumalite said:**
> For the future: it's a matter of good practice to always backup before any install of any OS.

Very true.  That's just SOP these days. No matter what the "fuss".

Good luck to the OP.

---

### Post by bodhi.zazen on 2007-10-23
> **rudeboyskunk said:**
> If you pay your local police station $10,000, they could get everything off using an electron microscope.

Bah, the Department of Home Security already has a copy ...
[indent]But they are unlikely to know how to find it again ...[/indent]

---

### Post by qbox on 2007-10-23
hmm maybe you didnt format another partition. maybe you just didnt mount drive. When I instalate ubuntu I didnt be able to see another partition.

---

### Post by Pumalite on 2007-10-23
That would be something...I hope that is so; for the OP's peace of mind.

---

### Post by ryanVickers on 2007-10-23
> **Culgan said:**
> I am so angry right now.. I just installed the new version of Ubunutu and it completely destroyed years and years worth of music I collected because the installation program couldn't format the correct drive.

I have two drives hooked up to this computers, A 250gig Maxtor (master) which formerly had all my music and a LOT of other important stuff, and a 320gig Seagate (slave) which I wanted to use for this. Well, during the installation it even asked me what drive I wanted to format, so of course I chose the Seagate, and even checked to be sure it was correct several times. Well, it installs and guess what! It installed on my Maxtor instead of the drive I TOLD IT TO. 

What now, is there any way to recover my files or is that it?
man, I can only imagine what that must be like - but I *have* to ask; "you don't have a backup!?" :(

---

### Post by bonejob on 2007-10-23
I am SO sorry for your loss. I once did a similar thing. But fortunately for me, the loss wasn't as large or as catastrophic. Once - in my old Windows 98 days - a power outage that occurred while doing a file copy TOTALLY corrupted the file system. It was so bad that not only would the damned thing not boot, but putting the drive onto another "good" computer didn't help either; the file system was "not recognized."

A $100 program called "Get Data Back" enabled me to recover almost all the data. It enabled me to literally get the data out - often in fragments - and put it back together block-by-block at times. VERY labor intensive, but it worked. I myself am too new to Linux to know if there is anything similar in the Linux world. 

I once even performed a full format on a drive with data on it that I REALLY didn't want lost and the little-known "unformat" DOS command brought it back. Again, I don't yet know enough Linux to tell you if there is a command-line routine to undo a Linux format. I would be shocked to hear if there wasn't though.

The lesson to be learned is to BACK UP before you do something as drastic as formatting a drive or installing an operating system. If it makes you feel any better, I and just about everyone I know has had to learn that lesson the hard way, too.

---

### Post by Tekno_Cowboy on 2007-10-23
Don't back up what you don't mind losing. Even without formatting problems, a drive crash can cause major data loss. Lucky for me I have a friend who will host my backups on his 2,000 TB server, or I'd be out 3TB of data myself.

---

### Post by ryanVickers on 2007-10-23
2 PiB!  OMG! Lucky! :p

---

### Post by Tekno_Cowboy on 2007-10-23
Ya Betcha! When lightning melted my drives, he even gave me my data back on Samsung 500GB drives that he had extra. I'd sure like to know what that rich guy does with all that space though. No matter how much I ask he refuses to tell me. :confused:

---

### Post by ryanVickers on 2007-10-25
> [ 			 		 		 		 		Ya Betcha! When lightning melted my drives, he even gave me my data back on Samsung 500GB drives that he had extra. I'd sure like to know what that rich guy does with all that space though. No matter how much I ask he refuses to tell me. :confused:


:p

---

### Post by brennydoogles on 2007-10-25
> **Culgan said:**
> I am so angry right now.. I just installed the new version of Ubunutu and it completely destroyed years and years worth of music I collected because the installation program couldn't format the correct drive.

I have two drives hooked up to this computers, A 250gig Maxtor (master) which formerly had all my music and a LOT of other important stuff, and a 320gig Seagate (slave) which I wanted to use for this. Well, during the installation it even asked me what drive I wanted to format, so of course I chose the Seagate, and even checked to be sure it was correct several times. Well, it installs and guess what! It installed on my Maxtor instead of the drive I TOLD IT TO. 

What now, is there any way to recover my files or is that it?

Photorec. If you are in your installation of ubuntu, open a terminal and run ```
sudo aptitude install testdisk
```, and photorec is included with it. I must note however, that some of the data is most likely lost forever if data was written to that disk, and that if at all possible you want to run photorec from an installation on the hard drive that you originally meant to install Ubuntu on (This will allow you to recover the most data possible.) Once you run Photorec, you will have thousands of randomly named files in your home folder. You may use the attached script to organize them by file type, and it may be possible to recover the file names using the ID3 tags, but I'm not sure how.

---

### Post by midknight51 on 2007-10-25
I know how your feeling, I did a similar thing, I was formatting a friend of mine's computer and had all of his drivers on a portable HDD of mine that also had all my games and music and the like. During the setup I accidentally selected my HDD and erased it all. Luckily I did have some recovery software on my M$ computer so was able to get it back but until then I felt like crap and was so angry.
.
.
.
But ive never done it since.

---

### Post by linuxlizard on 2007-10-25
I did that too once- lost all my family photos and everything from 1993 to 2000. It was my fault.

Only took one time to learn my lesson the hard way. I always back everything up now before an install.

---

### Post by baka_toroi on 2007-10-25
How come the default option in the freaking kubuntu installation erases the WHOLE ******* HDD? Jesus ******* christ... I'm so pissed off i can barely type...

Besides, there was a clear message that read Ext3 and swap would be formatted. It didn't say it would screw up the whole FS and delete the NTFS partition...

Oh dear... trying the photorec thingie right now.

---

### Post by bungnati on 2007-10-25
I had the same thing happen. I had a dual boot with XP and it wiped out the partition info because it couldnt format the correct partition. Lost every picture of my daughter from birth to now and tons of music and software. ubuntu would find it on the live cd but once the install script was run they dissapeared and couldnt be mounted weird huh. looked everywhere for a fix couldnt find one.
Couldnt even write to my external drive because it was NTFS (friggin windows).
Ya im pretty pissed too.

---

### Post by ryanVickers on 2007-10-25
wait, are you implying that you let it pick (used the "automatic" mode)?  Because if you did, you can't really blame it - that section of the installer is a piece of s***.  I always use manual, and it's great - you can actually tell it what you want! ;)

If you *did* use manual, however, then that's very strange that it would randomly decide to format the wrong one.

---

