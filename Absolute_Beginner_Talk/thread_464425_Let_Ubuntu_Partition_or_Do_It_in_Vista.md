---
title: "Let Ubuntu Partition or Do It in Vista?"
date: 2007-06-04
forum: Absolute Beginner Talk
---

### Post by plinydogg on 2007-06-04
Hi everyone,

I'm considering setting up a dual-boot system with Vista Home Premium and Ubuntu 7.04 (I currently have only Vista Home Premium installed). My question is: is it better to try to partition the drives from within Vista or is it better to let Ubuntu do it during the install process (there is an option to create a dual boot when you try to install Ubuntu from a livecd, right?). 

I hope you say that it would be better to let Ubuntu do it because for some reason Vista isn't letting me shrink my partition (even though I have 30+ GB free and have defragmented the drive recently, etc.). 

Also, I see a lot of threads with titles like "tried to dual boot, now system is dead" and similar titles. Is dual booting inherently dangerous or something? 

Thanks in advance!

Plinydogg

---

### Post by oilchangeguy on 2007-06-04
use gparted from the ubuntu cd.

---

### Post by jonward0690 on 2007-06-04
I have heard you should only mess with Vista partiton with Vista because it does not like to be resized with anything but its self but I could be totaly wrong.

---

### Post by Nekiruhs on 2007-06-04
No Your right, let Vista do it. Vista throws a TANTRUM when something messes with its partition.

---

### Post by oilchangeguy on 2007-06-04
> **jonward0690 said:**
> I have you should only mess with Vista partiton with Vista because it does not like to be resized with anything but its self but I could be totaly wrong.

and you got this information from where? gparted will work fine. search other threads where users are dual booting vista and ubuntu, and show me where vista can only be resized from within itself.

---

### Post by Nekiruhs on 2007-06-04
> **oilchangeguy said:**
> and you got this information from where? gparted will work fine. search other threads where users are dual booting vista and ubuntu, and show me where vista can only be resized from within itself.
Trust me, I tried, Vista gets really angry and throws some weird errors when you reboot.

---

### Post by oilchangeguy on 2007-06-04
people who post replies based on hearsay, should not bother posting at all.
read this:[http://www.smartcomputing.com/editorial/article.asp?article=articles/archive/r1006/39r06/39r06.asp&guid=](http://www.smartcomputing.com/editorial/article.asp?article=articles/archive/r1006/39r06/39r06.asp&guid=)

---

### Post by plinydogg on 2007-06-04
Thanks for the help everyone. As I mentioned in the initial post, Vista isn't letting me resize the partition so I think I'm going to have to try to use gparted (that's the linux partition manager that automatically takes care of partitions during the install process, right?).

---

### Post by oilchangeguy on 2007-06-04
> **plinydogg said:**
> Thanks for the help everyone. As I mentioned in the initial post, Vista isn't letting me resize the partition so I think I'm going to have to try to use gparted (that's the linux partition manager that automatically takes care of partitions during the install process, right?).

you are correct. good luck!

---

### Post by jonward0690 on 2007-06-04
> **oilchangeguy said:**
> and you got this information from where? gparted will work fine. search other threads where users are dual booting vista and ubuntu, and show me where vista can only be resized from within itself.

Well lets see several places I have seen posts from people saying that they resized Vista partitons in Ubuntu and Vista would refuse to reboot and I have seen this several times.But like I said I could still be wrong

---

### Post by oilchangeguy on 2007-06-04
> **jonward0690 said:**
> Well lets see several places I have seen posts from people saying that they resized Vista partitons in Ubuntu and Vista would refuse to reboot and I have seen this several times.But like I said I could still be wrong

there is the possibility of operator error, and not operating system error. don't you think?

---

### Post by jonward0690 on 2007-06-04
Maybee but that would mean that every person that  has  messed up has had to have been  a retartd and I dought that.But hey there is no point in going back in forth were here to help people not argue.

---

### Post by plinydogg on 2007-06-05
Alright. Since I can't use Vista's partition manager I've been checking the Vista forums for word on alternative methods of shrinking my volume. Several threads list third party programs (e.g., partition magic, acronis disk director, etc.), but (a) these are no less than $50 each; and (b) for any given third party program, there is a host of people who say it works and another host of people who say it doesn't work at all. Several posts even say to use the gparted livecd. 

What's a beginner to do? :(

---

### Post by LaRoza on 2007-06-05
The file system in Vista was changed, so the older tools would not resize Vista's partition properly and Vista would not work.

I heard on the forum this was fixed, but I have not tried it.

I installed Ubuntu to a separate hard disk, and have Vista on the second hard disk, thus avoiding any file system problems.

---

### Post by p_quarles on 2007-06-05
I used Vista's partition manager to prepare space for Ubuntu, and found it quite easy. Obviously, this isn't a Vista forum, but if you want to send me a private message I might be able to help you out.

---

### Post by plinydogg on 2007-06-05
I agree, p_quarles, that resizing the partition in Vista is quite easy....at least in theory. You see, I know the steps I have to go through (I think) but after I click on "shrink volume" and it goes through the step where it calculates the amount of possible shrinkage, it says 0 mb even though I have 30+ GB free. 

Actually, that's what used to happen, since I deleted all my old restore points it says that I can create a partition of 352 MB, but that's obviously not enough to install Ubuntu, which I believe requires at least 3 GB. 

As far as this not being a Vista forum, I see what you're saying but I also think that there are going to be a lot of people who currently run Vista but want to dual boot with Ubuntu and if any of them have the same problem I'm having than it is relevant to the Ubuntu forums (and could be really helpful: anyone who reads this thread knows not to use Ubuntu to repartition their drives). 

LaRoza: you're lucky that you have a second disk. I guess I could always consider installing it on my external USB hard drive but that doesn't seem very practical. 

Thanks for you feedback!

---

### Post by Brightbelt on 2007-06-05
I'm a newbie and I just recently set up this dual-boot.  I was strongly advised to do the partition in Vista ahead of time, and that worked just fine for me, 

Frank B.

---

### Post by plinydogg on 2007-06-05
Thanks Brightbelt but my problem is that I currently can't partition in Vista (see above).

---

### Post by Brightbelt on 2007-06-05
I've used the Vista partition several times. This is a long shot --- but --- It may be that the space you're wanting to use is not totally unallocated. And it needs to be totally unallocated for you to expand volumes with it. 

If there's a drive letter at all attached to the space into which you're wanting to expand, it won't work. For example, you may have a space named 'G: Raw', meaning that it is unformatted space, but it has still been assigned a drive letter and is thus already partitioned. In that case, you'd actually delete this volume, then it would become set as unallocated space. Then you could use it to expand other volumes. 

Like I said, this is a long shot, but one never knows unless they're looking over your shoulder at the computer. 

I hope this helps, Frank B.

---

### Post by plinydogg on 2007-06-05
Thanks Frank, but I don't think that is it in this case (but it could be). My drive has only one partition on it and the drive letter C: is attached to it. I know that in order to create a new partition I need to first shrink the volume, then I take the unallocated space (that results from shrinking the volume) and create a new volume with it. My problem is that I can't get past the shrinking the volume phase. In other words, I'm not even at the point where I would be assigning a drive letter to unformatted space. I hope what I just said makes sense.

---

### Post by Brightbelt on 2007-06-05
Hi Plinydogg,
Also, and this comes directly from MS tech support (if that means anything ;)), IF you do succeed in doing the partition with Vista, I was advised to restart the computer 2 times to get Vista to securely set the new partitions in its inner Bios (or however to word that).

Thanks, Frank B.

---

### Post by p_quarles on 2007-06-05
> **plinydogg said:**
> You see, I know the steps I have to go through (I think) but after I click on "shrink volume" and it goes through the step where it calculates the amount of possible shrinkage, it says 0 mb even though I have 30+ GB free. 

You're probably right that this could be helpful to people here. In any case, that's kinda strange. What are the steps you're going through? I might need to boot up to Vista to remind myself how I did it, but if you could give some details first it would help.

EDIT: I'm guessing you've already tried this, but did you defragment the drive prior to loading the partition manager?

---

### Post by Brightbelt on 2007-06-05
I do understand your situation; that is difficult.  One idea - if you could pick a recent restore point so that it doesn't interrput your system setup too much - might be to do a System Restore in Vista.

That might just tweak the C:\ volume in a way so that it would let you shrink it.  It's an idea, anyways, and System Restores can be undone if needed.  Sometimes, they don't work in the first place, but that still  wouldn't harm your system or change anything.

Frank B.

---

### Post by plinydogg on 2007-06-05
Brightbelt: thanks for the tip. I'll be sure to follow your advice IF I ever get the partitioner to work. 

p_quarles: Here's the steps I take:

(1) I type in diskmgmt.msc in run (alternatively, you can right-click on "computer" and select "manage);
(2) I right-click on the only drive/partition I have (C:/);
(3) I select the "shrink volume" option from the context menu; and
(4) The computer "thinks" for a moment and then tells me that the maximum amount I can shrink the volume is 0 GB (actually, now it says 352 MB, not enough for an Ubuntu install). 

Also, before I took the steps above I defragged my drive (using the build-in defragger) and deleted all my old restore points. 

Thanks for your help everyone!

---

### Post by LaRoza on 2007-06-05
> **plinydogg said:**
>  

LaRoza: you're lucky that you have a second disk. I guess I could always consider installing it on my external USB hard drive but that doesn't seem very practical. 



Actually, I took the harddisk out of my other, Ubuntu only, computer and replaced the Vista drive with it and put the Vista drive in the "Slave" drive spot. It was a SATA drive, so there is no true slave.

I once resized the Vista partition, in Computer Management, to make a partition. Recently, I tried to resize the Vista partition again, shrink, and the option is not there. For some reason, Vista doesn't allow it to resize the partition. I have not figured out what went wrong, but my experience with Vista is that it is Vista's problem.

---

### Post by plinydogg on 2007-06-05
Brightbelt: I don't have any restore points left because I deleted them all in an effort to make more space(!). 

LaRoza: I have no doubt that it is Vista's problem! I guess I'm going to have to wait until I find $50 in the street or something and can afford to buy a copy of Acronis Disk Director. What a bummer :(

---

### Post by Big_Croc7 on 2007-06-05
I haven't used Vista, so take what I say on that basis, but I would suggest the following:

- if your USB hard disk is bigger than your internal hard disk, make a complete copy of your existing Vista partition onto the USB HD as a back up
- if you can't or don't know how to do the above, backup all your user data, files, etc. onto something else, and be happy to reinstall Vista if necessary; you probably won't need to, as dual-booting is not especially risky, but if you haven't done it before anything that involves changing partitions could potentially wipe your data
- use the GParted liveCD to resize your vista partition; this uses a newer version of GParted than is included with Ubuntu ([http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php) or [http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828](http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828)).  I have found this is more successful, especially with NTFS partitions.
- reboot and install Ubuntu

Good luck!

---

### Post by plinydogg on 2007-06-05
Has anyone had any experience using BootIT NG ([http://www.terabyteunlimited.com/bootitng.html)?](http://www.terabyteunlimited.com/bootitng.html)?)

More specifically, has anyone had any experience using it with Vista? 

It is cheaper than Acronis Disk Director.

---

### Post by plinydogg on 2007-06-05
Big_Croc7: thanks for the tip. I might try this if all else fails but I've read too many horror stories on these forums about using the gparted liveCD. I'll definitely keep it in the back of my head though. 

As far as backing up everything goes, I've already backed up my important files, but I haven't created an image of my whole partition. Perhaps it's a good idea to do so. 

Thanks for the help!

---

### Post by Brightbelt on 2007-06-05
You may have already tried this, but I was thinking you might want to actually UN-plug any external hard drives while trying to use Vista's Disk Manager,...Frank B.

---

### Post by plinydogg on 2007-06-05
Frank: I have tried that. I only plug in the external drive when I'm copying stuff to it.

---

### Post by Barrius on 2007-06-05
> **plinydogg said:**
> Big_Croc7: thanks for the tip. I might try this if all else fails but I've read too many horror stories on these forums about using the gparted liveCD. I'll definitely keep it in the back of my head though. 

As far as backing up everything goes, I've already backed up my important files, but I haven't created an image of my whole partition. Perhaps it's a good idea to do so. 

Thanks for the help!

GPartEd runs a whole suite of disk checks before actually changing the partitions.  I've used it dozens of times at home and work (triple booting NT / Vista / Ubuntu).    I routinely delete/resize partitions (Ubuntu testing, install etc).

You said you have your important files backed up.  Using Vista, download CCleaner from CCleaner.com.     Install and run, deleting all temporary internet files, junk etc.     Run it a second time.

Run a ChkDsk on the drive.    Defragment the drive.   Run ChkDsk again.  If any errors are found allow Vista to repair.   Run until NO ERRORS are found.

Boot Ubuntu from CD, selecting start/install.   When the desktop is loaded,   Then used GPartEd to resize the partition.

It worked for me.

---

### Post by plinydogg on 2007-06-05
Barrius: Thanks for the reply! I'll do everything you suggest (I already use CCleaner) except for possibly running Gparted. I've just heard too many horror stories about it. Until someone figures out why it works for some people but not for others I'd like to see if there is another way. 

Also, I tried to run chkdsk yesterday but I got an error saying something I can't remember (it included the words "need" and "elevated" though).

---

### Post by LaRoza on 2007-06-05
You need to run chkdsk as administrator.

Right click cmd.exe, select "run as administrator"

---

### Post by plinydogg on 2007-06-05
LaRoza. Thanks, I don't know why I didn't think of that myself.

---

### Post by Brightbelt on 2007-06-05
I don't know about CCleaner, so it may take care of this. But I would run this command: %prefetch% and delete all the files in that folder. 

Just another cleaning mechanism really. ....Frank B.

---

### Post by plinydogg on 2007-06-05
Will do (I assume they can be safely deleted, right?). Thanks Frank.

---

### Post by louieb on 2007-06-05
Shrinking a partition that contains data is [COLOR=Red]**Dangerous **[/COLOR]to the health  of the data. [COLOR=Black]There is a reason backup is recommended. I have personally screwed up an NTFS partition by using GParted to shrink it. But I'm bullheaded I still use it:evil: There are things you can do to minimize the risk defrag, ccleaner, scandisk ... seen some others i hadn't thought about posted here.

You said you have 30gig free but out of what total? Vista may not want to shrink it because it want a certain percentage free. Don't know about VISTA but XP will slow to a crawl and  Linux will come to a halt when its partition gets filled up. 

The first time I set up a dual boot pc I was paranoid to the point that I got a second hard drive. Since then I have found GParted will  successfully shrink partitions most of the time. But you also have to consider if you left enough room for VISA.             [/COLOR]

---

### Post by plinydogg on 2007-06-05
Thanks for the response louieb. My hard drive is 75 GB total. Thus, Vista and my other files occupy roughly 45 GB. 

I just had an idea: perhaps I can move (not copy) all of my media files (music, movies, etc.) to my external drive, which might allow me to shrink the Vista partition enough. Then, I could just reload the media files I need later. 

This question might be better asked elsewhere but while we're already talking about partition size, what do you recommend? I know I'll need a Vista partition (my original partition), an Ubuntu partition (ext3, right?), as well as a small (2GB?) Ubuntu swap file partition (also ext3). What sizes do you recommend?

---

### Post by Barrius on 2007-06-05
Move media to your backup.   Chkdsk and cleanup - 30Gb should be more than enough.

Using Gparted resize Vista to your new size.

Verify Vista boots ok.
Using GPartEd create a "primary partition (shared) (either FAT32 or NTFS - I prefer NTFS) of 35Gb.
Create an extended partition using the remaining 10GB.
Create logical partition of 1Gb (set as swap).
Create ext3 logical partition of 5Gb (mountpoint of /) for the system.
Create ext3 logical partition of 4 GB (or remainder) for /home (separating allows you to reinstall Ubuntu without wiping out your personal data.  

The shared partition would be available from Vista and Ubuntu.

---

### Post by plinydogg on 2007-06-05
Thanks for detailed instructions Barrius. I'll try when I get home and report back here.

---

### Post by plinydogg on 2007-06-05
Thanks for everyone's help. I did everything suggested but Vista still won't let me shrink my volume more than 352 MB. And while I appreciate the various suggestions about how to partition (using gparted, etc.), I just can't afford to mess up this PC. So I've decided not to even attempt it. I know that's lame but I would just be really mad at myself if something went wrong and I doubt that I would be able to fix it. 

The last straw on the camel's back was the complete lack of agreement about safe ways to resize partitions in Windows Vista (other than by the super-easy way, which apparently won't work for me). 

I'll probably still lurk here from time to time because I really want to give Ubuntu a try but I guess I'll just have to wait until the next time I buy a computer and buy one with a larger hard drive (or two hard drives). Too bad I just bought the one I use now. 

Thanks again everyone :)

---

### Post by plinydogg on 2007-06-05
Wait! Wait! As a last ditch effort I looked at the help files for diskmgmt.msc (where you access Vista's volume shrinking abilities). There were instructions about how you use the utility from a command prompt. I figured, why not try it so I did. And I was able to shrink the partition by 14 GB! Enough for Ubuntu install right (at least a basic install?).

---

### Post by hkahwaji on 2007-06-05
Hi,

I just posted a tutorial where I was able to dual boot Vista Business and Ubuntu 7.04. Here is the link:

[http://ubuntuforums.org/showthread.php?t=465465&highlight=tutorial](http://ubuntuforums.org/showthread.php?t=465465&highlight=tutorial)

I started from scratch. Basically, I used a WinPe Hard Drive Delete Utility to delete my hard driver and then I created 2 partitions using the Vista DVD. 

I then installed Vista and then installed Ubuntu. See the link.

Hope this helps

---

### Post by p_quarles on 2007-06-05
> **plinydogg said:**
> Wait! Wait! As a last ditch effort I looked at the help files for diskmgmt.msc (where you access Vista's volume shrinking abilities). There were instructions about how you use the utility from a command prompt. I figured, why not try it so I did. And I was able to shrink the partition by 14 GB! Enough for Ubuntu install right (at least a basic install?).

That's totally enough for a basic install. Glad you were able to find a solution.

And, for what it's worth, if you have the system backup disks and an external for your files, then you really don't need to worry about screwing up the system. Worst thing that could happen is that you have to reinstall (and then tweak Vista into some approximation of usability all over again). Of course, if bought it used (with Vista?) and didn't get the disks, I'd understand the reluctance to use gparted. 

Good luck, and hope you enjoy Ubuntu.

---

### Post by plinydogg on 2007-06-05
hkahwaji: thanks for the tip I will check it out!

p_quarles: thanks for your help and for the reassurance about not needing to worry about screwing the system (although I'm not sure if I have a recovery disk per se...but I did by this system new so maybe they're around here somewhere?). 

Thanks to everyone for the generous help!

---

### Post by p_quarles on 2007-06-05
If the recovery disk wasn't included, you SHOULD be able to make one. Look around in your start menu: there should be a program that allows you to make a bootable image of your installation, with drivers and stuff included. Mine took two DVDs, though, so if you don't have DVD writing capabilities, you're gonna need a bunch of CDs :-)

If not, maybe call the manufacturer and ask about it?

---

### Post by Big_Croc7 on 2007-06-06
Sorry to add another thing to think about(!), especially when it seems like you're nearly there, but I've thought of something that might be causing problems.  A lot of new computers now come with a 'recovery partition'; this is because the manufacturers are cutting corners too much and don't want the expense of making a recovery CD/DVD.  This is a partition, usually at the start of the disc, and sometimes it is hidden from Windows.  Just something to be aware of - don't worry about it for now, but if you see two existing partitions from Ubuntu but only one from Windows, that's probably what it is.

---

### Post by plinydogg on 2007-06-06
Big_Croc7: I did have a recovery partition when I got the computer but it was wiped out during the Vista upgrade process. 

p_quarles: I'm just going to be as careful as possible with the installation process and if something goes wrong, I'll try to order a recovery CD/DVD.

---

### Post by RealG187 on 2008-05-05
> **LaRoza said:**
> The file system in Vista was changed, so the older tools would not resize Vista's partition properly and Vista would not work.

I heard on the forum this was fixed, but I have not tried it.

I installed Ubuntu to a separate hard disk, and have Vista on the second hard disk, thus avoiding any file system problems.

About this:
[http://ubuntuforums.org/showthread.php?t=782076](http://ubuntuforums.org/showthread.php?t=782076)

Bascially, older versions of Ubuntu dont "know about" vista, right?

---

### Post by housam on 2008-05-06
You can try the manual partitioning :
- First of all you have to back-up your data - just in case.
- Do defrage your HDD 2-3 times and notice the position of the green sector ( windows file system ) . let say at 40% from the left side.
- This means that you cann't resize windows partition to less than that size of the HDD or you'll damage it.
- Use Gparted tool ( on the live CD ) to do the partitioning task.(system >> admin. >> Gparted )
- You can create up to only 4 primary partitions on single HDD.( you already have two of them , one has windows and the other for the recovery )
-I suggest to create one more primary partitions for your data and another one as extended partition which can be devided to many logical partitions (resizing windows partition and creating two new partitions)
- the extended partition can be devided to 2 partitions : one EXT3 ( 10 GB is a good space ) for installing ubuntu as a root partition ( / ). and the other one as a swap ( only 1 GB ).
- During the installation process when it comes to the partitioning choice choose the manual way and assign the EXT3 as a root ( / ) .

---

### Post by RealG187 on 2008-05-06
@housam

Who where you talking to?

---

### Post by p_quarles on 2008-05-06
This thread had been dead for nearly a year until yesterday, so I'm closing it. Anyone who wants to start a similar topic in the *current* Absolute Beginner Talk section is welcome to do so.

---

