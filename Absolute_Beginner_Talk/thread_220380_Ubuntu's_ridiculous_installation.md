---
title: "Ubuntu's ridiculous installation"
date: 2006-07-21
forum: Absolute Beginner Talk
---

### Post by Tadpole on 2006-07-21
I've never used Linux before and Ubuntu is making me rip my hair out. I don't mean to sound bitter - I'd just like some help. Last night, I put my LiveCD in, clicked "install" on the desktop, and set the partition. It took so long I decided to leave it on all night.

Guess what I found when I woke up? The spinner was still spinning. *Nothing changed.*

I tried it again, this time making the partition bigger (about 10 GB), and it complained it couldn't partition enough space for the installation. Does ubuntu honestly take more than 10GB? If so, why doesn't it say so, instead of making me guess how big to make the partition?

---

### Post by Drakkor on 2006-07-21
Is this the ship it cd or one you burned ?

---

### Post by Paerez on 2006-07-21
Those are not normal problems. I agree with Drakkor's guess that it is a bad burn.

---

### Post by Tadpole on 2006-07-21
Neither. I purchased it from Amazon.

---

### Post by stricevics on 2006-07-21
I don't know why is it giving so much trouble. When I was upgrading from Windows, I have manually resized NTFS partition and told Ubuntu Installer to use the unpartitioned space for root and swap partitions. And that was it. It took like 5 minutes.

---

### Post by ewl1217 on 2006-07-21
Try booting your disc with the option to check for errors. You probably got a bad download and/or burn. If there are errors, try checking the MD5 sum of the disc image (.iso). If it's good, then try burning again, but if not, you'll have to download it again.

**EDIT:** I missed the post that you bought the CD. I've heard about troubles using the Live CD to install. Maybe you could try using the alternate install CD, if possible.

---

### Post by echo $USER on 2006-07-21
Just a case of corrupt media.

---

### Post by Tadpole on 2006-07-21
How can the CD be corrupted if the live version works? I played around with ubuntu running off the DVD just fine. It's just that the installation doesn't work.

---

### Post by PingunZ on 2006-07-21
1 ) its ridiculous to buy a free software cd wich can be sent to you for free
2 ) Its ridiculous to start a topic with such a name

Now I've said that, welcome to this forum and I'm sure you'll be able to install ubuntu soon
- try downloading a .iso file and [burn it to a cd at a slow speed]("https://help.ubuntu.com/community/BurningIsoHowto")
- are you sure there's enough space on you hdd, is a linux partition ready ( you can use gParted on the liveCD, Partition magic on windows, ... )

If that doesn't work post again ;)

Grtz PingunZ

---

### Post by tribaal on 2006-07-21
Yeah, I get your point... But actually the liveCD doesn't use the partitionning tool for example, so maybe only the installation parts are corrupted. 

I second my fellow forum members: try to select the "check disk for defects" option on the liveCD boot screen.

Cheers

- trib'

---

### Post by Tadpole on 2006-07-21
> **PingunZ said:**
> 1 ) its ridiculous to buy a free software cd wich can be sent to you for free
Sorry, but ShipIt sucks. I asked for a LiveCD last year and still haven't received it.

Oh, and I can't burn it myself because I don't know how.

---

### Post by Brunellus on 2006-07-21
you know, there are probably a number of people here on the forums who could act as a "secondary ShipIt."  I've been pretty good about getting ubuntu discs to anyone who's wanted one. 

Possible install issues:  1) bad burn, as everyone else has mentioned. 

also, nobody seems to have suggested 2) You are probably attempting to run the Ubuntu Desktop CD on a computer with less than 256MB of RAM.  Either try the Alternate CD, or go with Xubuntu Desktop.

Third point:  please note the helpful and friendly responses that you're getting.  This is much more than you really have a right to expect, given the way you've phrased your initial post.  This community is more than happy to help, as you can see.  But we'd also like to be treated more like human beings.  A thread title like "Ubuntu installer stalls" or "Ubuntu installer won't finish"  is likely to be looked on more kindly than "Ubuntu's ridiculous installation."  

Vehemence does not overcome ignorance.

---

### Post by byen on 2006-07-21
Tadpole,
First of all... I would like to Welcome you to the Ubuntu forums. I would also second the idea that you should "Check the CD for Defects" to see if the CD is infact corrupted. Lets us know what this test shows you and we can start from there. It would also help us if you can give us your computer configuration to see if there is anything there that might be effecting the install process.
On a side note: I know how hard it is to get stuff working when nothing seems to work. I also understand how infuriating this process can get. But please understand that everyone is here to help. Please be patient and let us help you better.

I hope we can find a solution to your problem. Goodluck.
byen

---

### Post by reacocard on 2006-07-21
> Oh, and I can't burn it myself because I don't know how.

download the .iso for the cd: [http://mirror.cs.umn.edu/ubuntu-releases/6.06/](http://mirror.cs.umn.edu/ubuntu-releases/6.06/)
burn it using deepburner free: [http://deepburner.com/download/DeepBurner1.exe](http://deepburner.com/download/DeepBurner1.exe)
that's it!

---

### Post by skale on 2006-07-21
How much memory do you have?

---

### Post by Tadpole on 2006-07-21
I have 256MB RAM and I think 1.6 Ghz processor. I'm checking for errors right now...seems to be taking a long while.

---

### Post by Tadpole on 2006-07-21
The error checking is completed. It states: "0 checksums failed."

There are no errors, and I have enough RAM. Yet the installation doesn't work.

:(

---

### Post by aysiu on 2006-07-21
How much RAM do you have?

**Edit**: Never mind. 256 MB should be okay. It won't be great, but it should be okay.

---

### Post by Tadpole on 2006-07-21
> **aysiu said:**
> How much RAM do you have?

**Edit**: Never mind. 256 MB should be okay. It won't be great, but it should be okay.
Well until I get it to work it won't even be okay :( 

Thanks for your help though, everyone. aysiu's sig is kind of ironic considering the topic. Personally I've never had problems with installing Windows, but I can't get my $10 Ubuntu disc to install at all. ](*,)  Oh well...

---

### Post by Metacarpal on 2006-07-21
Hi Tadpole,

I'm sorry to hear you're having troubles with your install.  Your hard drive is more than large enough.  And if the checksums were all okay, the install CD might well be fine - possibly a problem with your hard drive itself?

Was your computer previously running an operating system before you attempted the Ubuntu install?  If so, were you experiencing any errors?

---

### Post by Derek Djons on 2006-07-21
Also I had the same problem. A while ago I ended up downloading the (installable) Live-CD instead of the Text-mode version. So I found it weird the CD took quite a while and finally booted me the desktop.

But I saw the install icon on the left and was relieved. Since I could still install it permanently on my machine. But I was wrong. I started the utility and after clicking one or two options the app stoped responding.

From reading this thread I think there could be a bug which is being triggered by some kind of hardware or what ever.
I tried to to perform the installation on my portable. It's an Intel Pentium 1.5GHz mobile, 512MB DDR SDram, 40GB hard drive and CD/DVD-combo.

Eventually I ended up downloading the text-mode installation CD's.

---

### Post by Tadpole on 2006-07-21
Metacarpal, my computer has both XP Professional and XP Home, and both are running fine.

---

### Post by aysiu on 2006-07-21
> **Tadpole said:**
> Well until I get it to work it won't even be okay :( 

Thanks for your help though, everyone. aysiu's sig is kind of ironic considering the topic. Personally I've never had problems with installing Windows, but I can't get my $10 Ubuntu disc to install at all. ](*,)  Oh well...
Well, I don't think your experience is very typical. Usually difficult with installing from the live CD (especially hanging up) stems from one or more of the following:

1. Badly downloaded ISO
2. Badly burned CD (it happens, even with official disks, unfortunately)
3. Hardware failure (something wrong with your CD-ROM drive or the hard drive you're installing to)
4. Hardware shortcomings (for example, if you had 128 MB of RAM or less)

---

### Post by steve.horsley on 2006-07-21
You say you set up the partition. It may be that now the disk has been partitioned by the installer there is no free disk space to make another partition. You may need to use custom partitioning to re-use the partition the first attempt made.

Just a thought. But not much help if the installer keeps freezing. Perhaps the text-mode installer would work better.

---

### Post by Drakkor on 2006-07-21
Was just thinking of that,Steve, you must have non-partitioned "free space" to install Ubuntu,the installer will ask you to use the largest continuous free space available,and then will partition that to ext3,and then install Ubuntu. Hope this helps. I used Partition Magic in Windows to make free space. ;)

---

### Post by Tadpole on 2006-07-21
> **steve.horsley said:**
> You say you set up the partition. It may be that now the disk has been partitioned by the installer there is no free disk space to make another partition. You may need to use custom partitioning to re-use the partition the first attempt made.

Just a thought. But not much help if the installer keeps freezing. Perhaps the text-mode installer would work better.
Nope, not possible. The second time around, when the installer complained that 10GB wasn't enough space, it was on a different computer than the first try (both computers have 256MB RAM, BTW).

---

### Post by Uncle Spellbinder on 2006-07-21
I know computers are different, people are different, hardware and partitions are different. Having said that, my experience a couple weeks ago with installing Ubuntu Dapper Drake LTS 6.06 was so smooth, I'm still thinking about it. 

I have a 160 GB hard drive. I partitioned, in advance, Windows (C) to 25 GB, a seperate empty FAT partition (for music, files and such) to 110 GB. this left 25 GB of unallocated (free) space. I put in the Live CD, rebooted. Once the Live CD loaded, I clicked the install icon. I was guided quickly through the process where the unallocated (free) space was used to create the necessarry partitions automatcally. CD ejected, rebooted, Done. 

The Ubuntu install itself took 17 minutes. The entire process, from partitioning my hard drive to Dapper boot up took around 35 minutes.

---

### Post by Tadpole on 2006-07-21
> **Uncle Spellbinder said:**
> I know computers are different, people are different, hardware and partitions are different. Having said that, my experience a couple weeks ago with installing Ubuntu Dapper Drake LTS 6.06 was so smooth, I'm still thinking about it. 

I have a 160 GB hard drive. I partitioned, in advance, Windows (C) to 25 GB, a seperate empty FAT partition (for music, files and such) to 110 GB. this left 25 GB of unallocated (free) space. I put in the Live CD, rebooted. Once the Live CD loaded, I clicked the install icon. I was guided quickly through the process where the unallocated (free) space was used to create the necessarry partitions automatcally. CD ejected, rebooted, Done. 

The Ubuntu install itself took 17 minutes. The entire process, from partitioning my hard drive to Dapper boot up took around 35 minutes.
Not to be confrontational, but I didn't even know it was *possible* to store music files somewhere on my harddrive without an operating system. So I'm not surprised that someone of your skill level can get ubuntu running in the time it takes to listen to Beetoven's 3rd Symphony. I just would like this to work without downloading separate tools like "Partition Magic" or using a command line.

Thanks again anyway, everyone.

---

### Post by Uncle Spellbinder on 2006-07-21
> **Tadpole said:**
> Not to be confrontational, but I didn't even know it was *possible* to store music files somewhere on my harddrive without an operating system. So I'm not surprised that someone of your skill level can get ubuntu running in the time it takes to listen to Beetoven's 3rd Symphony. I just would like this to work without downloading separate tools like "Partition Magic" or using a command line.

Thanks again anyway, everyone.

I'm an Ubuntu beginner. I'm dual-booting. As I said, I partitioned Windows (C) to 25 GB. It's still there, hence my seperate partition for music and such. I used no seperate tools or command line, just went to disc management in Windows and did it there.

---

### Post by SkyNet2029 on 2006-07-21
Since the other OS's work fine on your hard drive, you might want to double-check that it's not 'size-limited' on the hard drive itself. That's about the only thing that would cause the installer to cry for more disk-space. And if it just stopped midway through, like you said in your original post, maybe a memory check is in order, just to make sure you've got all 256Mb available.

---

### Post by Drakkor on 2006-07-21
Sorry,but I think you have been confrontational through this whole thread, beginning with the title of your post,maybe you're  a person that Ubuntu is not really for you. Maybe try another distro.

---

### Post by vayu on 2006-07-21
> **Drakkor said:**
> Sorry,but I think you have been confrontational through this whole thread, beginning with the title of your post,maybe you're  a person that Ubuntu is not really for you. Maybe try another distro.

That's funny, reading this thread I've thought many of replies were offensive.  There have been several posts lacking Ubuntu spirit. The title of the thread is certainly missing some patience, but when you're trying to get something to work that isn't, people can be understandably frustrated.

Tadpole, I've had problems with the partitioner on the live CD and I've used many different partitioners and somewhat know what they're asking.

On one of my computers I could not get the partitioner to work at all.  What I ended up doing was using the live CD from GParted (another partitioner).  That was able to partition and format the drive.  Then after that I was able to use the installer.

I would recommend that you get ahold of the alternate install CD and try that.  I'm going away for a month and am tied up so I can't help you, maybe someone else here can?

(You might also want to search the forums here for ideas on what partitions and what sizes people are using)

Hang in there. Ubuntu does rock.  On some computers you may have troubles, but if you have the time and patience to work them out you'll end up with a nice OS.

---

### Post by Drakkor on 2006-07-21
Although people have been trying to help (Ubuntu Spirit) there is a negative,almost hostile replies by the orginal poster. NO communication,it's like the poster is trying to talk Over everyone. It is quite disconcernng.It's like well I don't understand what's happening,so I'm going to blame Ubuntu, it just doesn't wash.

---

### Post by psycosmyth on 2006-07-21
Hey, it's Ok. I had the same problem. I'm not sure but I had no trouble instaling U on my AMD desktop with 512mb ram. My laptop with 256 and a Celeron was a joke, there was no way I was going to wait 2 days for it to install.  The trick was to get XUbuntu!!! It's a smaller distro and cached pretty well and then after installing, I just added what I wanted, I even kept the Xfce desktop because it's so clean. :cool:

---

### Post by Wadeisabeast on 2006-07-22
I have had a very similair problem trying to install Xubuntu from a Livecd.  It freezes once it gets to the partitioning part.  I am downloading the alternate version now, and it should be done in an hour.  I really hope it works, i've spent about 3 days now working on this computer.

---

### Post by Sable683 on 2006-07-22
I just got done installing Ubuntu on my 900 MHz laptop... It took me three attempts to get it right. For some reason, the Ubuntu partition software on the Live CD would not work. Then, set up partitions and format of drive with Partition Magic. Attempted install again, got up to 73%  and the install halted, unsure if the screen saver caused the halt or not.  Third time, used the Partition Magic, then re-formated the drive with the Ubuntu Live CD, the rest of the install went smooth as silk.  
After reading these posts, there area only two things I can think of that may be causing the faulty install, first: maybe you sized your swap partition too large. I have been told that if your swap is too large, it starts to be detrimental to the system. Or, two: there maybe the wrong mount was selected for your drive. I am a newbie too, just my $0.02.

~Sable

---

### Post by argie on 2006-07-22
> time making the partition bigger (about 10 GB), and it complained it couldn't partition enough space
AFAIK, it should report that there is not enough space on the partition to install if that's the problem, it can't partition enough space may mean there isn't any "Free Space" on it.

Things I think you should check:
1. The partition you made for Ubuntu, is it ext3? Is the mount point / ?
2. Are you clicking the Automatically partition button, anytime during the whole thing?

I'm no expert, and I haven't ever used the Live CD to install, just trying to  help identify the problem.

---

### Post by eyebrowman92 on 2006-07-22
Ok in my opinion there really is no excuse for buying free software. I'd recommend getting a new cd directly from ShipIt.

---

### Post by GuitarHero on 2006-07-22
> **eyebrowman92 said:**
> Ok in my opinion there really is no excuse for buying free software. I'd recommend getting a new cd directly from ShipIt.

That takes forever.

---

### Post by professor_chaos on 2006-07-22
I had the same problem as the thread starter, with the partitioning. If at any point I selected "back" (changed my mind with some particular setting) during the install process prior to partitioning, the partitioner would be completely frozen. It took me like 5 attempts to finally get partitioning. 

And if this experience was my first with linux or ubuntu, I probably would have given up and gone back to windows or whatever I was using. IMHO, the non-graphical installer worked much better, and while the live-install works for most, it needs work.

---

### Post by psycosmyth on 2006-07-22
what the crap is a partition?:rolleyes: 
Not for ..........windows?:evil:

---

### Post by steve.horsley on 2006-07-22
> **Sable683 said:**
> I just got done installing Ubuntu on my 900 MHz laptop... It took me three attempts to get it right. For some reason, the Ubuntu partition software on the Live CD would not work. Then, set up partitions and format of drive with Partition Magic. Attempted install again, got up to 73%  and the install halted, unsure if the screen saver caused the halt or not.  Third time, used the Partition Magic, then re-formated the drive with the Ubuntu Live CD, the rest of the install went smooth as silk. 

For anyone else reading this thread: Don't use Partition Magic to create and format partitions to put Ubuntu on. There are 2 reasons for this:
1) You might forget the make a swap partition too.
2) Partition Magic formatted Linux partitions often don't work.
By all means use PM to shrink the Windows install and make some free space, althoughteh Ubuntu installer can do this. But leave the space free and let the Ubuntu installer make and format its own partitons from the free space.

---

### Post by Vlammetje on 2006-07-22
If you're unsure of what partitions are created and how much space they use, partition manually during install. Just be sure to have neough free speace besides your windowss partition to do so.
Write down beforehand what partitions you want (for example /, /home, /root, /usr or any others)

Also always be sure to have one partition with mount point '/'. This was one of my beginners-errors and would (after hours) have my install CD conclude that there was no 'base system set up' (crappy translation but hope you catch my drift)

Other than that, where exactly does the installer hang? I've had issues with GRUB installing the last time around, which incidentally was ther very last step of the install.

Finally: it's been siad before but I just will repeat it, try and post as much info on your steps and on your configuration, the more info people get, the more likely somebody might spot the problem.

---

### Post by BoyOfDestiny on 2006-07-22
I didn't encounter any trouble with the desktop installer, however, I decided to use gparted for partitioning (under System -> Administration -> Gnome Partition Editor. It is included in the desktop live CD...)

I resized the ntfs partition, created / and /home (reiserfs) and a swap partition (and a fat32 partition for both OS's to read/write.) Then just did the install and made sure / and /home and swap pointed to the proper partitions. 

It was pretty straight forward (although I had to make an extended partition, but I blame dell for putting like 4 partitions...) 
I haven't set up a dual boot like that before (not my machine...) Much easier to just put Ubuntu :mrgreen: 

Anyway hope that helps you... 

P.S.
Also, why do some people think it's wrong to sell and buy free software? It's one of the freedoms you get with it. Stallman did it with emacs back in the day...

---

### Post by mk74 on 2006-07-22
I have no idea about Linux (I use Microsoft O/S for many years) but yesterday I downloaded the desktop edition. I burned it and today I installed it on a PIII 800MHz/256MB/20G HD (no dual boot). In fact it was one of the easiest installations I've ever done. Now I think it's very interesting for begin, I'll keep it and try to learn more in order to pass to the most interesting part for me which is the server one.

---

### Post by robertfranz on 2006-07-22
Speaking from the standpoint of a complete Ubuntu noob, was there enough free space to create the partition in the first place?

Not being used to the linux gui partitioning interface, I found myself trying to set a 30 gig partition on an already partitioned drive....

It took me a moment to realize I had to manually delete the existing partition first.

---

### Post by Tadpole on 2006-07-22
> **Drakkor said:**
> Although people have been trying to help (Ubuntu Spirit) there is a negative,almost hostile replies by the orginal poster. NO communication,it's like the poster is trying to talk Over everyone. It is quite disconcernng.It's like well I don't understand what's happening,so I'm going to blame Ubuntu, it just doesn't wash.
Interesting. I read and responded to every post. I tried every suggestion (even tried the text installer this morning - failed). I said thank you to everyone - *repeatedly*. The fact that it failed on multiple computers with enough RAM and the CD showed no errors led me to believe the problem may be due to ubuntu's partitioner, not a problem on my end.

You may dislike hearing stories about ubuntu performing less than perfectly, but you needn't try to reaffirm ubuntu's efficacy by lobbing demonstrably false personal attacks about how I'm just not listening. It's just self-deception.

---

### Post by Drakkor on 2006-07-22
So.....did you just want to say Ubuntu's ridiculous,and fight with posters,or are you actually running Ubuntu ? It's hard to reason with a person who's already made up his mind obviously. :rolleyes:
[http://tinyurl.com/m72gm](http://tinyurl.com/m72gm)

---

### Post by aysiu on 2006-07-22
Speaking from my own experience and what I've read in numerous threads in these forums, I'm of the opinion that the partitioner during installation on the Ubuntu Dapper Desktop CD is buggy. I would not recommend using it. It can work, but it can also be... not functional.

For the best results, I use DiskDrake on PCLinuxOS to do partitioning and the Ubuntu Dapper Alternate CD to actually install Ubuntu.

Just my two cents.

---

### Post by Bartender on 2006-07-22
Tadpole -
It sounds like you've got a few PC's laying around.  Can you get your hands on a spare HDD?  Doesn't matter whether there's data on it or not, as long as the data isn't valuable.  How about trying a simple, non-dual boot install?  
Pull your Windows HDD out, plug in the test HDD, and let's see what happens if you let Ubuntu wipe and set up the whole drive.

That's what I did with my test PC (sig) as preparation for installing Dapper a few weeks ago.  I removed the precious dual boot W2K/Breezy HDD and plugged in a crusty old 8 gb Western and it worked fine.  

BTW, the sig PC has worked fine with Ship-it CD's as well as hand-made CD's.  My modern home-brew PC has refused to run Dapper or Breezy; Ship-it or home-made CD's.  I've tried various tweaks in BIOS and a coupla different pieces of hardware, such as the CD burner.  No go.  So does that mean Ubuntu sucks?  Of course not.  It's not going to work on every single PC on the planet.  I've poked around on the forums and found at least one other person with the same mb (ASUS P5GDC-V Deluxe) who had no problems so if I were smarter and more persistent maybe it'd be working.

You claim that you've tried the same CD in a few different PCs and none of them worked.  Doesn't that indicate something's wrong with the CD?  Even if Ubuntu says "no errors found"?  Lots of folks had problems when they used cheap media.  Someone cranking out Ubuntu CD's and selling them probly isn't cutting into his profit by using Verbatims.

---

### Post by Daremo on 2006-07-22
Tadpole,
mabee try another distro. I've had very good success over the last few years with Mandriva's disk partioner. It's graphical and easy to use.

---

### Post by Tadpole on 2006-07-22
If anyone could recommend a good third-party Windows partitioner, please let me know. Someone in this thread said I shouldn't use Partition Magic, so I'm looking for anything that will work.

---

### Post by aysiu on 2006-07-23
[DiskDrake](http://www.ubuntuforums.org/showthread.php?t=114142) is a good free partitioner.

---

### Post by steve.horsley on 2006-07-23
> **Tadpole said:**
> If anyone could recommend a good third-party Windows partitioner, please let me know. Someone in this thread said I shouldn't use Partition Magic, so I'm looking for anything that will work.

That was me. You should be fine using PM to shrink the windows partition. Just dont use it to create Linux partitions. But the Ubuntu installer has an option to use the free disk space so using PM to shring windows and leave a gap is all that you need to do. It's just that several people have had problems trying to use Linux on a partition that was created and formatted with PM.

---

### Post by sguart on 2006-07-23
tadpole,

i think for ppl to help you further. you need to be more forth coming about information.

you need to list out your hardware setup, your partition layout, your installation steps, and the exact error that you are getting.

it's hard for ppl to second guess your progress and know what's the current state of affair.

i have read through the entire thread and i still don't know what your exact setup is and what your partition layout is.

you should organize the steps that you tried and list them out in an easily readable table or something and people can see your progress.

if you have a test pc on the side, the u can run the steps while you document the details on another machine that u r using to post to the forum.

this is just a suggestion.

good luck,

sg

---

