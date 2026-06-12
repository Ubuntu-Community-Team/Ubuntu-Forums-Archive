---
title: "Yet Another Dual-Boot Question"
date: 2006-03-28
forum: Absolute Beginner Talk
---

### Post by da5id on 2006-03-28
I have run the Ubuntu Live disc and I boot into Ubuntu without much problem.  It seems to "see" all of my hardware and allows me to use my USB mouse and keyboard, LCD monitor and motherboard network interface adapter -- i.e., I can surf the Internet with Firefox without problem.  Alas, even though it correctly sees and identifies my SoundBlaster Live!  audio card, I couldn't get any sound and one of my USB devices, a mechanical hundreds CD/DVD storage/database "solution" cycles around and around (it's kind of a carousel type thing).  Other than that, a pretty good start I think.Now, of course, I want to run the Ubuntu from one of my hard drives.  I've read many of the existing posts on the subject but still have questions.  I was unable to find the "Windows XP and Linux dual-boot tutorial" reference by one poster.

First of all, I did see a reference that Ubuntu can't install on a machine with more than five hard drives (mass storage devices.)  I have more than that, to wit:  A -- floppy; C: -- a single physical/logical 36 GB internal SATA; D: second physical internal SATA drive with three logical partitions D:, H:, and K: (this is an empty 20 GB partition I created with Partition Magic specifically for a Linux installation); E: internal CD-RW optical drive; F: 275 GB Buffalo Technology Linkstation (this is connected to my wired/wireless router by an ethernet cable and can mostly be used and external hard drive; G: -- memory card reader integrated into my floppy connected to one of the internal motherboard USB connectors; H: -- second logical partition on second internal physical hard drive (on D); I: another removable memory disk reader probably daisy chained to G:; J: external DVD-RW Plextor optical drive connected by FireWire to a PCI FireWire card.  To summarize:

A: -- floppy with two memory card slots
C: -- primary physical  drive for Windows XP Home
D: -- secondary internal physical SATA drive
E: -- internal IDE CD drive
F: -- external LAN drive
G: -- internal memory card reader
H: -- second logical partition on D:
J: --  external FireWire DVD -RW drive
K: -- third logical partition on D: -- I specifically made this last as an empty partition for a Ubuntu

Can I install Ubuntu on this machine.  I understand from previous posts that I would be better just bringing up some space and leading Ubuntu make it to two partitions and install.  I'm fairly certain I can merge K: back into physical press D: with Partition Magic and give Ubuntu about 25 GB on D:.

Will this work?  From what I understand so far, Ubuntu does not install any boot manager, but rather, Windows will load all the time unless the Ubuntu CD is in my CD drive (which is, of course, bootable by just putting it on the list, as it is now, in the BIOS).  It is any of this correct?  Am I missing anything?

This is about as close as I have ever come to actually installing a working Linux distro on the hard drive of a Windows PC.  Any assistance will be greatly appreciated.  Links that explain in detail how could dual-boot Linux and Windows XP are fine.  I would, however, appreciate any feedback as to whether my convoluted A through K looks like it has any pitfalls.  Thanks in advance for any assistance.

-- Gene

---

### Post by Stealth on 2006-03-28
Looking at the list you actually only need to worry about:
C: -- primary physical drive for Windows XP Home
D: -- secondary internal physical SATA drive
H: -- second logical partition on D:
K: -- third logical partition on D: -- I specifically made this last as an empty partition for a Ubuntu

I'm not sure where you read about installing Ubuntu witho more than 5 harddrives, but you really only have 2, with that network drive (assuming its your averagely mapped drive to some network shared). You can easily install Ubuntu in that "K:" partition, even though in the installer it will not be reffered to that but as hdb7 (probably, seeing as how its your second drive (hdb), 3rd logical partition (5,6,**7,**). So with sufficient space (if you just want to test, that may be split into a 9GB partition for Ubuntu, and 1GB swap space) it should work fine. 

And Ubuntu **DOES** install a bootloader, GRUB, which will auto-detect your Windows and allow you to choose either OS on boot. :)

---

### Post by aysiu on 2006-03-28
I'm with Stealth on this one.

Don't forget to visit this site before you set up the dual boot:
[http://users.bigpond.net.au/hermanzone](http://users.bigpond.net.au/hermanzone)

---

### Post by da5id on 2006-03-28
Stealth and Aysiu, thank you for your quick and concise responses.  It will probably take me a couple of days to download and burn the Ubuntu install ISO, read everything on the Australian dual-boot web site, create rescue disks, and doublecheck the hard drive number.  It seems to me that I have seen screenshots of boot loader/Linux installation screens and they usually identify the different partitions with information including size.  The size alone will be enough for me to see which one to point the installer to.  As I understand it, Ubuntu doesn't use NTFS and is going to create two Linux partitions within the K partition "space."  There are two Windows system folders there -- they are in every logical partition -- a trash can (Recycler) and a folder entitled "System Volume Information."  I was gratified to see the Ubuntu grand unified boot loader (GRUB ) described is nearly foolproof.  Do I choose which OS to default to or does it require a keystroke at every boot up?  I suppose this is just minutia and I'll find out when I find out.

Hopefully, my next post here should be something like "Eureka!"  :-)

---

### Post by Stealth on 2006-03-29
Yea, Ubuntu (and most Linux distros) use a filesystem called ext3 and another partition of swap space.

I suppose the folders there are just average storage folders, and not some strangely spread out Windows installation! :X

Yea GRUB is great, there will be a configuration file that will let you do many things, including select your default OS, to list all of them on start, or just to show a countdown (where you press ESC to get the list again) to autoboot into your default OS, and much more :)

---

### Post by Flanker35M on 2006-03-29
S!

 What I did was like this..I have one 160Gb and one 37Gb HDD. The bigger one is partitioned to 3 parts, the smaller one into 2. I did install Ubuntu on the smaller(and faster one too!) one's first partition (12Gb) and when asked added Grub to the C:\ where resides the product of MS. Flawless operation with the boot menu :)

 Just one question. As there seems to be several options available, like K8-SMP(Default), K8-SMP(Previous), K8-SMP(Recovery) etc. How can I make it that I can put the one I use, K8-SMP, to the top of the list and remove those that I do not use?  Thank you in advance!

 And the more I use this 64-bit version the more I like it. Browsing these forums has given quite a lot of tips and tricks for future reference :)

---

### Post by YuHoo on 2006-03-29
Though this is a bit off topic, I would read up on GRUB. When uninstalling linux you would remove it and possible with that your master boot record. After that you're screwed. But this post explains nicely what to do [http://ubuntuforums.org/showthread.php?t=76652]("http://ubuntuforums.org/showthread.php?t=76652")
I'd also back up my windows partitions before installing/uninstalling linux since bad stuff can always happen and there is nothing more saddening than losing term papers.

Good luck and have fun with your new operating system!

---

### Post by Flanker35M on 2006-03-29
S!

 Thank you for the heads up. I have uninstalled this Ubuntu a few times and Windows has not been affected in any way, works like before. But will look into this more now though. Thank you once more :)

---

### Post by da5id on 2006-03-29
Interesting FYI

When I wrote tech support regarding defragmenting my Buffalo Technology external LAN share hard drive they responded:

"The drive self-defrags.  That is the nature of the ext3 filesystem." 

-- Gene

[QUOTE=Stealth]Yea, Ubuntu (and most Linux distros) use a filesystem called ext3 and another partition of swap space.

I suppose the folders there are just average storage folders, and not some strangely spread out Windows installation! :X

Yea GRUB is great, there will be a configuration file that will let you do many things, including select your default OS, to list all of them on start, or just to show a countdown (where you press ESC to get the list again) to autoboot into your default OS, and much more :)[/QUOTE]

---

### Post by da5id on 2006-03-29
Flanker, 

I think we have very similar machines in so far as internal drives go.  My primary drive is a 37 GB Raptor (10,000 rpm) and a 160 GB Seagate as my secondary.  Since my Windows OS and numerous applications are on the extremely small Raptor I didn't want to partition it -- I am kind of superstitious about giving the operating system 5 or 10 GB of breathing room even though, as I recall, I have the swap drive for W he he indows set on the secondary physical drive.  I hope I have as much luck with my first Linux install as you seem to have had with your previous ones.

-- Gene

[QUOTE=Flanker35M]S!

 What I did was like this..I have one 160Gb and one 37Gb HDD. The bigger one is partitioned to 3 parts, the smaller one into 2. I did install Ubuntu on the smaller(and faster one too!) one's first partition (12Gb) and when asked added Grub to the C:\ where resides the product of MS. Flawless operation with the boot menu :)

 Just one question. As there seems to be several options available, like K8-SMP(Default), K8-SMP(Previous), K8-SMP(Recovery) etc. How can I make it that I can put the one I use, K8-SMP, to the top of the list and remove those that I do not use?  Thank you in advance!

 And the more I use this 64-bit version the more I like it. Browsing these forums has given quite a lot of tips and tricks for future reference :)[/QUOTE]

---

### Post by Stealth on 2006-03-29
There is no need to defrag ext3. I suppose he means it self-defrags in the way that ext3 is a better filesystem, and the way it stores its files and such is as if it was as clean as a defrag or soemthing!

---

### Post by da5id on 2006-03-29
Well, my Ubuntu installation was not a resounding success.  I followed the instructions on the Australian site, including the part that added a Fat32 partition -- that may have been pushing it.  Is it generally accepted that an NTFS based machine can utilize a Fat 32 partition?  The bottom line is I ended up with a small section, about 8 MB, of "unallocated" space on my C drive and lots space, a fat 32 partition , and a NTFS partition all within an "extended" partition on my second physical drive.  I lost 40 or 50 GB of of data -- mostly inconsequential backups of my DVDs I have not had a chance to burn.  Fortunately, anything important was backed up to my LAN drive.  There are some quirky things going on that are best explained graphically by Partition Magic and I would appreciate any suggestions as to where to go from here -- BTW, Ubuntu did not install it all.  I've looked at this forum carefully and I don't see how to attach files, such as a JPEG.  Does this forum not support attachments or am I missing something?  Any suggestions as to these partition issues will be greatly appreciated.  I want to get back on track to installing Ubuntu -- this time avoiding the complication of a Fat  32 partition

---

### Post by aysiu on 2006-03-29
I'm not sure what happened, but there shouldn't be any unallocated space if you choose to manually edit the partition table.

In any case, to attach a picture, scroll down to Additional Options and click Manage Attachments.

If you're editing an existing post, click on Go Advanced.

---

### Post by da5id on 2006-03-29
[QUOTE=aysiu]I'm with Stealth on this one.

Don't forget to visit this site before you set up the dual boot:
[http://users.bigpond.net.au/hermanzone](http://users.bigpond.net.au/hermanzone)[/QUOTE]

I did go there.  I followed all the instructions.  All 20 something steps.  Twice. I ended up with a lot of partitions.  I did not end up with Ubuntu.  Click link for a graphical representation of the results.  Any suggestions appreciated. Thank you.

[http://img88.imageshack.us/img88/5444/scap0198pd.jpg](http://img88.imageshack.us/img88/5444/scap0198pd.jpg)

---

### Post by aysiu on 2006-03-29
It looks as if Ubuntu's on /dev/sda6?
So it doesn't boot?
What happens when you boot your computer?
Did you install Grub to the MBR?

---

### Post by da5id on 2006-03-30
[QUOTE=aysiu]It looks as if Ubuntu's on /dev/sda6?
So it doesn't boot?
What happens when you boot your computer?
Did you install Grub to the MBR?[/QUOTE]

I do not think that 278 MB constitutes an install.  I have installed enough software to recognize the unpacking and installation process.  That did not occur.  I terminated the install process at a screen with a solid red background and a message, the gist of which was "nothing went right, there is no point in preceding."  Nevertheless, there was an option to continue.  I did not.  Does the Ubuntu Breezy Badger 5.10 install in 278 MB?

It boots into Windows, thank God.  I'm beginning to believe Windows XP takes a licking and keeps on ticking

If the installer installs GRUB to the MBR, then presumably I did.  The bootup process is the same so I assume that the Ubuntu boot loader did not install correctly -- isn't this what GRUB is?

Did you notice that the aggregate "Size MB" for the "second drive" (all the partitions listed in the graphic)  exceeds its capacity of 160 MB?  During the first install process is said there wasn't room to install something and that is when a "Free Space" entry appeared under the first drive (drive one) caption.  It was a small amount -- I thought it was the change made in the MBR to install grub.  As it turns out, it basically installed a 9 MB partition on my C: drive.  Did you notice that in the drive table?  I find that inexplicable.

Would it do any good to load up the Live CD for Ubuntu.  Probably it could access the Linux partitions that appear to have been installed.

I should have tried a simple install without messing around with a fat 32 partition -- I'm not even sure that Windows XP supports NFTS and Fat 32 on the same machine.


Thank you very much for your assistance.  I started about 2 p.m.on this-- I'll give it another try tomorrow.

---

### Post by aysiu on 2006-03-30
[QUOTE=da5id]I do not think that 278 MB constitutes an install.  I have installed enough software to recognize the unpacking and installation process.  That did not occur.  I terminated the install process at a screen with a solid red background and a message, the gist of which was "nothing went right, there is no point in preceding."  Nevertheless, there was an option to continue.  I did not.  Does the Ubuntu Breezy Badger 5.10 install in 278 MB?[/quote] No, no, you're right. I wasn't looking too carefully at the numbers. Ubuntu usually takes at least 2 GB of space if it's fully installed.

What's this solid red background with a message? That sounds really bad. I've seen a solid *blue* background on the Ubuntu installation, but not solid red. Maybe your installer CD's bad?

> 
It boots into Windows, thank God.  I'm beginning to believe Windows XP takes a licking and keeps on ticking

If the installer installs GRUB to the MBR, then presumably I did.  The bootup process is the same so I assume that the Ubuntu boot loader did not install correctly -- isn't this what GRUB is? I don't believe Ubuntu installed Grub fully if it's booting to Windows but not Ubuntu. Do you get a boot menu when you boot up, or does it go just straight to Windows? My guess is that if it installed only 278 MB of something, it probably didn't even get around to installing Grub.

> 
Did you notice that the aggregate "Used MB" for the "second drive" (although partitions listed in the graphic)  exceeds its capacity of 160 MB? It doesn't exceed 160 GB. In fact, I just did a total, and it totals 153 GB. The second part (67 GB) is for the entire extended partition, which has three logical partitions. If you add up the numbers, you'll see what I mean. > During the first install process is said there wasn't room to install something and that is when a "Free Space" entry appeared under the first drive (drive one) caption.  It was a small amount -- I thought it was the change made in the MBR to install grub.  As it turns out, it basically just installed a 9 MB partition on my C: drive.  Did you notice that in the drive table?  I find that inexplicable. Yeah, it's weird. It sounds as if it just did not install correctly, and it could be something wrong with your CD. Have you verified the disk image?

[http://www.linuxiso.org/viewdoc.php/verifyiso.html](http://www.linuxiso.org/viewdoc.php/verifyiso.html)

> 
Would it do any good to load up the Live CD for Ubuntu.  Probably it could access the Linux partitions that appear to have been installed. "[D]o any good" as in magically getting Ubuntu installed from its 278 MB? Probably not. You can, however, use the live CD to mount the Ext3 partition and see what folders got installed there--if any--just to see at one point the installation did fail.

> 
I should have tried a simple install without messing around with a fat 32 partition -- I'm not even sure that Windows XP supports NFTS and Fat 32 on the same machine. It does. The first six months (perhaps longer) I used Linux, I had something like this partitioning scheme:

1. XP (NTFS) 13 GB
2. data (FAT32) 100 GB
3. Ubuntu (Ext3) 20 GB
4. Mepis (Ext3) 20 GB
5. whatever-distro-I-was-playing-around-with (Ext3) 7 GB

---

### Post by da5id on 2006-03-30
[QUOTE=aysiu]No, no, you're right. I wasn't looking too carefully at the numbers. Ubuntu usually takes at least 2 GB of space if it's fully installed[/quote]

Inside the ~10 GB Ext3 partition created by the Ubuntu installer is a single folder entitled "Lost+ Found."  Ubuntu Live could not read any of the files within that folder.  I did try the usual stuff such as show hidden files, etc.

[QUOTE=aysiu]What's this solid red background with a message? That sounds really bad. I've seen a solid *blue* background on the Ubuntu installation, but not solid red. Maybe your installer CD's bad?[/quote]

I did an MDM sum check on the ISO file before burning it.  I did not carry out the extra steps of re-extracting an ISO image from the burned disc and checking its MDM sum.  However, I am very conversant with Windows CD and DVD burning procedures and I am fairly confident that I do not have a corrupted installation disk.  The screen with the red background I believe was a clear indication that I was attempting to do an action that the Ubuntu installer knew would result in the destruction of data on an existing NTFS partition.  You have probably never seen it because you have not had to, in utter frustration, bull-headedly pushed the installer to the edge of a cliff.

 [QUOTE=aysiu]I don't believe Ubuntu installed Grub fully if it's booting to Windows but not Ubuntu. Do you get a boot menu when you boot up, or does it go just straight to Windows? My guess is that if it installed only 278 MB of something, it probably didn't even get around to installing Grub.[/quote]

I believe you are correct.  However, it has created a 9 MB partition of "FREE SPACE" which, as I understand it, is the purpose of the manual procedure that I utilized.  Is it possible that at this point it thinks it's done?  Every time I rerun the installer and try to point to the existing Ext3 10 GB (by selecting this partition and then tabbing down to the command that ends in "write files as the install destination) in less than a second it just brings me back to the same screen with nothing written.  I believe it attempts to write to the only "FREE SPACE" and stops there for obvious reasons.

 [QUOTE=aysiu]It doesn't exceed 160 GB. In fact, I just did a total, and it totals 153 GB. The second part (67 GB) is for the entire extended partition, which has three logical partitions. If you add up the numbers, you'll see what I mean.  Yeah, it's weird. It sounds as if it just did not install correctly, and it could be something wrong with your CD. Have you verified the disk image?

[http://www.linuxiso.org/viewdoc.php/verifyiso.html](http://www.linuxiso.org/viewdoc.php/verifyiso.html)[/quote]

I'll be happy to burn another ISO image, but you solve the partition chart -- do you really think it's going to come out differently?

 [QUOTE=aysiu]"[D]o any good" as in magically getting Ubuntu installed from its 278 MB? Probably not. You can, however, use the live CD to mount the Ext3 partition and see what folders got installed there--if any--just to see at one point the installation did fail.[/quote]

No, I never engage in magical thinking when in a non-altered state of consciousness.  I am pretty much a scientific method show me a double-blind study kind of guy.  I don't know what I wrote that gave you a contrary perception.  I do know I was tired and frustrated.  I have previously successfully installed cheesy to a dual boot XP machine, but I have never found a Linux distribution that seemed most suitable to my needs and reasonably easy to install alongside Windows XP.  Because of a special situation, I require at least one application (Dragon's speech-recognition) that has not been ported to Linux yet so I do not have the option of utilizing Linux as my sole OS.  (Although, I do understand that IBM has released its source code to ViaVoice to the Linux community and it has been ported to Linux.)

 [QUOTE=aysiu]It does. The first six months (perhaps longer) I used Linux, I had something like this partitioning scheme:

1. XP (NTFS) 13 GB
2. data (FAT32) 100 GB
3. Ubuntu (Ext3) 20 GB
4. Mepis (Ext3) 20 GB
5. whatever-distro-I-was-playing-around-with (Ext3) 7 GB[/QUOTE]

Interestingly, when I enabled my hard drives in Live Ubuntu, I was able to see the filenames and folders in two "public" folders (My Music and My Pictures) that either Windows or I set under Windows sharing as public (Windows Home anemic rights/permissions scheme).  However, Live Ubuntu could not see any of the attributes of the MP3s, for example, including their size, creation dates, etc.  At first, I thought maybe you Ubuntu could read any NTFS file with the correct permissions, but I am doubtful now -- maybe it was getting this information from the MBR -- this is pure speculation of course.

Sorry for this long response.  I have one question.  In Partition Magic is said that if I "deleted" a partition it would delete every other partition on the same "extended" partition which would include all of the data in my now denominated D: partition.  (In other words, all the data in the space outlined in turquoise would be destroyed.)That would be disastrous because I have customize Windows so that documents and settings is on that separate physical drive/partition and have performed many custom installations of applications placing their data and preference files on that partition.  What I'm getting to hear is that the Ubuntu installer does have an option to "delete" the existing 10 GB Ext3.  Would it turn this 10 GB partition into "unallocated space" into "FREE SPACE" like it did with that 9 MB partition on my C: drive without affecting any other partition?  If so, then it seems it should then accept an installation of Ubuntu on to that FREE SPACE partition.  The installer for Ubuntu says in its instructions it will not overwrite an existing Linux installation.  I assume this accounts for its refusal to install Ubuntu over the Lost+Found data on the existing Ext3 Linux partition.  What do you think?

Regards, Gene

PS having just quoted your post, piece by piece, and responding to each section I recognize the time and effort you put into this.  Please accept my thanks for the tenacity and graciousness of your responses.

---

### Post by da5id on 2006-03-30
EUREKA!!!!  Ubuntu installed -- this message brought to you by Ubuntu Firefox.  Now I can ask Ubuntu Linux questions. ;-)

---

### Post by aysiu on 2006-03-30
[QUOTE=da5id]EUREKA!!!!  Ubuntu installed -- this message brought to you by Ubuntu Firefox.  Now I can ask Ubuntu Linux questions. ;-)[/QUOTE] First of all, congratulations! I was getting worried there for a bit.

Secondly... how did you do it? What turned out to be the problem, and how did you fix it?

It may be a good idea to say so just in case someone who has the same problem stumbles upon this thread.

---

### Post by da5id on 2006-03-31
Used all default -- enter, enter, . . .n100 -- reboot 1 -- Eureka.  No offense, Aust. method sux for noobs.  More later, my Win speech recognition down.  Stay subscribed to this thread, please. -- g

---

### Post by aysiu on 2006-03-31
[QUOTE=da5id]Used all default -- enter, enter, . . .n100 -- reboot 1 -- Eureka.[/quote] Great. Glad it worked out. > No offense, Aust. method sux for noobs. No offense, but I've been around these forums quite a while, and I've seen plenty of "noobs" helped more than hurt by Herman's tutorial. It has screenshots and explanations, and I don't think it gets better than that. Did it work for you? No, and I'm sorry about that. But it does help almost everyone else who uses it. > More later, my Win speech recognition down.  Stay subscribed to this thread, please. -- g I'll be looking out.

---

### Post by da5id on 2006-03-31
Point taken re Herman's tutorial. -g

---

### Post by da5id on 2006-04-06
I have successfully installed Ubuntu in a duel boot configuration on a Windows box.  I have successfully enabled my soundcard and sticky keys, the latter of which is essential for me.  I would like to say that it was simply a matter of consulting the specific Ubuntu and/or general Linux documentation available on the WWW.  However, mostly I "mastered" these simple tasks by trial and error, that is, by just pointing and clicking at the various Ubuntu menus, submenus, dialog boxes, etc.  For me, this is a very enjoyable and instructive process -- certainly not tedious or beyond the pale of what I would expect in encountering a brand new OS.  I have a couple of more "issues" to resolve before I can easily dual-boot, i.e., switch back and forth between the operating systems without assistance.  I will be posting my specific questions in separate threads.  This will be my last post in this thread.  Thanks to all who provided gracious substantive and moral support.

---

