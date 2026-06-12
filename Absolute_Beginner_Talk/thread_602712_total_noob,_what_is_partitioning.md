---
title: "total noob, what is partitioning?"
date: 2007-11-04
forum: Absolute Beginner Talk
---

### Post by trogdoor17 on 2007-11-04
In the live CD installer, is the new partitioner slider going to partition the disk for ubuntu or everything else?

---

### Post by Pumalite on 2007-11-04
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)
[http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty_p2?](http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty_p2?)

---

### Post by Fred_E _krugar on 2007-11-04
It is basically splitting the HD in half to make it look like 2 HD and it will use the new side for the Ubuntu install.
 
D4mit Puma, are you stalking me???

---

### Post by candtalan on 2007-11-04
> **trogdoor17 said:**
> In the live CD installer, is the new partitioner slider going to partition the disk for ubuntu or everything else?

I think you are asking  that if the slider indicates say, 40%, then does this mean 40% for Ubuntu, or only 40% for windows?

I have to say I am just not sure. I do not think the explanation displayed is totally clear and I would not be sure. If you choose something very different from the initial offer (near to 50/50 I guess) then if you get it wrong you might get some problems.

One way around this is to *first* change the windows partition size either using the windows own partitioner or a facility like parted magic (live cd). Do not make a new extra  partition, then just tell ubuntu installer to install into the largest free (uncommitted) space available on the drive.

---

### Post by StomUK on 2007-11-04
> **Pumalite said:**
> [http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)
[http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty_p2?](http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty_p2?)

THanks for the links there Pumalite..

I too am still a 'beginner' with Ubuntu (and Linux in general) and have also been interested in whaty I guess is a optimal setup as far as partitioning goes. IF I use the /home setup mentioned in the second link does it mean that programs and so on get installed in my /home section thus keeping them separate from the OS side of things? (Or is it like on my Amiga where some of the library files are held in the OS side of things?).

Basically I guess I need to find out a guide or summat that tells me what all the folders in the filesystem are there for and what they do (eg, where does the system save its settings for program and so on? a general preference folder (ala Env on the amiga) or a Registry (urgh) like windows?)

Thanks for any adice, links of further help :)

---

### Post by Pumalite on 2007-11-04
It's nice to have a separate /home partition because your settings and other handy things are stored there and you can use it (save it) in case of a future 'clean install'.

---

### Post by goslings on 2007-11-04
> **candtalan said:**
> I think you are asking  that if the slider indicates say, 40%, then does this mean 40% for Ubuntu, or only 40% for windows?


Where is this slider everyone keeps mentioning 
I click install and I get 7 steps - nowhere is there a % slider, irrespective of which options I take on each step .
Where is the step by step guide to the install on Ubunto for *7.1*

I thought the partition was an automatic part of the installation with min input from user and no chance to screw up win-xp
regards

---

### Post by trogdoor17 on 2007-11-04
> **candtalan said:**
> I think you are asking  that if the slider indicates say, 40%, then does this mean 40% for Ubuntu, or only 40% for windows?

I have to say I am just not sure. I do not think the explanation displayed is totally clear and I would not be sure. If you choose something very different from the initial offer (near to 50/50 I guess) then if you get it wrong you might get some problems.

One way around this is to *first* change the windows partition size either using the windows own partitioner or a facility like parted magic (live cd). Do not make a new extra  partition, then just tell ubuntu installer to install into the largest free (uncommitted) space available on the drive.

yeah, this right here is the question i am asking.

---

### Post by Pumalite on 2007-11-04
I usually use Gparted Live CD and make the partitions ahead of time (much more control over the process):
10 GB for'/'
2x RAM up to 1 GB for /swap
The rest for /home.
Then you go 'Manual' and you use them in the installation.

---

### Post by StomUK on 2007-11-04
so for a 'ideal' partition setup I would have something like err..

/ (where ubuntu itself istalled right?) (20GB?)
/home (20GB maybe? would this be where programs I add get installed or do they go into the / partition? (if so I would make root 40GB and /home 20GB))
/swap (2GB in my case as I have 1GB memory?)

---

### Post by Pumalite on 2007-11-04
10 GB for '/' is enough. Hardly anybody needs more than 1 GB for /swap.(except laptop for hibernation where /swap=RAM)

---

### Post by candtalan on 2007-11-05
> **goslings said:**
> Where is this slider everyone keeps mentioning 
I click install and I get 7 steps - nowhere is there a % slider, irrespective of which options I take on each step .
Where is the step by step guide to the install on Ubunto for *7.1*

I thought the partition was an automatic part of the installation with min input from user and no chance to screw up win-xp
regards

Install options have several possible situations, it is assisted, and not entirely, completely, automatic. If you present it with a pc with only a blank unformatted drive, you probably will not get many options and probably no slider. If you present it with a single hard drive with windows XP  on one partition which fills the drive, you will probably get a slider - as an early option about how you want to partition. You could also choose to delete xp entirely of course (no slider) etc etc.

The slider should normally I believe be shown using the live CD early in the (graphical) install in a situation where you have chosen to proceed to install into a drive which is recognised as containing windows (XP anyway). I believe Vista is similar but may be troublesome in other ways, not sure, I do not and probably will not, use vista so I cannot comment much.
see the 'Prepare disk space' window in:
[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)

Please be aware that an install process does in fact give a number of chances for things to go wrong, although this is unlikely in situations with a single drive with XP only. As the  hardware and system options get more complex it is best to err towards caution.
Also in all situations it is most wise to have a good backup of data before starting a process which includes changing partitions.

btw the version numbers represent year and month so the latest release is '7.10' for October, 2007
hth

---

### Post by goslings on 2007-11-08
> **candtalan said:**
> .... If you present it with a single hard drive with windows XP  on one partition which fills the drive, you will probably get a slider - as an early option about how you want to partition. 
...snip
hth

Many thanks, I do not get the step 5 "prepare disk space" screen
So is there a link to a proceedure that explains how to partition a disk with xp on it so that the slider screen does appear - this seems most safe way to not screw up xp and have dual boot with Ub7.10
regards

---

### Post by Pumalite on 2007-11-08
The safest way is to use Gparted Live CD. Boot from it and resize your XP partition. Then partition as desired, then install Ubuntu.

---

### Post by goslings on 2007-11-08
thanks
I will try it 
Is there some step by step you can give me
Here is what Gparted displays
[http://ubuntuforums.org/attachment.php?attachmentid=48940&d=1194110482]("http://ubuntuforums.org/attachment.php?attachmentid=48940&d=1194110482")

---

### Post by goslings on 2007-11-09
> **goslings said:**
> thanks
I will try it 
Is there some step by step you can give me
Here is what Gparted displays
[http://ubuntuforums.org/attachment.php?attachmentid=48940&d=1194110482]("http://ubuntuforums.org/attachment.php?attachmentid=48940&d=1194110482")

bump - just because I only have the weekend to play on this 
thanks

---

### Post by Pumalite on 2007-11-09
[http://gparted.sourceforge.net/documentation.php](http://gparted.sourceforge.net/documentation.php)

---

### Post by goslings on 2007-11-09
just started to look using windows to partition using computer management
Disk management shows the attached image
Help says click free unallocated space and select new partition 
am admin account but righ clicking in either box produces no create new partition ??
This is what  I gort  under GParted 
[http://http://ubuntuforums.org/attachment.php?attachmentid=48940&d=1194110482]("http://http://ubuntuforums.org/attachment.php?attachmentid=48940&d=1194110482")
rather confused

---

### Post by goslings on 2007-11-10
bump - just because i have only weekends to work through this
thanks

---

### Post by goslings on 2007-11-11
Trying Gparted
keep getting errors 
run chkdsk /f TWICE 
do not understand
anyone any ideas

---

### Post by teabuntu on 2007-11-11
Hi,
Does anyone know if there is a maximum limit as to the number of partitions you can have?

Thanks.

---

### Post by bulldog on 2007-11-11
> **teabuntu said:**
> Hi,
Does anyone know if there is a maximum limit as to the number of partitions you can have?

Thanks.

Yes,in basic you can have up to four primary partitions.
But by offering one primary and make this extended [rest of the hdd free space] you can create up to 256 logical partitions.

Be ware you can't boot windows from a logical,ubuntu can.
You can have just one extended partition though.

To install ubuntu on a hdd with windows:
primary one windows
primary two windows data [can be logical if you wish]
rest of the hdd extended partition and create here three partitions for ubuntu
10GB for /
1-2GB for swap
remaining space /home

There's more than one way to do this,but you get the idea I hope.

---

### Post by goslings on 2007-11-11
> **goslings said:**
> Trying Gparted
keep getting errors 
run chkdsk /f TWICE 
do not understand
anyone any ideas

Bit the bullet backed all up on D; the extended partition 
reformatted the area, errors disappeared, and would let mr resize to give me 30Gb free space.
taking a while
when this finishes - should I be able to install Ubuntu into the generated free space ?
:guitar:

---

### Post by bulldog on 2007-11-11
Yes it should.:)

---

### Post by goslings on 2007-11-11
I've seen notes about making region for /home /swap ex3 ?
will i need to do this ?
thanks

---

### Post by Tux.Ice on 2007-11-11
i would just set the slider to 50% or do manual partitioning:lolflag:

---

### Post by Pumalite on 2007-11-11
What,... and ignore all the other nice partition suggestions?

---

### Post by bulldog on 2007-11-11
It all depend on your needs.
I prefer to have my data and preferences on a different partition so when I have to reinstall or want to try another distro,I can do so without loosing my data.

---

### Post by goslings on 2007-11-11
i have never seen the slider 
this is how the post starter
does this slider make the /home area so all can be saved and U7.10 kept up-2-date + personal settings etc
thanks

---

### Post by bulldog on 2007-11-11
> **goslings said:**
> i have never seen the slider 
this is how the post starter
does this slider make the /home area so all can be saved and U7.10 kept up-2-date + personal settings etc
thanks

Yes in fact it does,under the root system,when you will reinstall you have to backup your data.
If you make a separate partition for /home you won't

---

### Post by goslings on 2007-11-11
therefore 
after this resize thats 15mis away from finishing.
I need to make another partition for /home, before I install U7.10 ?
is best to make it at the end of this 100Gb region ? as it take 2hrs to resize and open me up a 30G region 
(I suppose I could resixe the 30G I have just made for /home ???
thanks for your help btw

---

### Post by bulldog on 2007-11-11
> **bulldog said:**
> Yes,in basic you can have up to four primary partitions.
But by offering one primary and make this extended [rest of the hdd free space] you can create up to 256 logical partitions.

Be ware you can't boot windows from a logical,ubuntu can.
You can have just one extended partition though.

To install ubuntu on a hdd with windows:
primary one windows
primary two windows data [can be logical if you wish]
rest of the hdd extended partition and create here three partitions for ubuntu
10GB for /
1-2GB for swap
remaining space /home

There's more than one way to do this,but you get the idea I hope.

It's all told before,start reading your own topic,please.

---

### Post by goslings on 2007-11-11
apologies 
yes I just realised
thanks

---

