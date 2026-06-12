---
title: "Installing ubuntu destroyed my computer"
date: 2007-05-06
forum: Absolute Beginner Talk
---

### Post by the lemming on 2007-05-06
If I hadn't got my hair cut so short last week I would have puule it out by now.

All day I have tried to get my two hard drives ready to install ubuntu.

So far I have tried to install 7.04 twice with disasterous results.  The first time I had a go ubuntu tried to install onto my second hard drive and would not boot up.  However I got this message during boot up.

[ 26.553388] request-module:runaway loop modprobe bunf mt-ffff
[ 26.553388] request-module:runaway loop modprobe bunf mt-ffff
[ 26.553388] request-module:runaway loop modprobe bunf mt-ffff
[ 26.553388] request-module:runaway loop modprobe bunf mt-ffff

when I had another go I got

[16.474249] bla bla bla   


After that I only got a black screen which did nothing.  However I did manage to re-boot into windows XP.

When I tried again I tried to install ubuntu into the master hard drive.  When re-booting I got the following error messages:

[19.989855] bla bla bla

This time my computer was completely fried as I could not boot into any operating system.  However Norton ghost saved the day and I have at least got XP to work.

Surely installing ubuntu as a dual boot should not be so disasterous, should it?

and after another

---

### Post by darkrose on 2007-05-06
Sounds like you have a corrupted disk, did you download it? did you check the md5sum before burning it? did you burn it at the slowest speed possible?

---

### Post by Iceni on 2007-05-06
I can't directly answer your question based on this, could you please provide the following information:

1. Are your hard drives ide or sata?
2. Which one is set as master?

This might help identify the problem. I had similar problems myself and solved them by unplugging all my hard drives except the one I wanted ubuntu on, then reconnect them and add windows. Might be worth looking into. Also remember to validate your cd.

Sorry if this sounds like basic advice, but skill levels are very different here :)

---

### Post by mikewhatever on 2007-05-06
Have you downloaded a Live CD (desktop installer)? If that is the case, you could have run Ubuntu from memory only without installing, just to test it. Have you tried that?
After all, I hope no harm is done neither to your PC, nor to your hair. :)

---

### Post by dptxp on 2007-05-06
Download using torrent.
Burn using InfraRecorder (download it free), use command 'burn image'.

Right File, right burn and right CD.

---

### Post by regomodo on 2007-05-06
i'd have to say a corrupt cd.

It's a thing you soon learn about very quickly.

I learnt about it whilst attempting a Hackintosh osx10.4.6

---

### Post by the lemming on 2007-05-06
Thanks for the quick replies everybody

As far as I know the cd is fine as I did the checksum test on it.  My two hard drives are IDE

And the Live CD works fine.

I am a novice user who learnt how to use ghost before even considering to dual boot Windows VISTA.

I would be greatful for any help or advice.  I don't want to lose XP because it has a few applications that ubuntu does not have yet.

Cheers

---

### Post by oilchangeguy on 2007-05-06
here's what i did. unplug the second drive, install ubuntu on the master drive. then unplug it. plug in the second drive. jumper it as master, install xp. then jumper the drive as slave. plug the master drive back in. when you reboot you should be able to boot to either os.

---

### Post by the lemming on 2007-05-06
> **oilchangeguy said:**
> here's what i did. unplug the second drive, install ubuntu on the master drive. then unplug it. plug in the second drive. jumper it as master, install xp. then jumper the drive as slave. plug the master drive back in. when you reboot you should be able to boot to either os.

  Sorry can't do that.  XP came pre-installed on my hard-drive.

Can XP and ubuntu live on the same hard drive?

---

### Post by jiminycricket on 2007-05-06
Yes, must be different partitions though (...unless you use [Wubi]("http://www.cutlersoftware.com/ubuntusetup/wubi/en-US/index.html"))

---

### Post by oilchangeguy on 2007-05-06
> **the lemming said:**
> Sorry can't do that.  XP came pre-installed on my hard-drive.

Can XP and ubuntu live on the same hard drive?
yes they can.

---

### Post by Happy_Man on 2007-05-06
OH sure, yeah, that's my setup! I'm thinking either a corrupt hard disk, or a corrupt install. Nothing else would throw such bad errors.

---

### Post by the lemming on 2007-05-06
THis is all seriously beginning to annoy me.

So far I have spent in excess of 8 hours today trying to get 7.04 to install.

I have disconnected my second drive, burnt a fresh cd using the slowest speed that NERO will let me.  I have also done a checksum on the image file and everything seems A OK.

When I go through the install procedure I can not choose which partition to put Ubuntu in because I keep getting the error message "No root file system is defined"

I have tried every possible combination of options but to no avail.

This time I tried to install ubuntu completely on the hard drive which was connected to my pc and over write XP but nothing.  It would not even boot up.

Am I exceptionally unlucky?

Should I try the earlier version of ubuntu?

This is all exceptionally frustraiting

---

### Post by Lucifiel on 2007-05-06
Hmmm... I found a thread with a similar issue. Anyone care to tell the poster how to do the technical stuff 'cos I'm not experienced enough? 

[http://ubuntuforums.org/archive/index.php/t-76322.html](http://ubuntuforums.org/archive/index.php/t-76322.html)

---

### Post by ShirishAg75 on 2007-05-06
> **the lemming said:**
> THis is all seriously beginning to annoy me.

So far I have spent in excess of 8 hours today trying to get 7.04 to install.

I have disconnected my second drive, burnt a fresh cd using the slowest speed that NERO will let me.  I have also done a checksum on the image file and everything seems A OK.

When I go through the install procedure I can not choose which partition to put Ubuntu in because I keep getting the error message "No root file system is defined"

I have tried every possible combination of options but to no avail.

This time I tried to install ubuntu completely on the hard drive which was connected to my pc and over write XP but nothing.  It would not even boot up.

Am I exceptionally unlucky?

Should I try the earlier version of ubuntu?

This is all exceptionally frustraiting

 Ok, before we proceed anywhere this is what I would like you to do & if you have done them, please say check  in your reply quoting my message :-

1. Let's say its an 80 GB HDD which has 2-3 partitions let's say 
C:/ , D:/. E:/  then put all the data from E:/ the last partition in C:/ & D:/  and go to Disk Management in Windows & re-format it, this way, things are easier. 

              Alternatively 

1a. If you don't have partitions, use the windows in-built defragmenter to defrag the whole filesystem/hard disk say C:\ & see to it that u have somewhere close to 8-10 GB HDD space free, you could do with less or more, but that should be good enough. Having done that, still make another partition using Disk Management tool so there is D:/

2. Now when you try installing see to it that it points to the empty pre-formatted partition done for it. You need 2 partitions called /  & swap , you can have more or do things later when you are more adept with the situation therein. 

 Another alternative method you could do is use vmware to actually test the installation, and post screenies if & where you are having issues. If u do that, having a screenshot at each stage of the install till where you are having an issue it would become much more easier for us to trouble-shoot. 

 And yes, its an excellent suggestion to take out all the other hdd's except the one on which you want to install ubuntu.

---

### Post by the lemming on 2007-05-06
> **shirishag75 said:**
> Ok, before we proceed anywhere this is what I would like you to do & if you have done them, please say check  in your reply quoting my message :-

1. Let's say its an 80 GB HDD which has 2-3 partitions let's say 
C:/ , D:/. E:/  then put all the data from E:/ the last partition in C:/ & D:/  and go to Disk Management in Windows & re-format it, this way, things are easier. 

              Alternatively 

1a. If you don't have partitions, use the windows in-built defragmenter to defrag the whole filesystem/hard disk say C:\ & see to it that u have somewhere close to 8-10 GB HDD space free, you could do with less or more, but that should be good enough. Having done that, still make another partition using Disk Management tool so there is D:/

2. Now when you try installing see to it that it points to the empty pre-formatted partition done for it. You need 2 partitions called /  & swap , you can have more or do things later when you are more adept with the situation therein. 

 Another alternative method you could do is use vmware to actually test the installation, and post screenies if & where you are having issues. If u do that, having a screenshot at each stage of the install till where you are having an issue it would become much more easier for us to trouble-shoot. 

 And yes, its an excellent suggestion to take out all the other hdd's except the one on which you want to install ubuntu.

Hello

I'm a bit confused by your posting and would appreciate it if you could explaine a bit more.

At the moment I have 2 hard drives and both are 112gb in size.

My master drive is split into three primary partitions:
C: xp operating system     16.5gb
G: empty NTFS partition    10gb    (Hopefully where I want to put ubuntu)
F: empty NTFS partition    85.29gb

My slave hard disk has two primary partitions

D: Ghost Backup of entire master drive          30gb
H: where I store my stuff   jpeg, docs dvd     81.79gb

When I try to install ubuntu 7.04 I try to point the partitioning tool at the 10gb of free space and this is where I get the "no root file system" error

If I try to overwrite the XP partition everything goes fine untill I re-boot the system.  Things start to happen and then it all goes quiet with the "request-module:runaway loop" message.  Should I leave this for quite a few minutes or should things happen almost straight away?

What would happen if :

a:  I put the primary disc back to one partition
b:  Remove the two primary partitions and do not allocate anything to the space that they left behind?

Cheers

---

### Post by the lemming on 2007-05-06
This time I decided to convert my master drive back to one partition.

As normal I ran the 7.04 CD, which was downloaded from a different UK location and burnt as slow as possible.  I chose the recomended option to share disk space and followed all instructions.  Everything went fine untill I was asked to remove the disk and re-boot.

When I re-booted everything seemed to be working untill I got to the  "request-module:runaway loop modprobe binf mt-ffff" message

From there I could have typed anything in the world and nothing happened.

What the hell am I doing wrong?

I must point out that something happened to my Slave drive.  For some reason part of my drive was lefu un-allocated and unformatted.  I wonder why this happened?

---

### Post by ShirishAg75 on 2007-05-06
> **the lemming said:**
> Hello

I'm a bit confused by your posting and would appreciate it if you could explain a bit more.

At the moment I have 2 hard drives and both are 112gb in size.

My master drive is split into three primary partitions:
C: xp operating system     16.5gb
G: empty NTFS partition    10gb    (Hopefully where I want to put ubuntu)
F: empty NTFS partition    85.29gb 

 That's one messy way of having partitions, admittedly XP does that but you can make it behave better. First of all go to disk management & change the drive letters of the slave partitionsto some other letters which are not used for it.  For e.g.  Y:  & Z: Then rename the G: drive/parition  to D: & similarly  F: to E: 

   After doing that, rename the other partitions in the HDD so the sequence is normal. Its also a good idea to label them so you know for e.g. (M01) & something like that so you can recognize them without effort when you have Ubuntu. 
  Now coming to the 10 GB partition in-between that's bad way of doing stuff. A much better, cleaner method would be  the now modified :-

C:/  16.5 GB NTFS
D:/  85.   GB NTFS (data)
E:/ 10 GB free formatted. 

Now for this you would have to push the 85 GB data to the slave hdd format both D:/ & E:/ put back all your data to D:/ & let E:/ remain. 

 After all of this is done, disconnect your secondary/slave hdd & install from CD to  E:/ drive  and you should have an relatively better installation. Accept the defaults where you are not sure apart from making sure that its the 10 GB from E:/ . You could go for manually edit partition table & see that E:/ is formatted only with ext3 & nothing else.  Let's say if you have 10 GB space, make sure to use 9 GB or thereabouts for /  & remaining 1 GB for swap. Swap is like virtual memory the only difference is its in linux. Make sure your swap is double the RAM hence assuming 1 GB.  The rest of the install can be seen at  [https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall) 

> **the lemming said:**
> 
My slave hard disk has two primary partitions

D: Ghost Backup of entire master drive          30gb
H: where I store my stuff   jpeg, docs dvd     81.79gb

When I try to install ubuntu 7.04 I try to point the partitioning tool at the 10gb of free space and this is where I get the "no root file system" error

If I try to overwrite the XP partition everything goes fine untill I re-boot the system.  Things start to happen and then it all goes quiet with the "request-module:runaway loop" message.  Should I leave this for quite a few minutes or should things happen almost straight away?

What would happen if :

a:  I put the primary disc back to one partition
b:  Remove the two primary partitions and do not allocate anything to the space that they left behind?

Cheers

I wouldn't recommend either at this point in time. Make things simple. As you learn how the partitioner logic flows you would be able to do more complex installs or complex configurations. The first goal at this point in time is to have a working system, so concentrate on that. Cheers !

---

### Post by GrueTamer on 2007-05-06
> **the lemming said:**
> My master drive is split into three primary partitions:
C: xp operating system     16.5gb
G: empty NTFS partition    10gb    (Hopefully where I want to put ubuntu)
F: empty NTFS partition    85.29gb

My slave hard disk has two primary partitionsUbuntu can't install to NTFS partitions.  That may be your problem right there.  Try an ext3 filesystem type instead.

---

### Post by the lemming on 2007-05-06
Got some new developments.

I converted my master drive to one partition and then disconnected the slave drive.

Everything went fine.  I clicked and accepted all the recomended options during the install.  While installing I got some new stuff such as 

Installing system
Configuring hardware 94%

It has been at 94% for the last15 minutes now.

The screen has frozen with the clock saying 11:01pm
I have a new icon which says   /target

I feel that I am a step closer but why has my desktop frozen like this?

Have I failed again?

Agggggggggggggg

---

### Post by ChaosNipples on 2007-05-06
Well, I believe that this happens when you try to install Ubuntu on either a Dell, Gateway, Compaq, or HP computer. Companies like them will dis-allow access for Linux since it will tell you all mthe hardware defects that their computers have.

---

### Post by the lemming on 2007-05-06
It may help if I explain that my computer is an Advent product.

Would this make a difference?

Cheers

---

### Post by Happy_Man on 2007-05-06
Don't worry. It's doing something... go make some coffee, watch CNN, just walk away for an hour. It will be fine.

---

### Post by the lemming on 2007-05-06
> **Happy_Man said:**
> Don't worry. It's doing something... go make some coffee, watch CNN, just walk away for an hour. It will be fine.


Opps

I hit the magic blue button and shut the whole thing down.

Having another go.  Should I disconnect my wireless router before I install?

Would this make a difference?

My head hurts.  Wonder if it is anything to do with the Brazilian rum, lime and sugar drink that I'm having right now?

---

### Post by Happy_Man on 2007-05-06
No, disconnecting your router probably won't make a difference; in fact, you may need to manually configure it later, better to just let the system take care of it. And remember, don't force shutdown unless it has been unresponsive for AT LEAST 8 hours. Just my advice.

---

### Post by the lemming on 2007-05-06
I've had enough with 7.04.  I have tried every variation that I can think of so now I'm going for an earlier version of ubuntu.

Could somebody please recomend what I should do with my master drive before I have a go with 6.06?

My tollerance for this is now growing thin

Cheers

---

### Post by the lemming on 2007-05-06
just tried to boot ubuntu in safe mode and my screen has stopped at

root@frank-desktop:~#

anybody know what that means?

I some how managed to get the welcome screen (?) where it asked for my username but I could not type anything or even move the pointer with my mouse.

---

### Post by Drifter on 2007-05-06
Most computers that are sold in stores etc. like gateway etc. put the system cd in a different partition on the drive.  Usually called D.  The drives are formatted in NTFS, ubuntu will not install on NTFS drives.  You stated that you had on the slave drive a 30 gig partition with a ghost of your system on it.  This is what your problem is in my opinion.  Your slave drive needs to be formated with the ubuntu cd or at least the partiontion that you want to use on the slave.  Forget about useing the Master drive because of it being factory fornated with NTFS and a system in a different Partition on that drive.  I would format the entire slave useing it as master and unhooking the one with windows on it.  You can then make the windows drive the master again and the ubuntu one the slave.  This is what I have on mine and it works fine.  Hope this works.

---

### Post by the lemming on 2007-05-06
Don't ask me how but I have made it past the username ad password sections.

However everything has frozen from there.

I can't even move the pointer.

Are things improving?

---

### Post by the lemming on 2007-05-06
I have no idea what I have anaged but I have completed 2 out of three boot-ups into ubunto 7.04

Not got internet access for wireless but that is another task for tomorrow.

I recon 27 hours must be a record.

Well it is in my books anyway.:popcorn: 

Everybody have a drink on me.

Cheers

---

### Post by drowner on 2007-05-06
I am ecstatic you got it working.

I cant believe that over a year ago, as a total n00b, i got it installed 5th time.... and the first 4 problems were me being unable to partition my drives because WinXP had sprayed files all over the HD... and it needed some SERIOUS defragging ;)

Well done.

I will presume, that like me, in 1 years time you wish you just hosed your XP partition :D

---

### Post by Drifter on 2007-05-06
Good work glad you got it going.

---

### Post by dptxp on 2007-05-07
Ubuntu did not destroy your computer. You did.

You simply did not do your homework well before taking the plunge. You did not read the best way to download, and the  best way to burn iso. 

If your CD is correct, and runs well live, you are making mistake in partitioning and choosing the right formats. The / is set for ext3 format, you need min 2 GB there, use min 4 GB. Use 2 GB for swap and make sure that format options are ticked. 

The /target icon is normal.

Once you get through, you will realize that installing Ubuntu is much simpler than Windows. No reboots, no extra CDs for drivers. Take a break as someone has said, start with a fresh mind.

---

### Post by kelvin spratt on 2007-05-07
Don't be to hard most people have never installed a os from scratch they think its like using the recovery disc then say windows is easier to install then try to install Linux and are totally out of there depth most people don't know how to defrag  there hard drive or format and partition or where to put grub they really think its like useing
the restore disc.

---

### Post by the lemming on 2007-05-07
> **dptxp said:**
> Ubuntu did not destroy your computer. You did.

You simply did not do your homework well before taking the plunge. You did not read the best way to download, and the  best way to burn iso. 

Bit harsh wouldn't you say especially when you don't know how much homework I have put into researching this issue?

I have put in a lot of effort reading various web sites, posting questions on this site before even and taking on-board all suggestions before taking the plunge and that is not to say the checksum test that I took on a correctly downloaded iso file.

I may be a novice in the world of linux but at least I had a disaster recovery scenario to get me out of trouble throughout my attempts to install ubuntu.  

With this in mind we can assume that I did some homework and a little preparation.

---

### Post by dptxp on 2007-05-07
Honestly I did not mean to be harsh at all. I just pointed out what I thought were your mistakes. Yes, I admit it sounds a bit harsh.

In fact I have been pursuing the guys here to provide proper and simple documentation so that people do not end up with problems like you have.

I know that it is difficult to collect information from several links, and many information is out dated.

In fact your problem had prompted me to ask the moderators to provide guidance in a sticky thread first before a complete documentation is made so that users are at least able to run live CD and install with minimum time and damage.

check here :
[http://ubuntuforums.org/showthread.php?t=434824](http://ubuntuforums.org/showthread.php?t=434824)

I can understand how upset you must be. You have lost your pre-installed XP too.

OK, I will put a smily on that post.

---

### Post by the lemming on 2007-05-07
> **dptxp said:**
> In fact I have been pursuing the guys here to provide proper and simple documentation so that people do not end up with problems like you have.

I know that it is difficult to collect information from several links, and many information is out dated.

In fact your problem had prompted me to ask the moderators to provide guidance in a sticky thread first before a complete documentation is made so that users are at least able to run live CD and install with minimum time and damage.

check here :
[http://ubuntuforums.org/showthread.php?t=434824](http://ubuntuforums.org/showthread.php?t=434824)

I can understand how upset you must be. You have lost your pre-installed XP too.

OK, I will put a smily on that post.

Hello

I totally agree with you that the whole process is a little complicated if not verging on the esoteric.  I really, really want this whole process to work because I do not want to put Vista back onto my computer because it does not work nearly as well as XP.  Sadly XP will stop being supported in 2009 and I want to be ready.

I do have XP up and running thanks to being able to use Norton Ghost 2003 which clones an entire drive.

If there is anything at all that you can do to help with my exceptionally steep learning curve then I would be nost greatful.

Cheers

---

### Post by dptxp on 2007-05-07
I will tell you for 1 HDD, it should work for 2.

First install XP, if you have a partition fine, else partition with XP, use say 15-20 GB for XP (C-Drive) for Primary. rest for extrended, you can make more partitions, no need to format other partitions now.

In case you have recovered using Norton Ghost, use the 2nd drive for / and swap and partitions. Shall save you a lot of time. You need not defragment.
Or else split the 10 GB to 8 GB for / and 2 GB for swap after you click INSTALL at time of installation.

Next download 2 programs, both FREE. One is Bittorrent. Other is InfraRecorder. Install both in XP.

Next download the corresponding torrent file (about 25-30 kb) from Ubuntu downloads to desktop.

If you got the iso already, set the destination folder in Bittorrent where the iso is.

Click on the torrent file and open with Bittorrent. If your iso is corrupt, only the corrupt files will be replaced. Saves time from downloading full iso using bittorrent.

Once you are sure your iso is correct, open Infrarecorder. Go to Action Menu , click on Burn Image and select your iso file. Your CD will burn in dynamic speed mode at about 20X.

Next boot with CD, carry integrity check just to be sure. Next click on Live/Install.

You got to ensure that you CD is correct. You can get FREE from Ubuntu too, I got mine in 2 weeks.


NOw when you click on Install, choose manual partitioning.

Resize the extended partition for D drive, resize the rest for E drive and so on. One partion has to be marked /, it will be EXT3 and say 4 GB to 8 GB, one for swap and say 1 to 2 GB, others shall be formatted as EXT3 or FAT32 (WIndows has problem with EXT3). Make sure that you format what you want, and do not what you do not want. You can use existing partions, 8 GB for / , 2 GB for SWAP. Ubuntu does not like NTFS, you can set the format as FAT32 so that both OS can read/write.

All partitions have to be mounted, ignore the / and swap, set /media/disk-1, /media/disk-2 (you can use any name for disk-1 or disk-2) for other partitions, the windows one you will see as /media/windows, you may see others as /media/hda3 (you can retain the names and not change them).

Similarly you may see 2nd HDD and partition it, set formats.

The /target menu is normal.

Click on OK, OK after that.

Best of Luck. Get through in less than an hour.

---

### Post by the lemming on 2007-05-07
> **dptxp said:**
> I will tell you for 1 HDD, it should work for 2.

First install XP, if you have a partition fine, else partition with XP, use say 15-20 GB for XP (C-Drive) for Primary. rest for extrended, you can make more partitions, no need to format other partitions now.

In case you have recovered using Norton Ghost, use the 2nd drive for / and swap and partitions. Shall save you a lot of time. You need not defragment.
Or else split the 10 GB to 8 GB for / and 2 GB for swap after you click INSTALL at time of installation.


Hello again

I have done a new checksum on my ISO and used the burning software that you recomended.  I also burned it at the lowest speed possible and ran the disc so that I could perform an integrity check.  Every stage passed.

I am a bit confused about the couple of above paragraphs and was wondering if you could go into a bit more detail because I can't grasp what it is that I am supposed to do.  

I have completely removed 7.04 from my system by cloning a previous version of XP which never had ubuntu installed.  I intend to format my drives with the following setup.  Please let me know if any of this is wrong.

master drive

XP system 20gb NTFS
10 gb ext3
5gb swap file
the rest as FAT 32

Slave drive
30gb partition with cloned image of XP operating system NTFS
the rest FAT 32

does this sound about right?

If so, then I will attempt another install.

Should I disconnect the slve drive when I install?

---

### Post by Happy_Man on 2007-05-07
You don't actually need FAT32, as there are ext3 drivers for windows available @ [http://fs-driver.org](http://fs-driver.org). I would highly suggest taking out the slave when you install; it will save you much problems and you can always stick it back in later.

---

### Post by dptxp on 2007-05-07
With Infrarecorder, you need not set anything, just burn image. You burn fast that way.
Yes, my post got a bit messy after I saw that you got Windows back.

Your scheme seems OK, but 5GB for SWAP seems large. You got space, you may keep.

Make the partition for cloned image of Windows first with Windows. Do not format it while installing Ubuntu and I think you should not mount it too, if Ubuntu allows.

First run CD live. This is first step.

No need to disconnect the slave, it should show in your partition table during installation. Treat it just as another partition. Honestly I have not tried 2 drives, this suggestion is based on what I have read on posts.

Maybe you install Ubuntu on second drive.

Take care of the mounting part.

In case you have to  reinstall again, you do not have to reformat your data partitions, so you can keep your data and use Windows as you play with Ubuntu.

---

### Post by the lemming on 2007-05-07
Hello

Thanks for your help and advice.

After a couple of days of tinkering I think that I have finally solved the problem.  I really appreciate your help and as suggested I burnt a disc using the software you recomended.

I now appear to have a fully working ubuntu and XP.

Cheers

---

### Post by Happy_Man on 2007-05-07
Congratulations and welcome to Ubuntu!

---

### Post by the lemming on 2007-05-07
> **Happy_Man said:**
> I would highly suggest taking out the slave when you install; it will save you much problems and you can always stick it back in later.


May I ask how this will help?

---

### Post by Happy_Man on 2007-05-07
Well, you know, the less partitions you have to worry about, the less problems with "master or SLAVE????" when installing, etc. I dunno, I've never actually had to deal with this. Sorry if my posts seem stupid. :)

---

