---
title: "Taking the Plunge"
date: 2007-04-05
forum: Absolute Beginner Talk
---

### Post by dschultz on 2007-04-05
I've been a Windows user all my life and am currently a Network Administrator for a grocery supply company.  I'm great with all flavors of Windows.

At home I have a powerful system that I recently installed Windows Vista X64 Premium on.  I can't say this enough, Vista is total garbage.  I've never been so unhappy with a Windows O/S in all of my life.  I've had it, enough is enough.  I'm moving to Linux.  After reading through countless web pages full of opinions on which version of linux to install and I've decided to go with Ubuntu.

I had almost no problems installing Ubuntu on my laptop.  The only problem is my built-in camera and I can live with that.  I already spent hours digging around only to discover the camera is just not supported because nobody has ported the drivers for the camera's chipset.  Okay, I need to get to the point here... 

My desktop PC has been a real challenge and I'm at the point of frustration.  So, here I am signed up for the forums and posting my challenge:

I have a SATA raid controller on the motherboard.  If it's fake... okay great... I can live with that even though I dropped $200 on the MB thinking it was going to be blazing fast.  I want to install Ubuntu 6.10 on the desktop.  I have 3 SATA drives plugged into the SATA RAID 1,2,3 slots on my mother board.  Drive 1 is 300gb, Drive 2 is 300gb, and Drive 3 is 400gb.  In the raid controller which loads a config in the bios during POST I was able to group all three hard drives and set them up for a Raid-0. I know, I'm living on the edge with Raid-0 but I'm going for performance here.  

I first tried the standard Live CD install and when Ubuntu loaded up from the CD, I went with the little "INSTALL" shortcut on the desktop.  This gave me an option to install on ONE of the three drives... so.. it doesn't see the raid-0 array as one big 1 Terabyte drive... choosing manual doesn't help.  

I read that 7.04 supports SATA raid better than 6.10.  I downloaded the CD, burnt and did the "Install" shortcut from the desktop.  Same thing, doesn't see it as a RAID-0 array.  I only have the option of installing Ubuntu on 1 drive.

I found [THIS]("http://www.ubuntu-in.org/wiki/SATA_RAID_Howto") guide for installing my SATA raid-0 while booted into Ubuntu live.  I followed each step, very carefully and in the order the steps are presented.  When I start up GParted I do NOT see the raid array as the guide shows.  Instead, I only see the 3 separate drives.  So, this guide doesn't do anything for me because it dies when I try to look for the /dev/mapper/XXXX in GParted.

I went ahead and did the sudo dmraid -ay command and it displayed:

RAID set "SIL_ahaeaeccajch" already active

When I browse to "/dev/mapper/" I can see that SIL_ahaeaeccajch is in there but it has a red [X] over it.

I found a guide that says I needed the "Alternate Live" CD so I downloaded that and burnt that to CD.  When I got to the part where I setup the drives I was very confussed.  Boy do I miss the ole fashioned FDISK in dos... anyway... have hours and hours of looking around, researching, and reading through countless guides I sort-of figured out that I need to setup each drive as RAID - K with mount option turned ON and each drive needs to be LOGICAL as opposed to PRIMARY.  Now, I get my raid array showing up as a nice big 1 Terabyte drive but... when I create the SWAP partition... it tells me that the other 985gb are Unusable... *sigh*  So I cannot create the swap and /root on the 1TB raid-0 drive I created in the confusing gui-shell linux thingy.  I know I'm a noob and I'm willing to go through hell and back in order to start using linux even though I know I'll continue going through hell to get my programs and games to work (wish it were easier).  The only option I see at this point is to ask for help or just forget using my nice raid feature and install Ubunto on 1 of my 3 disks and let the others just... do nothing?  I'd really like to take advantage of this raid config and have a nice big 1terabyte drive instead of it being broken up into pieces.  I could go out and buy a SATA raid controller for my PC too if that would help.  Any advice would be appreciated.  Thanks for reading my verbose post.  :)

---

### Post by arbulus on 2007-04-05
I actually would be interested in the solution to this as well.  I have Ubuntu installed on my server and it has 4 HDDs @ 9.10 GB each.  But as far as I could tell, i couldn't set up separate partitions on a RAID (/ /boot, and swap).  So what I had to do was create 2 partitions on the first HDD one boot, one swap, and then the other 3 HDDs are a RAID 0 where the / partition is.  I just hate to waste so much space on the first drive because neither boot nor swap need 4.5 GB each, and I feel like it's actually not the best set up in the world.  i've never had any problems with it, but i figure it could be faster if the boot and swap weren't arranged the way they are. Also, this is just a software RAID, I don't have a hardware controller, and the HDDs are scsi.

So would it be possible to further partition a RAID?  I guess I'll give an example for my situation

The optimal situation I would like:
4 HDDs @ 9.10 GB each = 36.4 GB RAID 0
Then further partition that RAID into a 100 MB boot, a 320 MB swap, and the rest root.
So is that possible?

From what he's descrbing, it seems like this is the same thing that dschultz is aksing about (at least I hope so anyway).  If not, I sincerely apolgize and in no way meant to hijack the thread.

---

### Post by jerryrw on 2007-04-05
One solution is to make a small /boot partition and then use LVM on the others.

As far a performance depending upon use *nix can sometimes do better with things split across a bunch of smaller partitions rather than in one large one.

---

### Post by dschultz on 2007-04-05
From my understanding, when you setup a RAID-0 array you have all the drives working together at the same time on your read/write requests.  The more hard drives working on your request, the faster the data is read/write.  It's like having 3 vaccum cleaners working in the same big room together at the same time as opposed to having 3 vaccum cleaners all in seperate rooms, sometimes one is turned on, sometimes one is turned off.

Raid-0 therefore is a faster choice.  That's the way it's been in my experience with SCSI raid arrays in Windows based servers.  When I setup a RAID-0 on a SCSI raid controller, I setup the RAID set in the scsi controller's bios... choose my drives, choose my raid-0 and poof.... Windows 2003 server sees all my drives as ONE BIG drive.  One big seemless, high-speed blog of storage where I put my apps and my O/S with lightning fast data access.

The problem appears to stem from my "raid" not really being true "raid".  Or is it?  Like the SCSI controller in my servers, I am presented with a RAID setup during POST.  I hit CTRL-R and choose the drives and choose the RAID-0 and now my 3 drives are one big drive when it comes to loading Windows Vista... I hate Windows Vista.

It looks like real raid, it acts like real raid, and on Windows Vista... it behaves like real raid.  But, [THIS ]("http://linux-ata.org/faq.html")guy thinks everyone's got fake raid. 

I'm going to assume I have fake raid and use [THIS]("https://wiki.ubuntu.com/FakeRaidEdgy") guide to try... once again... to install Ubuntu on my raid configuration.  While Ubuntu was very easy to install with 1 hard drive, it's a total nightmare for a noob doing it on a SATA raid-0 setup.

---

### Post by dschultz on 2007-04-05
Further problems...

Using [THIS]("https://wiki.ubuntu.com/FakeRaidEdgy") guide did not help me configure my fake raid.  I'm wondering if it's because I'm using the 64AMD version of Ubuntu 6.10.  When I get to the step where you enter the command "dmraid -ay" the command prompt reports that the file doesn't exist.  After a few days of battling to simply get Ubuntu on my Raid-0 SATA setup, I'm unable to find any more How-to's.  Any help would be greatly appreciated.  I've put so many hours into this I'm still up to trying anything anyone has before I go back to Windows Vista (i just threw up in my mouth a little).  The good news is, I've learned quite a bit about Linux.

---

### Post by Maestro23 on 2007-04-05
> **dschultz said:**
> Further problems...

Using [THIS]("https://wiki.ubuntu.com/FakeRaidEdgy") guide did not help me configure my fake raid.  I'm wondering if it's because I'm using the 64AMD version of Ubuntu 6.10.  When I get to the step where you enter the command "dmraid -ay" the command prompt reports that the file doesn't exist.  After a few days of battling to simply get Ubuntu on my Raid-0 SATA setup, I'm unable to find any more How-to's.  Any help would be greatly appreciated.  I've put so many hours into this I'm still up to trying anything anyone has before I go back to Windows Vista (i just threw up in my mouth a little).  The good news is, I've learned quite a bit about Linux.

For the "dmraid" command, you need to install it from the repositories.

> sudo aptitude install dmraid

If you don't find it, you need to enable extra repositories: [https://help.ubuntu.com/community/Repositories?action=show&redirect=AddingRepositoriesHowto](https://help.ubuntu.com/community/Repositories?action=show&redirect=AddingRepositoriesHowto)

---

### Post by dschultz on 2007-04-05
In the guide I followed for setting up a fake raid, I was told to copy the DMRAID and other files to a USB stick, mount the stick and install DMRAID from there.  I did that.  But when I actually go to run DMRAID, it doesn't find it.  

Now, your saying that I need to follow the sites you gave me in order to enable repositories, download DMRAID (which I did but it's on a USB stick) and then I'll be able to run the DMRAID command?

sudo aptitude install dmraid

Didn't work so I'm going to research how it is I turn on the repositories... so that I can install them.  I don't get it though.. I thought downloading the DMRAID to a USB stick and installing from there was enough...

---

### Post by Maestro23 on 2007-04-05
> **dschultz said:**
> In the guide I followed for setting up a fake raid, I was told to copy the DMRAID and other files to a USB stick, mount the stick and install DMRAID from there.  I did that.  But when I actually go to run DMRAID, it doesn't find it.  

Now, your saying that I need to follow the sites you gave me in order to enable repositories, download DMRAID (which I did but it's on a USB stick) and then I'll be able to run the DMRAID command?

sudo aptitude install dmraid

Didn't work so I'm going to research how it is I turn on the repositories... so that I can install them.  I don't get it though.. I thought downloading the DMRAID to a USB stick and installing from there was enough...

Ah, sorry.  Didn't read far back enough in this thread.  Didn't know you were downloading stuff to a flash drive and then trying to do commands.

When you run dmraid from the usb stick, and it doesn't find anything, does it give any kind of error?

---

### Post by dschultz on 2007-04-05
> **Maestro23 said:**
> Ah, sorry.  Didn't read far back enough in this thread.  Didn't know you were downloading stuff to a flash drive and then trying to do commands.

When you run dmraid from the usb stick, and it doesn't find anything, does it give any kind of error?

Okay, in the guide I am to perform these steps to copy and then install the files from my USB drive (called /mnt) to my installation drive..thingy lol:

cp -r /mnt/udeb tmp
udpkg -i tmp/udeb/libdevmapper1.02-udeb*
udpkg -i tmp/udeb/dmraid-udeb*

Which looks like this:
~# cp -r /mnt/udeb tmp <ENTER>
~#
~# udpkg -i tmp/udeb/libdevmapper1.02-udeb* <ENTER>
(Reading database...)
(Updating database...)
~#
~# udpkg -i tmp/udeb/dmraid-udeb* <ENTER>
(Reading database...)
(Updating database...)
~#

In the next steps I am to run DMRAID and here is what I get
~# modprobe dm-mod
~#
~# dmraid -ay
/bin/sh: dmraid: not found

If you want I can contact you on any messenger your using, I have GAIM setup on my laptop and my laptop is setup next to the computer I'm trying to get Ubuntu installed on.

---

### Post by dschultz on 2007-04-06
Well it looks like I've lost the war.  I have a Silicon 3114 SATA raid chipset.  Funny that Silicon Image supports linux on this SATA RAID chipset.  It even has a driver download site for linux and lists the current linux kernel to support thier raid chipset ([click here to see]("http://www.siliconimage.com/support/supportsearchresults.aspx?pid=28&cid=3&ctid=2&osid=2&")) To me, it seems that the latest Ubuntu release should fully support not only my chipset, but also that it shouldn't have a problem automatically recognizing my RAID-0 array from the live CD.  I thought I was wrong and even tried 7.4 which boldly indicates that it's got better support for SATA raid chipsets.  Hell no, not in my experience.  I have 3 drives setup in a RAID-0 configuration where all 3 drives stripe accross.  I did this not for contingency (obviously) but for a boost in read/write performance when loading apps/games/photos/etc.  Here is what I tried to make this work in Ubuntu:

1.  Downloaded 6.10 / 6.10 alternate / 7.4 / 7.4 alternate
2.  I've tried the basic install from the live CD
3.  I've tried using DMRAID+Gparted within 6.10/7.4 live but Gparted doesn't see /dev/mapped/SIL_XXXXXXXXX 
4.  I've used the forums with no solid reply.
5.  I've used 4 separate online how-to's to get this to work.

I have spent a total of 14 solid man-hours, 8 blank CD's, and lots of coffee trying to get Ubunutu to simply recognize my raid so that I can install using RAID-0.  After all of this, I can safely say that Linux just isn't ready for prime time with my hardware.  However, all is not lost... I'll keep Ubuntu on my laptop and take note of it's progress in the world of fake raid.

I was a bit dissapointed in the Ubuntu communities ability to help me with my problem but then I realized something... looking at these forums... thier is a LARGE and CONSTANT stream of "help me" threads pouring into these forums.  I can't imagine that thier are enough people who know what they are doing to help everyone at all times all around the world... 

Thank you and while it was frustrating and it lead me to nowhere, it was a learning experience.

---

### Post by 1ino1eum on 2007-04-06
sorry but first : linux is not only ubuntu ... 
6.10 is a bit too old to suport shiny new hardware, and , you seem to forget, but feisty is still in beta and every days there is new upgrades, even for the dmraid package.

So, my advice is to try another distribution, which might have a better suport for sata fakeraid.
You should try the fedora distribition, their suport for fakeraid works great.
Then, you are free to give another try the 19th of april with the stable release of feisty ;)

---

