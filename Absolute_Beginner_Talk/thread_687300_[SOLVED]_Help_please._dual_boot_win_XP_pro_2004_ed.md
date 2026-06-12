---
title: "[SOLVED] Help please. dual boot win XP pro 2004 ed."
date: 2008-02-04
forum: Absolute Beginner Talk
---

### Post by stalkingwolf on 2008-02-04
I have tried for the last 2 days to set up dual boot with win xp pro 2004 ed and ubuntu fiesty fawn 7.04.

XP installs fine ( am using a 40 gig drive , partitioned into 2 20gig partitions on a toshiba techra 8200),
on its 20 gb partition.

When I try to install 7.04 I get all kinds of weird info from the partitioner ( both gparted on the 7.04
live cd and the gparted live cd) the 20 gb partition will read any where from 5 gb to 18 gb. when i resize
the partition i end up with several partitions i have no idea where they came from, that dont show up
until after install fails.

For instance the last install screen will show a partition of 16 gb as / and 2gb as swap.  proceed to install
and at about 75% it shows low disk space and install stops.  starting gparted shows that install was trying to install to a partition called /target of about 2 gb.  it also shows 2 or 3 "extended partitions"  one equal to the size of the original partition and 1 -2 of 2 -3 hundred mbs.

Does any one know of issues with this edition of xp or is it just that my HDD has been attacked by the Vortex? ( i am close to Sedona afterall).

I have never had this issue before. This laptop was set up as dual boot with 7.04 and the 2001 ed of xp.

---

### Post by jonabyte on 2008-02-04
Do you have a spare hard drive you can use for your Ubuntu installation. I find using a second drive for Linux much easier to install.

Also, you may have to try a different distro, sometimes other versions will work better with your hardware setup.

---

### Post by DiscGo on 2008-02-04
I don't know why but I had trouble with the GUI installation, so I used the text installation to install ubuntu and it worked great.

---

### Post by bumanie on 2008-02-04
With ubuntu, you need to have a free partition that is either unallocated or pre-formatted to ext3. It is mandatory to have at least a / partition and a /swap partition. Many advise to have a separate /home partition as well. 
For your installation (with a 20gb partition), you could probably have a / of 5-6gb a /swap of 1-1.5gb and 13-14gb for /home.
/ is roughly equivalent to c:\ in windows ie, wher the very basic OS is installed
/swap is like virtual ram - if ram is being fully utilised, /swap will be used
/home is where you r documents\music etc. is stored
You can just have a / and a /swap, but if something goes wrong with ubuntu, you will lose all your saved documents\music as they will be stored in the / partition. 
To achieve a setup like above, you should choose manual at the partitioner stage and designate partition sizes.

---

### Post by jan quark on 2008-02-04
some links, have not much to say anymore, posters above me are right IMHO...

alternate CD installation guide
[http://users.bigpond.net.au/hermanzone/p3.htm](http://users.bigpond.net.au/hermanzone/p3.htm)

dual boot xp first linux second
[http://apcmag.com/6101/dualboot_windows_xp_and_ubuntu](http://apcmag.com/6101/dualboot_windows_xp_and_ubuntu)

---

### Post by dstew on 2008-02-04
> gparted shows that install was trying to install to a partition called /target of about 2 gbFor some reason the installer seems to have targeted the 2Gb partition for the system. That is strange. Can you post a screen shot of the partitions that you see in gparted?

---

### Post by stalkingwolf on 2008-02-04
> Do you have a spare hard drive you can use for your Ubuntu installation. I find using a second drive for Linux much easier to install.
So do I, however Its a laptop . no place to put an extra HDD

> Also, you may have to try a different distro, sometimes other versions will work better with your hardware setup.
Yep I thought of that. Im going to try that tonight or tomorrow.

> With ubuntu, you need to have a free partition that is either unallocated or pre-formatted to ext3. It is mandatory to have at least a / partition and a /swap partition. Many advise to have a separate /home partition as well.

Yep.  First partition was formatted for xp2004 and had xp installed. no problem.  Second partition was
formatted ext3. the / and /swap should have been ( and were )set up during install.  the problem is that when install started it created a third partition of 2 gb or less called /target and tried to install
to this partition which ran out of space @ about 75%. I have never seen this happen before.  
As I said before I had this machine set updual boot with ubuntu and xp2001 but through a gross act of cranial flatulation it got wiped.

>  Can you post a screen shot of the partitions that you see in gparted?

At this point no. I fdisked and reformatted the drive last night to try again.  if it happens again i will
try to get a screen shot.

---

### Post by dstew on 2008-02-04
One more thought. The swap partition is a partition of type swap, but it does not have a mount point. In other words, /swap is not correct. That is a mount point. I don't know if you gave your swap partition that mount point, but if you did, the installer might have become confused.

---

### Post by stalkingwolf on 2008-02-05
As I recall it did show as linux swap not /swap.

Here is another question.  When I boot the live CD i get these 2 error messages
[199.944000]  Buffer IO error on drive fd0, logical block 0
[238.044000] Buffer IO error on drive fd0, logical block 0

I just assumed it was trying and not finding a floppy drive.  Is that correct?

---

### Post by bumanie on 2008-02-05
May be you need to try the alternate cd which is a text based installer and often works when the live cd is causing problems.

---

### Post by Forrest Gumpp on 2008-02-05
stalkingwolf,

Just a suggestion from a VERY new Ubuntu user.  Could this installation problem be a problem caused by a seeming immovability of the Windows XP paging file?  I don't have the technical savvy to be more specific, but as one qualified by years to be a student in the University of the Third Age, I understand that in more recent editions of Windows XP the page file has been made to appear relatively immovable:  there is a way of temporarily removing it, resizing the Windows partition, and then replacing it to retain Windows functionality, I am told.

Unless you know how to do that, however, the effect of this seeming immovability is to frustrate the dual boot installation of another OS on the single HDD typically involved in a laptop computer situation.

My geek son tells me that this problem has something to do with the hibernation settings in Windows XP, and that if they are disabled the seemingly immovable paging files should disappear after a restart of Windows XP.  Sadly, he has been so long away from Windows XP that he has forgotten the detailed procedure for effecting this fix.

Should this be the source of the installation problem and, having removed this obstacle, if you were then to proceed with your attempt to install Ubuntu, you may not encounter this installation difficulty with Ubuntu.

I don't offer this as a solution, just as a pointer for the far more technically competent to either deal with or dismiss in further advising you in what I regard as an ABSOLUTELY KEY AREA WITH RESPECT TO THE UPTAKE OF (UBUNTU) LINUX, DUAL BOOTING (with Windows)

I can recall this issue of the relatively recent immovability of the Windows paging file being discussed at the computer club that I and my son regularly attend, and the consensus seemed to be that it was a deliberate ploy by Microsoft to frustrate the installation of other OS, particularly Linux, upon computers sold with Windows pre-installed.  Whether this be true, and if so, it be in violation of US law with respect to deliberate suppression of perceived competition by Microsoft, I cannot say.  But its surely worth a look, I should think.

---

### Post by stalkingwolf on 2008-02-05
VICTORY, VICTORY.

Here are the steps I took to achieve this dual boot.  Hope they help someone else

1. fdisked the drive, and partitioned it into 2 20 GB drives. I left both unformatted ( i used 
ultimate boot disk floppy to do this)

2. Installed xp2004 on first partition letting the install CD format that drive to ntfs.

3 burned a new 7.04 CD

4.  used the partitioner on the live CD to partition second partition into ext3 and swap partitions

5.used manual partition in install and reduced ext3 partition.

6. resized ext3 partition and formatted it /

7. used the created free space and formatted it /Home

from here the install went flawlessly.  I once again have a dual boot with working wireless.
:guitar::guitar::guitar::guitar::guitar::guitar:

Thanks for all the suggestions

---

### Post by bumanie on 2008-02-05
You should mark this thread as solved.

---

### Post by stalkingwolf on 2008-02-06
i would if i could find the button.  must be having more of that cranial flatulation.

---

