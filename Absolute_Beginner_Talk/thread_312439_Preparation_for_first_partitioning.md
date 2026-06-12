---
title: "Preparation for first partitioning"
date: 2006-12-04
forum: Absolute Beginner Talk
---

### Post by 2CV67 on 2006-12-04
I am currently FAILING TO INSTALL 6.10 Edgy from Desktop CD to dual-boot with XP.
The CD checks OK & ubuntu works (somewhat...) from the CD.

I get to installation screen 5 of 6 & am offered an autopartition of 71% = 77.8Go which sounds OK (to somebody who knows nothing about partitioning, even after spending days reading forums).
When I press "Forward" then the disk-activity light is on briefly, then stops completely.
Screen 5 hangs with the timer turning.
I tried 3 times, letting it run for 30min but no good.

I wonder if I have not prepared my hard disk correctly?
I ran Auslogics & got down to 0.87% fragmentation, but the blue lines are NOT completely stacked to the left, so there is no big contiguous free space. 
Should the blue lines be hard-stacked left?
Do they NEED to be, before installing ubuntu?
If so - how do I do it?

If not - any ideas where I am going wrong?

Thanks guys!

---

### Post by bodhi.zazen on 2006-12-04
The desktop cd (the one you are using) sometimes fails.

You can try partitioning with [gparted](http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828) or try the alternate CD. The [alternate CD](http://releases.ubuntu.com/edgy/) is a text based installer but will not re-size a partition.


HTH 8)

---

### Post by 2CV67 on 2006-12-04
As a BEGINNER, I don't feel able to handle "a text based installer but will not re-size a partition". I need fool-proof graphics at the moment!

I assume gparted is a tool to use in ubuntu (?) but of course I don't have ubuntu yet - I can't install it...

Help?

---

### Post by az on 2006-12-04
> **2CV67 said:**
> I get to installation screen 5 of 6 & am offered an autopartition of 71% = 77.8Go which sounds OK (to somebody who knows nothing about partitioning, even after spending days reading forums).
When I press "Forward" then the disk-activity light is on briefly, then stops completely.
Screen 5 hangs with the timer turning.
I tried 3 times, letting it run for 30min but no good.


Let it go longer.  Parted (the partitioner backend) can sometimes take a long time to move data around - it is very safe.  I don<t know how significant the drive light is.  Are you sure it doesn't come on at all?

---

### Post by 2CV67 on 2006-12-04
I am absolutely certain that the disk-activity light comes on briefly, then goes off & there is no visible or audible activity at all for 30min until I stop it.

Surely this means nothing is being moved around?

---

### Post by rsambuca on 2006-12-04
I second the recommendation for the gParted live CD.  It is a graphical user interface for guys like you and me!  Very easy to use, and I have never had any problems, but make sure you backup first nonetheless.

After using gParted, go ahead and install .  The ubuntu partitioner is actually gParted as well, but not the latest version.

---

### Post by bodhi.zazen on 2006-12-04
> **2CV67 said:**
> As a BEGINNER, I don't feel able to handle "a text based installer but will not re-size a partition". I need fool-proof graphics at the moment!

I assume gparted is a tool to use in ubuntu (?) but of course I don't have ubuntu yet - I can't install it...

Help?

LOL :lol: 2CV67

The alternate CD is not so bad :)

And along those lines, I would welcome you to Linux, but suggest you be prepared to read a little as has been said so much it is a Cliché **Linux is not windows** and you will likely find a little reading will go a long way....

---

### Post by 2CV67 on 2006-12-04
Believe it or not, I have spent DAYS (I am retired, but not brain-dead yet!) reading about Linux & then ubuntu & especially partitioning, but I still don't get it.

The best explanation I have seen is at:[http://www.psychocats.net/ubuntu/index.php](http://www.psychocats.net/ubuntu/index.php)
but even that leaves me with unanswered questions, particularly:
1. If the automatic partitioner compresses XP & allocates the rest to ubuntu (doesn't it?) - then is XP in a straight-jacket for life?
2. Do I need to pack my hard-disk files to one end before trying to install ubuntu, or not?

I assume from the above replies, that I should pack & that I can do it with gParted even in XP (yes?) so I guess I will try that next...

Thanks for your help, guys, but maybe ubuntu should get some dummies like me on the test panel, to see how we can screw up & how we need SIMPLE instructions!  ;)

---

### Post by rsambuca on 2006-12-04
I would recommend:

1. backup your sensitive data
2. defragment your hard drive from within XP.  Defragment a couple more times (it will say you do not need to defragment, but just click on "defragment" again anyways.
3. try the installation disk again, or try using gParted live CD first to partition your drive.

How big is your hard drive?  It would help us to know in order to recommend what might be best to resize your partitions.

---

### Post by bodhi.zazen on 2006-12-04
> **2CV67 said:**
> Believe it or not, I have spent DAYS (I am retired, but not brain-dead yet!) reading about Linux & then ubuntu & especially partitioning, but I still don't get it.

The best explanation I have seen is at:[http://www.psychocats.net/ubuntu/index.php](http://www.psychocats.net/ubuntu/index.php)
but even that leaves me with unanswered questions, particularly:

General steps:

Defragment  in wondows XP.

Boot to a live CD (gparted live).

Resize your windows partition.

Make a swap partition, size = ram x2

Make an ext3 in the remaining free space. You will use this space at install for Ubuntu (root partition)

See here: [Psychocats install guide](http://www.psychocats.net/ubuntu/installing)

> 1. If the automatic partitioner compresses XP & allocates the rest to ubuntu (doesn't it?) - then is XP in a straight-jacket for life?

Yes. OS can not normally resize their partitions...

> 2. Do I need to pack my hard-disk files to one end before trying to install ubuntu, or not?

All you need to do is defragment.

> I assume from the above replies, that I should pack & that I can do it with gParted even in XP (yes?) so I guess I will try that next...

:p

> Thanks for your help, guys, but maybe ubuntu should get some dummies like me on the test panel, to see how we can screw up & how we need SIMPLE instructions!  ;)

Those are the simple instructions ! If you think that is hard, try installing windows ! Ubuntu is Far easier then Windows !

HTH

---

### Post by 2CV67 on 2006-12-04
Thanks very much.

Of course (I guess I should bever say that!) I have already backed everything up...

I have defragged several times with XP's own defrag utility, but it made a poor job of defragging files & never seems to pack things to one end at all.

I just downloaded Auslogics Disk Defrag which is much quicker & really gets rid of the fragmented files (even as judged by the XP utility) but has not packed them very much.
I will certainly try several more times (90min each) if you think that should do it.

Tell me once & for all - Do I have to pack to one end before installing?

My hard drive is 120Go with 65.2Go free space.

I really appreciate your help!

---

### Post by bodhi.zazen on 2006-12-04
> **2CV67 said:**
> 

Tell me once & for all - Do I have to pack to one end before installing?

No. I do not think it is even possible (or advisable) to do this with ntfs. Defragmentation is sufficient....

---

### Post by az on 2006-12-04
> **2CV67 said:**
> Believe it or not, I have spent DAYS (I am retired, but not brain-dead yet!) reading about Linux & then ubuntu & especially partitioning, but I still don't get it.

The first time I installed linux was on a windows98 box (fat32 filesystem)  Back then, there was no partitioner integrated in the Debian installer -  you had to run FIPS to split a fat32 partition in half and then create a partition for the free space using fdisk.

I must have cued everything up half a dozen times and triple-checked my handwritten notes before I finally cloased my eyes, took a deep breath and partitioned my drive.

> **2CV67 said:**
> 

1. If the automatic partitioner compresses XP & allocates the rest to ubuntu (doesn't it?) - then is XP in a straight-jacket for life?;)

What do you mean?  You get to chose how big to make the partition.  If you only want to give ubuntu a small space, it<s up to you.  If you want to give almost all your hard drive space to Ubuntu, you can too.

But each OS uses its' partition and that's it.

> **2CV67 said:**
> 
2. Do I need to pack my hard-disk files to one end before trying to install ubuntu, or not?

I assume from the above replies, that I should pack & that I can do it with gParted even in XP (yes?) so I guess I will try that next...

Thanks for your help, guys, but maybe ubuntu should get some dummies like me on the test panel, to see how we can screw up & how we need SIMPLE instructions!  ;)

The installer should be very safe.  It should be pretty easy to do.  Usually, there is no need to do anything to your hard drive like defragmenting it, since the partitiner can do all that.  In the case where it cannot, it will simply do nothing and spit out an error.

Of course, nothing can every be guaranteed 100 percent, so of course, you should back up your important data.

---

### Post by rsambuca on 2006-12-04
If you have already defragged a few times, I think that should be fine.

I am sure you will get a gazillion different views on this, but if you are just testing the linux waters for now, I would recommend adding a 20GB partition for ubuntu.  You can use the gParted CD to create one extended partition containing 19GB (formatted in ext3) for the ubuntu root directory (simply called the "/"), and a 1GB linux-swap (formatted as "linux-swap").

This should give you space to play around with ubuntu, and XP will still work fine with 45GB free space.

---

### Post by az on 2006-12-04
> **2CV67 said:**
> 
Surely this means nothing is being moved around?

I once had to turn out the lights and sit close to the drive to see the light coming on for only a split second every minute or so....


But if you are positive, then you are experiencing a bug.  Perhaps find another way to shrink your partition and create some free space.  Then let the installer use that free space to create the needed partitions.

---

### Post by bulldog on 2006-12-04
If you have 65GB free space,don't worry about the files not being at one side.

I should recommend the gparted live cd to do your partitioning manually.
It's just a 25MB download and cost just a cd-r so that's practically nothing.
Boot this cd just as you do with the live cd and follow the steps.

Resize windows but make it not too small you have plenty of free space,so let windows keep about 90GB so you have about 30GB free for Ubuntu.
Watch it,you have to apply before something will be changed.
Now create in the freed space the following partitions,by right clicking the free space and choose new partition,

A 10GB ext3 partition which will be /  (root)
A 1GB swap partition which will be swap
The rest of your space create another ext3 partition which will be /home
If you did all this you have to apply again.

Make notitions from what you created so when you go to install you can look back.

Now exit the gparted live cd and fire up the ubuntu install disk.
If you have the live cd you push the INSTALL button on the desktop,and follow the steps.

When you come to the partitioner,choose manual partition {you already did this}
Now take the note and have a look.
The 10GB you should mount as / just that,it means root partition and check it to be formatted as ext3.
The 1GB you mount as swap and format as swap.
The last partition you mount as /home and format as ext3.

Now you can proceed with the install,which should take half an hour or so.

Hope this makes it a little clearer for you,should say I wrote this out of my memory,and hope I didn't make any big mistakes.

Good luck and welcome to Ubuntu of course :D

Edit:
More than enough help here.

---

### Post by housam on 2006-12-04
Do the defrag once more and look for the unmovable data mark(windows system files)where it is , because you can't partition the HDD before resizing it to just before that mark or you will damage windows.that means if it is located in the middle , your windows partition will be not less than 65G . leaving the rest of the HDD unallocated.
You can use Gparted tool to do the partitioning manualy**before starting the installtion**( it is in the live CD >> system >>.
During the installation process chose the manual partitioning to just put every thing in the right order.
You need to devide the unallocated part to three partitions:
- 15G ext3 /.  for root
- 1G  swap
- The rest G ext3  for home
Good luck

EDIT: I didn't read what bulldog've wrote while I was writing my reply based on my personal solved problem. and it worked out.

---

### Post by 2CV67 on 2006-12-04
Thanks again guys!

I am keeping one eye on these replies & the other on reading the GParted website before I plunge any further.
I am getting a feel for the required partitions & sizes, thanks.

Two details:
1. my file system is FAT32 - I assume that is OK?
2. Housam's comment about damaging windows got all my attention, but not my full understanding... Tell me again about what I have to do relative to the unmovable green line, which is currently about 30% from the left end.

Think an earlier post was out of order - sorry!

---

### Post by bulldog on 2006-12-04
No problem if you leave enough space for windows and about 90GB is enough :D 
FAT32 is no problem it can be read and write by windows and ubuntu.

But the partitions for ubuntu you have to format in ext3 filesystem.
And the swap as swap af course.

---

### Post by 2CV67 on 2006-12-04
I think the phrase "of course" should be blocked out of a forum called "absolute beginner talk". ;)

or could we have an "even more absolute beginner's forum"?

My other eye is still stuck in GParted site & various links from there, so no more action yet...

---

### Post by housam on 2006-12-05
originally posted by 2CV67
> Tell me again about what I have to do relative to the unmovable green line, which is currently about 30% from the left end.

That means there will be no harm if you resized the windows partition to the minimun (65G)but I agree with bulldog 90G is fair enough to leave space for extra windows works.

---

### Post by ipina on 2006-12-05
I've been reading all your fine comments (and sorry for my englich, I'm a spaniard), particularly those of Bulldog which seems to me very interesting. Maybe, I miss, regarding resizing windows partion, some comment about the swap space of windows itself. I mean that before resizing windows it's a good idea to erase the swap memory of windows (pc properties, advanced, performance and advanced again). Of course, once resized, the swap memory of windows should be restituted (through the same procedure as before when erasing it). Cheers.

---

### Post by hyper_ch on 2006-12-05
If you are still having problems with gparted then maybe you want to resize the partition from within windows. For this job I can recommend PartitionMagic... I have several times changed my windows partitions with it (before I went to linux) and you can't really f*** up anything with it (especially since you already have backups).
In PM just resize the windows partition (make it smaller) and leave the rest as it is... no need to adjust anything for the linux partitions yet... the liveCD will take care for it then...

And regarding the alternate installer, it is "text" based but it's not like you have to enter every command by hand or so... I don't remember quite how it was with Win95 but I think the "text" installer is somewhat similar... you do get sort of graphics and stuff and options... have a go for it, it's less complicated than you may think now :)

---

### Post by Bartender on 2006-12-05
Besides, [hermanzone]("http://users.bigpond.net.au/hermanzone/") has a step-by-step guide to the text-based installer.  Get your Linux PC in the same room with another working PC, tune the other PC to his website, and go thru the dual-boot instructions step by step.  I used his "Ubuntu + NTFS" guide to dual boot W2K and Breezy.  Had no idea what I was doing but it worked.

---

### Post by 2CV67 on 2006-12-07
Thanks again for all the help!

Summary of recent progress:

I contacted Auslogics support & they confirmed that Auslogics Disk Defrag only Defrags & _does not consolidate free spaces_, so I stopped there (with blues spread all over).

The GParted forum moderator confirmed that I did not need to stack my files before shrinking my XP partition with GParted (solid second opinion!) so I tried gently squeezing it a bit & XP still worked OK.

I then reduced XP partition from 112Go to 80Go & XP was still OK, so I now know _I did not need to stack my files_.

I have created new primary partitions as follows:
Swap - 518Mo (256Mo RAM)
ext3 - 10Go
FAT32 (share) - 21Go

Next step will be to try installing ubuntu in there (unless somebody shouts to stop me)...

Appreciated all the help so far. :D

---

### Post by rsambuca on 2006-12-07
Looks good to me!  Good luck!

---

### Post by housam on 2006-12-07
Congratulations :D 
Have a nice ubuntu days.

---

### Post by bodhi.zazen on 2006-12-07
The suspense is killing me :p

---

### Post by bulldog on 2006-12-07
Should be done by know................shouldn't it?:D

---

### Post by 2CV67 on 2006-12-07
Yes - that part was actually painless. :-D :-D 

I think we (you) can now call this thread "solved", as the basic partitioning & installation seems OK.

There may be further threads on Canon Printer recognition & especially on USB WiFi recognition, but I will play/browse further before I ask!

Thanks to all!

---

### Post by bulldog on 2006-12-07
Well,we have a new Ubuntu User!!

Welcome to Ubuntu :D

---

### Post by bodhi.zazen on 2006-12-07
A geek is born :p

---

### Post by 2CV67 on 2006-12-08
> **bodhi.zazen said:**
> A geek is born :p

Thanks!
Please send me a large framed edition of that citation...
    ...but it may be a bit premature, as I still panic frequently!

This morning, I woke up ubuntu to see if it was still OK (it was - apart from WiFi & Canon, but that is another story).
Then I booted XP for some serious work ;) but first I couldn't hook to my WiFi (never before in 2 years) so I rebooted, got the XP screen, then a black screen with no action possible.
Rebooted to ubuntu, got ubuntu screen then "checking file system" then stuck at that screen...
Retried several times to get into XP & ubuntu but no good.
That's when I panic!

Finally I remembered the GAG4.7 floppy I made before partitioning & with that I booted XP perfectly (WiFi included).
After that, ubuntu & XP now boot OK, but I don't know what happened.

So, my learning has so far included:
Make a GAG floppy first.
Defrag but don't expect to pack files to one end.
Make partitions with GParted live CD - it will shift your files OK without screwing them up.
Don't loose the GAG floppy!

To be continued, no doubt...

---

### Post by hyper_ch on 2006-12-08
Strange that problem you had with winxp and ubuntu...


> **2CV67 said:**
> Thanks!
Make partitions with GParted live CD - it will shift your files OK without screwing them up.

As to the above: ALWAYS MAKE BACKUPS BEFORE YOU MESS WITH YOUR PARTITIONS... although 1 mio times there might not be a problem at all but if - for some reasons - there are problems then you will be happy to have the bu :)

---

### Post by rsambuca on 2006-12-08
Sorry, but what is GAG?

---

### Post by 2CV67 on 2006-12-08
[http://gag.sourceforge.net/](http://gag.sourceforge.net/)

:)

---

### Post by rsambuca on 2006-12-08
Thanks, definitely looks like a useful insurance disk to have around.

---

### Post by eisblitz on 2006-12-11
Hey! i'm downloading ubuntu 6.10 now and will maybe install it tonight, or try to. This isn't my first time with linux, but the first time in quite a few years (my first time was when i was 17) i'm a few years past that now, but not much; anyway...

i'm sick of windows XP!! i can really say that now. i've had so many problems with it as of maybe 3 weeks ago when for some reason it decided to downgrade its self from XP pro to XP plain.

My network support is gone and even though i defragged my hard disc, deleted all possible spyware, even erased some un-neccesary files, it still runs at half the speed of normal. it also crashes when i try to do the simplest things like opening msn messenger. i will stay with the learning curve. i'm not scared of it anymore, this must be better than windows, i can't go back!!!

i'm on a laptop that's 1.4ghz celeron, 1/4gb memory, 30gb hard disc and WiFi. more later...

---

