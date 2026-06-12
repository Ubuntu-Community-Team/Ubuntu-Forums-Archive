---
title: "Need some advice"
date: 2007-03-09
forum: Absolute Beginner Talk
---

### Post by SurR3AL on 2007-03-09
okay. i've got an 80GB hdd on my comp with XP on it. i will be gettin a 320GB internal Hdd on tuesday. wat i thought of doin was, keep the XP install on the 80GB and do a fresh install of ubuntu on the 320 without touchin d XP. will there be any problems with this setup? i dont wanna partion either of the hdd's (except for SWAP of course). any1 got any advice?
Thanks a lot ppl :)

---

### Post by PartisanEntity on 2007-03-09
It is absolutely no problem to keep your xp on the 80GB and install ubuntu on your new hdd.

---

### Post by Paul41 on 2007-03-09
This is the same way I have mine setup and it works well for me.

---

### Post by SurR3AL on 2007-03-09
thanks paul and partisan....one more thing....can i directly install linux on the new hdd or should a run a preliminary somethin on it?

---

### Post by Paul41 on 2007-03-09
> **SurR3AL said:**
> thanks paul and partisan....one more thing....can i directly install linux on the new hdd or should a run a preliminary somethin on it?

Here is how I did it.  When I installed the new drive I first formatted it with Windows.  Then I ran the Ubuntu install and told it to install on hdb (this was my new "blank" drive). I did this based on a tutorial I found.  Unfortunately that was about a year ago so I don't remember which tutorial I used.

---

### Post by jem7v on 2007-03-09
When you run your installer (either the LiveCD or the Alternate disk) it'll ask you what hard drive you want to put Ubuntu on. Just pick the right one, and it should do the rest!

---

### Post by SurR3AL on 2007-03-09
thanks jem7v.
@paul - i heard the windows formatter cannot handle drives which are 20GB+....is that true?

---

### Post by Paul41 on 2007-03-09
> **SurR3AL said:**
> thanks jem7v.
@paul - i heard the windows formatter cannot handle drives which are 20GB+....is that true?

Mine is a 250GB drive and it had not problems.

---

### Post by SurR3AL on 2007-03-09
oh ok cool...thanks will do that  :D

---

### Post by easyease on 2007-03-09
I seriously reccomend making a root partition of say 30 gb to install ubuntu then makin the rest a fat32 partition so you can share files between windows and ubuntu.........

---

### Post by SurR3AL on 2007-03-09
> **easyease said:**
> I seriously reccomend making a root partition of say 30 gb to install ubuntu then makin the rest a fat32 partition so you can share files between windows and ubuntu.........



cant i use ntfs-3g and that other software to make windows read ext2/3?

---

### Post by maniacmusician on 2007-03-09
> **easyease said:**
> I seriously reccomend making a root partition of say 30 gb to install ubuntu then makin the rest a fat32 partition so you can share files between windows and ubuntu.........
Nah, I recommend around a 20GB root partition, a 30 GB /home/[user] partition, and then partition the rest as ext3, and use the ext2 driver for windows ([http://www.fs-driver.org](http://www.fs-driver.org) ) to share that space between Windows and Linux.

@ SurR3AL: you don't really have to do anything. Just plug in your new drive, boot up the installation CD. when it gets to the partitioning part of the installation, just ignore the 80GB drive, and partition your bigger hard drive the way I typed it out in my response to easyease. GRUB will automatically create an entry for Windows XP.

---

### Post by SurR3AL on 2007-03-09
ok so i jus unplug my 80GB, then run the livecd, then let it install n partion or wateva automatiacally? that'll do everythin rite?

---

### Post by maniacmusician on 2007-03-09
No, don't unplug your 80GB drive...just don't do anything to it during the installation. Only partition your 300 GB drive.

---

### Post by Paul41 on 2007-03-09
When you run the install from the liveCD it will let you choose which drives to format.  As maniacmusician said you can tell it to leave the 80GB drive alone.

---

### Post by easyease on 2007-03-09
lol theres so many ways to do things but i always go by the tried and tested easy route.

---

### Post by SurR3AL on 2007-03-09
oh ok :) thanks for all those replies. but somehow, m not very comfortable with the idea of having partitions. will it be a problem if i have jus one drive for xp & one straight 320GB drive for ubuntu?

---

### Post by Paul41 on 2007-03-09
> **SurR3AL said:**
> oh ok :) thanks for all those replies. but somehow, m not very comfortable with the idea of having partitions. will it be a problem if i have jus one drive for xp & one straight 320GB drive for ubuntu?

No it won't be a problem. This is the way I have mine set up.

Edit: I never use Windows anymore so I don't care about being able to access the files between XP and Ubuntu. If this is something you care about the fat32 suggestion or something like that might be a good idea for you.

---

### Post by SurR3AL on 2007-03-09
@paul - ya u mentioned it. but i didnt know whether u used partitions or not :)

nws, every1 thanks for all ur replies....i will do the install on wednesday n report in :D

---

### Post by easyease on 2007-03-09
i still think its wise to have a seperate partition of some kind to stick your much loved music and movies on because if you ever break your install of ubuntu or have to reinstall you will lose everything........at least give yourself a seperate /home partition even if it is just ext3. trust me I learnt that lesson the hard way.

---

### Post by jem7v on 2007-03-09
You need to leave the 80 gig hard drive in there when you install or else it won't set up your system to dual boot, because it won't know there's supposed to be a hard drive with Windows on it! :)  That's WHY it needs to be there.

Having a seperate /home partition is really useful for the following reason:
If you decide to move to a newer version of Ubuntu (i.e., 6.10 to 7.04) but you would rather have the ease and stability of a clean reinstall instead of an upgrade, you need your /home folder to be in its own partition or else it'll get wiped clean.  Partitions aren't as evil or freaky as they sound.  They can be adjusted or removed later anyway with a tool like gparted.

Having a seperate /boot partition at the start of a drive is really useful if you have an old motherboard that won't boot from files more than 8 gigs deep inside a hard drive... but if it's a modern motherboard, this isn't an issue.

---

### Post by SurR3AL on 2007-03-10
omg ur right!! :) thanks for the info mate....i AM gonna do that.....the /home partition anyway. :D i have a hp pavilion that's 3 or 4 years old....i dont think the /boot will be needed....no?
i googled a bit, and found [this]("http://www.psychocats.net/ubuntu/partitioning") site on planning partitions. its aysiu's site i think. anyway, from wat u said, the plan i should stick to is the last image on that site. rite?

one more thing....how much do i need to resize the original drive to make room for the /home partition? this wil be a new unformatted Seagate 320GB drive.....

---

### Post by matheuu on 2007-03-10
Mate, scrap the windows XP.... I started out doing exactly what your doing.... You will eventually be thinking... why am I wasting that space on the other harddrive when I could be using it...and it sucks having to hang in bios when you could be booting straight into ubuntu.... The hardest thing for me was getting rid of the xp crap..... 
Cheers
Mat

---

### Post by SurR3AL on 2007-03-10
oh yeah...i've never TOUCHED ubuntu n i think its AWESOME.....m installin it on wed btw :)
Wish me luck
Cheers!

---

### Post by jem7v on 2007-03-10
I would leave your XP drive as pure XP and not touch the partitions on it, and then just put Ubuntu on your new drive, partitioning it for your root and /home partitions (and Maybe a /boot partition just to be safe - it shouldn't be necessary, but better safe than sorry).

And if you later decide to rid yourself of XP (which I would not do until you're absolutely sure you'll never need to boot into it again), it should be a simple matter of simply reformatting your old hard drive and wiping Windows (and everything else) out entirely.

---

### Post by SurR3AL on 2007-03-10
yep that's EXACTLY how i thought of doing it :D hey but just how do i make /boot partition? and i'm gonna resize my 320gb to make a new partition for /home......will around 20GB enough for the 1st partition? den 2GB for swap (i hav 1gig ram) and like how much ever for /boot and the rest for /home....will that work mate?

also, how do i set my swap size?

edit : i found [this]("http://www.psychocats.net/ubuntu/installing") site for the partitioning so no prob.....i jus wanna know....how big must the /boot parition be? also how big must the root ("/") partition be? thanks mate :)

---

### Post by jem7v on 2007-03-10
Boot doesn't have much stuff in it - i.e., mine has about 30 megs. 250 megs or so should be more than you need and it's always better safe than sorry... with a 320 gig hard drive, it doesn't much matter if you're out a few megs anyway.

Not sure how big the root partition should be.  That's where all your programs and the likes are going to be put... maniacmusician recommended 20 gigs for your root partition, and that's most likely a safe place to start.  I certainly know that I don't have nearly 20 gigs of OS and programs on my computer so you probably won't run out of space if you set aside 20 for root.

---

### Post by SurR3AL on 2007-03-10
ok i thought of 20GB for that too....guess that should be okay..and ya 250MB is like so tiny when u look at a 320gig hdd :) hehe...thanks for all ur help jem7v.....much appreciated :)

---

