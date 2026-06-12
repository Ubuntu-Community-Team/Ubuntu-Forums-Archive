---
title: "I cannot reisntall Windows XP."
date: 2007-07-02
forum: Absolute Beginner Talk
---

### Post by ferunandesu on 2007-07-02
I have Ubuntu 7.04 on both my laptop and desktop and decided to reinstall Windows XP Home on my desktop. When I boot from the installation disc, it says that setup is detecting my hardware configuration, and then it blacks out.

What's wrong here?

---

### Post by reset3x on 2007-07-02
> **ferunandesu said:**
> I have Ubuntu 7.04 on both my laptop and desktop and decided to reinstall Windows XP Home on my desktop. When I boot from the installation disc, it says that setup is detecting my hardware configuration, and then it blacks out.

What's wrong here?

[http://support.microsoft.com/kb/316941](http://support.microsoft.com/kb/316941)

---

### Post by ferunandesu on 2007-07-02
That doesn't help. This problem only showed up after installing ubuntu, so it's an ubuntu related problem. Somehow, ubuntu or the linux kernel i.g. is preventing the Windows XP setup disc from recognizing my hardware, either that, or causing it to crash.

---

### Post by wolfen69 on 2007-07-02
ubuntu will not prevent you from installing anything. when you install xp to a different partition, ubuntu isnt even running. so how could it interfere? at worst you would have to reinstall GRUB after installing XP. 

when will people learn to get a seperate drive for each OS? makes life so simple.

---

### Post by mlentink on 2007-07-02
> **ferunandesu said:**
> That doesn't help. This problem only showed up after installing ubuntu, so it's an ubuntu related problem. Classic 'post hoc ergo propter hoc'. 
> **ferunandesu said:**
>  Somehow, ubuntu or the linux kernel i.g. is preventing the Windows XP setup disc from recognizing my hardware, either that, or causing it to crash. No,  it isn't. When you boot the Windows XP installation disk, Ubuntu isn't even running. So how could its kernel interfere in any way with the Windows installation? If I were in your shoes, I would start looking for hardware trouble.

---

### Post by SoloSalsa on 2007-07-02
Relax, people, Ubuntu did nothing.  However, if you read that Microsoft guide, it did say something which would help: reformat the drive before installation.
Anyway, I always do that before I put Windows on things.  It has a clumsy installation process, in that it makes you reboot before copying the boot sector/boot loader.  And, since it's own loader is not there, it starts installation all over again, indefinitely.  And, other times, it just does nothing when an unfamiliar bootloader is present (like your case).
Usually, fdisk would be enough, but I do not know if you even can use it, because it blacks out with the disk...  So, you need to zero the disk.  Not just delete partitions, or even re-write the disk label; but zero it.  Or, that's what I would do, at least.  If someone knows another solution, that does not take as long as completely erasing the disk, then go with that.
If you need assistance in erasing the disk, just ask (or private message if you want a response before tomorrow).

---

### Post by ferunandesu on 2007-07-02
> **mlentink said:**
> Classic 'post hoc ergo propter hoc'. 


Not when you're familiar with the details of the situation and are capable of using reason to determine what is and is not 'likely'.

---

### Post by splintercellguy on 2007-07-02
Try a different XP disc? Ubuntu most like doesn't have anything to do with the hardware detection issue.

---

### Post by oilchangeguy on 2007-07-02
> **SoloSalsa said:**
> Relax, people, Ubuntu did nothing.  However, if you read that Microsoft guide, it did say something which would help: reformat the drive before installation.
Anyway, I always do that before I put Windows on things.  It has a clumsy installation process, in that it makes you reboot before copying the boot sector/boot loader.  And, since it's own loader is not there, it starts installation all over again, indefinitely.  And, other times, it just does nothing when an unfamiliar bootloader is present (like your case).
Usually, fdisk would be enough, but I do not know if you even can use it, because it blacks out with the disk...  So, you need to zero the disk.  Not just delete partitions, or even re-write the disk label; but zero it.  Or, that's what I would do, at least.  If someone knows another solution, that does not take as long as completely erasing the disk, then go with that.
If you need assistance in erasing the disk, just ask (or private message if you want a response before tomorrow).

now that's a new term i've not heard before. zero the disk. what do you mean?????? if the user actually knows what they are doing. and correctly deletes the partitions already on the drive. then there should be no problems in installing xp.

---

### Post by splintercellguy on 2007-07-02
He means overwrite the entire disk with zeros.

---

### Post by Raineer on 2007-07-02
Boot with the Ubuntu Live CD (the install CD) and run Gparted to format your entire disk, or just download the bootable Gparted image (google that) and format away...which won't involve Ubuntu in any way.

Trust me, we're not being defensive, windows won't install because they have a crappy product...doesn't have anything to do with your current OS

---

### Post by oilchangeguy on 2007-07-02
quote "Trust me, we're not being defensive, windows won't install because they have a crappy product"

and you're baseing this on what? are you sitting with the user? are you sure everything is being done correctly? if not, don't slam any os unless you know the FACTS about what's going on!

---

### Post by STREETURCHINE on 2007-07-02
if you wish to reinstall windows download gparted live disk .

place disk in drive  and reboot ,format the drive to ntfs.
then put in the windows install disk and it should install..

ubuntu has nothing to do with what is happening here,make sure it is an install disk and not a repair disk

---

### Post by Raineer on 2007-07-03
> **oilchangeguy said:**
> quote "Trust me, we're not being defensive, windows won't install because they have a crappy product"

and you're baseing this on what? are you sitting with the user? are you sure everything is being done correctly? if not, don't slam any os unless you know the FACTS about what's going on!
So it's ubuntu's fault windows won't install?

---

### Post by splintercellguy on 2007-07-03
I think we all need to assume a bit of good faith.

---

### Post by SoloSalsa on 2007-07-03
As I said, relax.  No operating system is at fault.  And, as helpful as gparted could be, it is not helpful here.  Even filling the drive with a partition, followed up with deleting said partition, will not fix it.  And, often, setting the disklabel will not help, either.
The fault is with the Windows installer.  Even if a disklabel claims there is no boot sector, Windows will look at the boot sectors.  And, there, it will find junk data.  It looks to determine what previous version of Windows is there, theoretically to optimize or guide installation or something...  Obviously, if it is not a Microsoft-friendly filesystem, it should be ignored.  But sometimes, for whatever reason, it does not handle those junk sectors properly, and blacks out.  I have had worse: it starts installing, and after wasting an hour of my time, then it complains about the disk.
Zeroing a drive would literally mean filling a drive with zeros.  That takes care of one's personal files, the filesystem, all partitions, the boot sector, *and* disklabel, all at once.  After zeroing a disk, the equivalent of washing something with pure bleach (but not really corrosive), if there is *any* problems with it, then the disk itself is bad (as in wear and tear, old age, etcetera).
So, you will lose *everything*, repeat, **everything** on the disk.  If you are okay with this, then ask how.

---

### Post by TravMan63 on 2007-07-03
Something similar happened with me - 
Installed Xubuntu on a primary partition, and created more partitions open for a windows install later.

Windows XP could not see any 'valid' partition, even after repartitioning the disk and reformatting (I did NOT reformat the partition where Xubuntu was).  I fixed GRUB with the UBCD.

I'm wondering with the 'screen going black' - XP prompts for scsi drivers at 1st... are you keying that correctly?

Other than that - if it's a laptop - (or I've seen some Dell 'desktops') that have a custom install disc for windows - that sets the partition table up to include a special partition (for hibernation perhaps)...

Either case - a wipe (reformat) of the disk (gdisk works well) - or a windows boot disk with fdisk.... and I'm sure there's a linux floppy that could perform that function as well would prepare it for a clean install of XP... 

If linux is still booting correctly, I wouldn't think it's a hardware issue.

TM
for a complete 'wipe' use dariks boot n nuke-complete DOD wipe, much slower than gdisk - > [http://www.ultimatebootcd.com/](http://www.ultimatebootcd.com/) <- use with caution!

---

### Post by louieb on 2007-07-03
Heres another one from the folks in Redmon. 
[How to Remove Linux and Install Windows on Your Computer]("http://support.microsoft.com/kb/247804")

---

### Post by SoloSalsa on 2007-07-03
Yeah, those Dell disks most likely zero the boot sectors and disk label.  A MS-DOS fdisk is not enough to fix it, though.
My solution is a proprietary (oh no!), but not commercial, program to put on an MS-DOS (or FreeDOS) disk that wipes out the disk.
The original poster, ferunandesu, has not replied.  Did you work it out?

---

### Post by gcos7 on 2007-07-03
:)If a newbie can join this thread, I'll tell you what my experience has been.  I'm going to assume something, so please correct me if I am wrong.  I will assume you only have 1 partition on your disk and it is dedicated to Linux, plus a swap partition..  You now want to go back to Windows without Linux.  In my case, a "Windows" CD is actually a special disk provided by the PC manufacturer - in my case Gateway.  This is not a "regular" Windows disk.  The installation procedure on it will not install Windows over the top of any existing partitions.  So, if you have a similar type thing, particularly a single partition with Linux and you are just trying to install Windows over the top, try qtparted and remove all Linux  partitions. 

:pThis truely isn't ANY operating system fault, and I'm surprised that instead of trying to help you, some of the people who have replied are all defensive about LInux.  You never said Linux was bad, in fact you say you also have it on a laptop and just want your desktop PC back to Windows.  That should be fine with anyone, no matter how much they might like Linux or Windows or Mac OS - it doesn't matter.  Instead of regressing to a P***ING contest, everyone should really try to just help the user.  If you don't know the problem, don't just assume it's Windows fault.  Or Linux.  Either help the user or don't reply.  This is a beginners forum, and people are looking for answers.

I personally hope that your Linux experience has been good.  I also wish you only the best in going back to Windows.  I'm sorry if my answer was of no help to you.;)

---

### Post by SoloSalsa on 2007-07-03
> **gcos7 said:**
> This truely isn't ANY operating system fault, and I'm surprised that instead of trying to help you, some of the people who have replied are all defensive about LInux.So true.  If this forum had user-reward things, I would give you a point.  And we have not even heard back from ferunandesu.  Personally, I like jokes in the workplace.  But we do not even know if we helped yet.

---

### Post by ferunandesu on 2007-07-07
I haven't tried anything yet. 

The Windows disc that I'm using is a retail version of XP home. 

What process do you recommend for zeroing a drive? Any particular software?

---

### Post by farueulogy on 2007-07-07
> **ferunandesu said:**
> I haven't tried anything yet. 

The Windows disc that I'm using is a retail version of XP home. 

What process do you recommend for zeroing a drive? Any particular software?

I believe gparted was suggested and is your best bet?

It's a live CD which runs a really specific version of Linux dedicated to formatting and editing partitions.

I've only used it once so people should feel free to correct me.

---

### Post by vexorian on 2007-07-07
> This truely isn't ANY operating system fault, and I'm surprised that instead of trying to help you, some of the people who have replied are all defensive about LInux. You never said Linux was bad, in fact you say you also have it on a laptop and just want your desktop PC back to Windows.
Not really, he specifically said it was an ubuntu problem which it isn't, I am not sure  why this forum  and (not the one dedicated to windows) should also give windows install support, which is supposedly MS' job...

---

### Post by pvdg on 2007-07-08
I know ubuntu forum members are remarkably helpful, but aren't we overdoing it  here?  Helping someone reinstall Windows XP? ;)

 I know, it could be worse... ferunandesu could be trying to reinstall Vista! :lol:

---

### Post by SoloSalsa on 2007-07-08
Windows is Windows, and Vista is, if anything, a marginally better version of it.  Though that does not matter.
GParted is wonderfully useful, for partitioning.  Though it will NOT zero the disk.  You need a separate tool for that.
I am sure there are *numerous* ways to do this, though I am only familiar with one: [KillDisk]("http://www.killdisk.com/").  The site has a free CD that can do a bunch of things, most importantly able to zero a disk.  Download the free image, burn it, and use it.  It is very proprietary, and runs DOS, but it does the job.  It will take about an hour to complete, even on a small and speedy disk.  When it completes, you are free to install Windows or whatever operating system you want, without any worry about the hard disk.

---

### Post by bigtoepfer on 2007-07-08
wow thats pretty neat.  the zero thing.  Cuz i had vista installed on here. and it wouldn't go away.  As in XP wouldn't install over it cuz the vista partition "the whole disk" couldnt be removed.  However when i made a copy of the newest ubuntu it was able to remove everything.  So i find it hard to believe that another live disc wouldn't be able to reset the disk for u.  I was going to PM Solo about the program but as i made my way to the end it was mentioned.  And i also wonder why its such a big deal to help someone reinstall xp on his/her system.  This is an ubuntu forum yes.  ubuntu was being used and is currently being used.  and until he/she no longer uses it at all period.  I'd still consider them an ubuntu user.  Now i'm new here and i've not tried to kill anyone for using an OS that was not my preferred OS but i still don't understand the amount of hate garnered when asked how to fix the problem. just my 2 cents

---

### Post by zero244 on 2007-07-08
You could try rewriting the MBR.......a Windows 98 boot disk will work or use the XP CD.
It might be Grub or maybe the MBR is corrupted.
If you clear the MBR and you still cant install XP it may be a hardware issue.
Are the EXT3 partitions still on the harddrive.
Usually with a Windows install it just ignores ext3 partitions like they don't exist. So as long as there ample space it will just go for that.
If all you have is ext3 partitions you need to delete them and format.

---

### Post by ferunandesu on 2007-07-09
> **vexorian said:**
> Not really, he specifically said it was an ubuntu problem which it isn't, I am not sure  why this forum  and (not the one dedicated to windows) should also give windows install support, which is supposedly MS' job...

If installing Ubuntu altered the boot sectors so that my XP setup disc now crashes, then, as far as I'm concerned, it's a problem that should be addressed on this forum. You can argue all you want about the Windows setup process being the real culprit, but that doesn't help me solve the problem. I consider myself a pragmatist, and I don't really care about getting into a debate about causality, knowledge, formal vs. informal logics, cogito ergo sum, and the general nature of the universe. 

You may be saying to yourself, ":confused:", but I've been around enough forums to know that things tend to go south when people start referencing informal logical fallacies. It's rude and lacking discernment.

With that said, thanks to the people who helped!

---

### Post by Church.Cameron on 2007-07-09
OK  so heres my solution and its the easiest one ready....

1 open up the tower/or laptop hard drive tray

2 take out hard drive

3 if you like the hard drive keep it for senmental value ( ahh good times )

4 go to your local computer store or go online and purchase another HD ( and get a good one over 120 GB)

5 install

6 take a break and watch some paint dry ( always fun)

7 getout that piece o crap windows

8 install

9 let t do its thing 

10 make ubuntu ( after windows is done) a virtual componet. 

it will then be a dual boot system andyou will have a brand new hopefully awsome HD

its that simple

if you can't afford a HD steal one ( i am joking )


REMEBER THE OPEN SOURCE MOTTO: " USE OpSrc AT YOU OWN RISK "


:popcorn: cani offer you some delcious ubuntu and popcorn anyone ?

---

### Post by mariosbar on 2007-07-09
I f you can get into ur deskyop thn just uninstall ubuntu but if u cant even boot up use the recovery console on the boot disc and on the black screen type c:\chkdsk/ r this recover ur comp hopefully but it can take anywhere from 2 hours to a day depending on the problem

[www.marios-bar.com](www.marios-bar.com)

---

### Post by dorath on 2007-07-10
> **ferunandesu said:**
> When I boot from the installation disc, it says that setup is detecting my hardware configuration, and then it blacks out.

What's wrong here?

Depends on where you're at in the installation, and unfortunately I can't tell by your post.  A bit more information could help.

If you're in *text-mode* setup, the part right after you boot off the CD and before the first reboot,  when the problem occurs then I would suggest the following:
-Power down the machine and disconnect the power to the hard drives.
-Start up the machine and boot off the XP install disk.
-If the install progresses past the point at which it has been crashing, then it is safe to assume that the hard disk is somehow involved.
-If the install crashes at the same point, I'd suggest trying a different XP CD, or running memtest x86, or something less drastic before wiping out your drive.

If you're in *GUI-mode* setup, and you're crashing during the PnP hardware detection/configuration, then you're probably going to have to slipstream some drivers into a new install CD.

Your best shot is to do everything you can to narrow down the possible causes before laying the blame squarly on the drive (or it's contents) and wiping out everything you've got.  This can be tough if you don't have extra parts laying about, or a spare PC to cannibalize.  Best of luck!

---

### Post by SoloSalsa on 2007-07-10
Tell us how far you are, any success?

---

### Post by ferunandesu on 2007-08-15
I blanked the disk and everything worked.

---

