---
title: "Partitioning for dual-boot."
date: 2005-04-30
forum: Apple PPC Users
---

### Post by Chunga on 2005-04-30
What I'm looking to do is set up my partitions to dual-boot between Tiger and Ubuntu.  I've already installed Tiger (loving it by the way), and now I just need to get Ubuntu installed.

When I installed Tiger, I repartitioned my hard drive with one HFS+ for Tiger and one "free space" partition.  I assumed that the Ubuntu installer would allow me to repartition the free space without messing up my HFS+ partition, but I can't see how it would be done.  The installer seems to insist on partitioning the entire disk.

From reading the documentation, it seems like I should be able to do this, but perhaps I missed something somewhere.  Does anyone have any suggestions for me?

---

### Post by kirsche on 2005-04-30
Try to start the installation in expert mode.

---

### Post by Chunga on 2005-04-30
It looks like expert mode uses the same partitioner, partman.  Are there any other partitioners on the install disk?

Thanks.

---

### Post by fordfan753 on 2005-04-30
I partitioned my drive with the Ubuntu installer...
When it gets to the partition bit it will say something like "erase full disk hda" and a couple of other things, one of the other things should be "manual partitioning" or something along those lines. Just use that to partition the free space, and format it as ext3

---

### Post by Chunga on 2005-04-30
Yes, I recall it has two options (besides Go Back).  One clearly erases the entire disk and the other is manual mode.  When I choose manual mode it goes to a screen with a bunch of options.  Enable RAID is an option as well as enabling something else.  Guided partitioning is also offered.  It also lists my entire disk there as one big 'free space' partition.  Adding partitions, even in doing the guided thing will always make partitions from this big free space partition which partman thinks is the the disk.  It's as if this partitioner is not even looking at the partition table on the disk.  :shock: 

So is partman just being especially difficult for me or is it thus limited?  I guess since it worked for you, it's a special problem or something.
Either way, if there is another way to do the partitioning I'd sure like to know about it.

Thanks.

---

### Post by chascon on 2005-05-01
You're missing something because its always worked like a charm for me.  I can't help you becaue its intuitive and therefore not 'describable' for me.

---

### Post by Chunga on 2005-05-01
I didn't ask you to describe the process to me.  I already know what it is supposed to be doing.  The problem is that partman is ignoring the partition map on the disk and therefore only offering to partition the entire thing.  I have found partman to be very "intuitive" as well, but that doesn't help my problem.  Fortunately I was able to just execute the shell and find mac-fdisk which worked perfectly as usual.  Thanks anyway.

---

### Post by dkitty on 2005-05-01
I've wiped my iBook's HD and will be installing OSX.2 (Jaguar) and Ubuntu in a bit. I've done it a few times before. It's pie. I seem to remember that when choosing how to partition for ubuntu I had to select manual formating, then select the free space, then choose an option along the lines of "automatically partition free space." The partitioner got busy and all was well.

I'll try to remember to post a few details here as I do it again later today.

---

### Post by dkitty on 2005-05-01
When you reach the !!Partition Discs portion of the installer:

1. Manually edit partition table

2. Highlight Free Space (near the bottom, likely above "undo changes to partition") and press enter

3. Highlight "automatically partition the free space" and press enter. The installer will computer the partitions and show you another screen complete with suggested swap and what not

4. Select Finish Partitioning and write changes to disc. Press enter.

5. Highlight "Yes" at the next screen and press enter

C'est fini. Just continue on with the installation from then on out

---

### Post by Chunga on 2005-05-01
Hey dkitty,

Thanks for this info.  This is more or less what I thought.  The problem is that on step #2, there is no "free space" option for me.  There is only the disk, and selecting that does give the option to "automatically partition free space," however it assumes that the entire disk is free space.  I have no idea why partman doesn't give me the option...  It might just be the way I partitioned the disk before I ever got to the Ubuntu installer.  There is a case-sensitive HFS+ partition on there, which is a new type, so perhaps it's messing up on that.  Who knows.  Anyway, I'm glad it is working well for most people.  I won't hold it against your beloved Ubuntu.  The entire installer was very intuitive.  I especially liked determining the keyboard layout (just type a key from a list and it's figured it out automatically).

Thanks again.

---

### Post by chascon on 2005-05-22
dkitty is correct. But if this doesn't help.
It's simple to go into OS X and find out the assignment that OS X gives the OS X partition and any other partitions.
You should be able to identify OS X from this.  It should be easy to figure out because OS X and Freespace will be the largest partitions.  If you find OS X, the other larger file should be the Freespace.  OS X will have something about HFS too.

---

### Post by pitpoule on 2005-05-24
I have then same problem. I've erase all disk before installing tiger. Then i've installed tiger with one HFS+ journalized case-sensitive partition and two unix partition. Then when I install ubuntu, i can't see any of those parts.
I had installed ubuntu with panther few weeks with same install cdrom and it worked great.

pit.

---

### Post by onizuka on 2005-06-03
hi,
just tried the Ubuntu Live cd on my G3-900Mhz worked a treat :)
my only worries is my wifi usb dongle working and i couldnt find an eject button to insert a driver disc
if that works then i wont have to buy an Airport card (which are rare)  :-# 

it seems a hell of a lot faster than MOSX but im still not prepaered to jump as i need adobe suite & more for my coursework  :neutral: 

im sure i can get used to gimp but what about pro audio and video editing tools? and i wouldnt know where to start with 3D graphics on *nix  ](*,) 
actually if all the above were solved id have Ubuntu on my AMD64 box also :grin: 


anyway back to the topic, is there anyway of just resizing my mac partition, with the free space make a small partition for testing Unbuntu properly?

i dont want to have to reinstall everything, even if i could make a drive image backup, so i can format and have a working copy of the old MOSX/APPS & files
ive got a PC program for this but unsure on macs

any help much appreciated

tia
Onizuka

---

### Post by dkitty on 2005-06-03
[QUOTE=onizuka]anyway back to the topic, is there anyway of just resizing my mac partition, with the free space make a small partition for testing Unbuntu properly?[/QUOTE]

I've heard that iPartition works well. Ditto VolumeWorks, if you don't mind the 60 bling. Though I've not tried either myself.

---

### Post by dbu on 2005-06-06
Yes; the partitioner in UBUNTU is broken.  Paritions exist; the no options to talk to them.  Both `cat /proc/partitions` and mac-fdisk see  partitions, but the debian/ubuntu installer does not.  
Even if i drop into mac-fdisk and manually set up a linux and swap partition, and even if I proceed to format the linux partition up with ext3, the installer see no partitions.  

What is the partitioner looking for in a partition?  Are there any logs somewhere that can be generated to sort out why it thinks there are no partitions?  

This is the same result I get with Warty, Hoary, and even the Beta 5.10 PPC CD.

[Ibook G4 / Tiger, /dev/hda1-11 exist according to /proc/partitions]

---

### Post by Chunga on 2005-06-09
Hello again,

Yup, the installer is broken.  For what it's worth, if you can manage to at least create the partitions using mac-fdisk, it is possible to install the base system.  After the partitioner runs, the root partition is expected to be mounted at /target so after creating the partitions you just mount it manually.  The installer will also try to unmount /target for some reason, but if you rename /bin/umount to something else it should work.

All of this is pretty pointless though, because yaboot-config fails as well.  What we really need is the problem to be fixed.  It's pretty apparent that Tiger did something unexpected to the disk--perhaps the existence of new partitions like HFS+ (journal,case-sensitive) is enough to confuse the installer?

Anyway, here's hoping it's fixed soon,
chunga

---

### Post by loading on 2005-06-09
I have exactly the same problem... Is some help near already?

I thought, that maybe there's the possible chance to first install a debian base system (has the debian installer the same problem?) and then our beloved ubuntu system? is there a how to do that?

---

### Post by Chunga on 2005-06-12
FYI: the newly released Debian 3.1 installer **does** suffer the same problems.

---

### Post by Gex on 2005-06-12
Just installed unbuntu with tiger today without really knowing what to do, but I'll tell you how I did it.  First I went to partion with the OSX disc and used disk utility and made one partion for 65 GB to use with OSX and the other 10 GB I left it as "Free Space".  Installed tiger with out a hitch and moved on to linux, I don't know if it makes a difference or not but I d/l the DVD ver. from bit torrent.  Now when I ran the Unbuntu installer there was a third option which gave Ubuntu use of the free space.  I picked that option and the rest was done.  If I want OSX I just boot up my PB, if I feel like linux I just hold down the "option" key and pick the linux partion.

---

### Post by Chunga on 2005-06-13
Just for troubleshooting purposes, what format did you use for the Tiger partition?  I doubt the DVD version has anything different with the installer, but I'm beginning to think the case-sensitive HFS+ partitions are the cause of these installer problems.

---

### Post by wallijonn on 2005-06-15
I installed OSX 2.2 and I couldn't get Ubuntu to install on the second partition - it always starts in OSX. 

Installing OSX was not the easiest thing to do, either as I had to set it to OSX standard instead of extended. I formatted the other partition as Unix (just in case). I was finally able to install OSX after rebooting but I could never get Ubuntu to install. 

Maybe I'll try holding down the option key as suggested.

---

### Post by loading on 2005-06-15
I have found a solution for our problem, there are two ways to install ubuntu after tiger...

1. install it from a ubuntu-livecd. you'll find explanations over here: [install ubuntu from livecd](http://www.willmer.com/kb/2005/02/installing-ubuntu-hoary-from-livecd/) 

2. install ubuntu as chunga explained you already with every steps you can do... and then boot the system with some livecd, chroot the root partition and
- configure apt-get with "apt-setup"
- do an "apt-get update"
- finish the installation with "apt-get install ubuntu-base ubuntu-desktop"
- then configure /etc/fstab and /etc/yaboot.conf
- install the bootloader with "ybin -v"

hope you are lucky with that...

---

### Post by loading on 2005-06-15
i forgot something: apparently this thing only works, when the mac-volumes are formatted without the case sensitive thing...

---

### Post by chombier on 2005-06-21
[QUOTE=loading]i forgot something: apparently this thing only works, when the mac-volumes are formatted without the case sensitive thing...[/QUOTE]
 As explained by Apple [here](http://developer.apple.com/technotes/tn/tn1150.html#HFSX), case-sensitive HFS+ volumes have a new partition type, "Apple_HFSX" instead of "Apple_HFS" this is to avoid bad repair tools to destroy the new volume format.
Looking in the parted debian source repository, it seems that case-sensitive HFS+ has been implemented 3 months ago, in parted version 3.6.2.
When I type parted --version here on my Ubuntu Linux PPC Hoary, it says "GNU Parted 1.6.20 with HFS shrink patch 16"
Sounds like it's time for an upgrade of parted in ubuntu ppc distro...

---

### Post by sf-andrew on 2005-06-21
[QUOTE=Chunga]Hello again,

Yup, the installer is broken.  For what it's worth, if you can manage to at least create the partitions using mac-fdisk, it is possible to install the base system.  After the partitioner runs, the root partition is expected to be mounted at /target so after creating the partitions you just mount it manually.  The installer will also try to unmount /target for some reason, but if you rename /bin/umount to something else it should work.

All of this is pretty pointless though, because yaboot-config fails as well.  What we really need is the problem to be fixed.  It's pretty apparent that Tiger did something unexpected to the disk--perhaps the existence of new partitions like HFS+ (journal,case-sensitive) is enough to confuse the installer?

Anyway, here's hoping it's fixed soon,
chunga[/QUOTE]
 I am having the same sort of problems trying to install onto a disk that contains a FAT32 partition, which suggests that the problem is across the board. The Ubuntu partitioner does not show the partitioning that I know to be present - I have checked it out with Knoppix and RescueCD.

Oh... and the LiveCD won't boot on my machine, either. Knoppix has no problems...

---

### Post by Chunga on 2005-06-21
[QUOTE=sf-andrew]Oh... and the LiveCD won't boot on my machine, either. Knoppix has no problems...[/QUOTE]
Hmm, this doesn't look like it's related to the partman/installer issues.  You should create a new thread about this if you haven't already.

---

### Post by mikelegurra on 2005-06-21
hi,

someone talked about using ipartition. i did and it worked great.
i had panther installed at the time, used ipartition to resize my mac os partition and used the rest of the space to create 3 new partitions. one boot, one swap and a third ext3.
started the ubuntu installer and pointed the installer in the right directions.
everything worked as a charm.

weeks later i upgraded to tiger and i could no longer choose at boot time if i wanted linux or mac os. i used the option key down method and ran 'sudo ybin' at the terminal.
everything works as before.

hope this helps someone.

---

### Post by Len on 2005-06-22
EDIT: Sorry, didn't notice the thread was 3 pages instead of 1, too early in the morning I guess...

[COLOR=Gray]Rather strange... you should be able to open fdisk (or pdisk) from another terminal in the installer or from the LiveCD and manually create your partitions. fdisk looks rather complicated to use at first, but it's actually doable. May sound strange, but try to delete the free space partition in fdisk and then try the installer again (sounds like OS X made a partition there or so). If that still doesn't work, create them with fdisk or whatever other command line utility. 1 bootstrap (1 MB), 1 SWAP (256-512 MB) and one / (1500 MB at least, can be ext3fs, xfs, reiserfs, etc). And don't worry, OS X has pdisk, you can reclaim your partitioned space with that one if you fail.

If you can't figure out you can always try inserting another linux distro to create your partitions with that :).[/COLOR]

---

### Post by kr3mliyn on 2005-07-09
[QUOTE=Chunga]What I'm looking to do is set up my partitions to dual-boot between Tiger and Ubuntu.  I've already installed Tiger (loving it by the way), and now I just need to get Ubuntu installed.

When I installed Tiger, I repartitioned my hard drive with one HFS+ for Tiger and one "free space" partition.  I assumed that the Ubuntu installer would allow me to repartition the free space without messing up my HFS+ partition, but I can't see how it would be done.  The installer seems to insist on partitioning the entire disk.

From reading the documentation, it seems like I should be able to do this, but perhaps I missed something somewhere.  Does anyone have any suggestions for me?[/QUOTE]
 Hi, I'm relatively new to the world of PPC Linux (ex Gentoo user), and a complete neophyte to Ubuntu. I have to say that, all in all, I am insanely impressed with how stable it is (well, besides minor issues with sounds and my keyboard, still haven't figured out where number-sign/hash key is, changed keyboard model to Macintosh, but no HASH!!!).

Back to the point, I had this problem with partman, so I cheated, I used mac-fdisk that comes as standard on the Gentoo Universal Install CD. I'd advise you download the miniature edition.

I have an iBook G4 800Mhz, 30GB, 640MB RAM that I have recently upgraded to Tiger (3 days ago!) and I was dreading the 4 day compile for Gentoo, so I thought I'd give Ubuntu a spin, and it's just amazing! I miss portage (emerge... sob...) but apt-get has a sort-of ring to it, I guess. Gentoo was/is TOO much hassle for PPC owners.

Good luck with the install (Note: - My HD is partitioned 7.5GB for Linux, and the rest for Mac OS X 10.4 Tiger... just having difficulty reading my HFS from Linux, ExtFSManager should be updated for Tiger in no time, so that side seems likely to be covered soon).

Later!

---

### Post by jcayo11 on 2005-07-09
I created 2 partions when I installed OS X and placed OS X on the second partion.
I used the disc utility that comes up with the Mac OS X cd.

Then I installed ubuntu on the first partion.

They both work fine, just that ubuntu is the default boot-up OS.

Not sure what to do in yaboot to make macosx the default.

I have placed a line in the yaboot.conf file "defaultos=macosx"
Not sure where it should go to make a diffrence though.

Here is my current yaboot.conf:

boot=/dev/hda2
device=/pci@f4000000/ata-6@d/disk@0:
partition=3
root=/dev/hda3
timeout=100
install=/usr/lib/yaboot/yaboot
magicboot=/usr/lib/yaboot/ofboot
enablecdboot
macosx=/dev/hda4
defaultos=macosx

image=/boot/vmlinux
	label=Linux
	read-only
	initrd=/boot/initrd.img
	append="quiet splash"

image=/boot/vmlinux.old
	label=old
	read-only
	initrd=/boot/initrd.img.old
	append="quiet splash"

Any help would be useful.

---

### Post by HughC on 2005-07-12
I'm very much a novice to linux and Ubuntu, but like the idea of running Ubuntu on my G3 iMac (400MHz, 126kB RAM, 12 GB hard disk).

(I hope this is the right thread, too: it's about partitioning for dual boot, but with OS 9, not OS X)

I'm cautious about partionining my hard drive, but as that's my only option (I can't lose my ability to boot in Mac OS 9), I'm seeking reassurance that the procedure described by dkitty below won't overwrite all OS 9 system, applications and files.

Can someone also confirm that I don't have to have partioned my hard drive before the Ubunto installer partitions it?  I wouldn't know how to partition it from Mac OS 9.

I'm hoping that if I've left at least 2 GB of free space on my HD, that will be enough

Since I'm starting with OS 9, I think my issue is different from Chunga's initial query.

The live CD is very very slow on my system (I aborted attempts to launch the Gnome help program, and the OpenOffice word processor, both after 2 hours without success), but I hope that a proper install will make it worth running.  If anyone has any experience to contrary with old processors with small memory, I'd be interested to know.

thanks!


[QUOTE=dkitty]When you reach the !!Partition Discs portion of the installer:

1. Manually edit partition table

2. Highlight Free Space (near the bottom, likely above "undo changes to partition") and press enter

3. Highlight "automatically partition the free space" and press enter. The installer will computer the partitions and show you another screen complete with suggested swap and what not

4. Select Finish Partitioning and write changes to disc. Press enter.

5. Highlight "Yes" at the next screen and press enter

C'est fini. Just continue on with the installation from then on out[/QUOTE]

---

### Post by nder on 2005-07-17
@HughC For dual booting with OS9, you may find [this article helpful.](http://people.debian.org/~branden/ibook.html)

Has anyone found a solution to the HFS+ Case Sentitive partition issue?  I can't get the bootloader on via the installer.  I'll probably have to do the live CD chroot solution, but I was hoping that a fix was issued.

---

### Post by CloudStrife on 2005-08-04
[QUOTE=nder]@HughC For dual booting with OS9, you may find [this article helpful.](http://people.debian.org/~branden/ibook.html)

Has anyone found a solution to the HFS+ Case Sentitive partition issue?  I can't get the bootloader on via the installer.  I'll probably have to do the live CD chroot solution, but I was hoping that a fix was issued.[/QUOTE]
I've found a solution :
I've booted on the Fedora Core 4 PowerPC install CD. The installer can partition my disk (if it says error, just click on "ignore").
When the disk is OK, you can stop the installation of Fedora and boot on the Ubuntu install disk. Now the installer can see the disk !
(I've tried the installation of Fedora, but Anaconda crash everytime ...)
So now I've OSX on HFSX, and Ubuntu on ext3 (but I don't have access to OSX file on Ubuntu nor Ubuntu files on OSX...)

---

### Post by leverknight1 on 2005-08-08
[QUOTE=Chunga]Yes, I recall it has two options (besides Go Back).  One clearly erases the entire disk and the other is manual mode.  When I choose manual mode it goes to a screen with a bunch of options.  Enable RAID is an option as well as enabling something else.  Guided partitioning is also offered.  It also lists my entire disk there as one big 'free space' partition.  Adding partitions, even in doing the guided thing will always make partitions from this big free space partition which partman thinks is the the disk.  It's as if this partitioner is not even looking at the partition table on the disk.  :shock: 

So is partman just being especially difficult for me or is it thus limited?  I guess since it worked for you, it's a special problem or something.
Either way, if there is another way to do the partitioning I'd sure like to know about it.

Thanks.[/QUOTE]

use the guided partion and select the use free space option and then use the all in one partion setup this is the easyest way to do it.i had the same problem at first until i used this sceme it isnt hard to do but it takes a while.
I started doing this last night and i am writing a How-to on it at the moment to be tested by my friend it should be posted in less than 2 weeks but i will post it once it is easy to use/understand.

---

