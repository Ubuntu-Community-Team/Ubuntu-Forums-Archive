---
title: "HOWTO: Resize your HFS+ partition for free"
date: 2005-11-13
forum: Apple PPC Users
---

### Post by closet geek on 2005-11-13
Just thought I'd share my success.

You may have been pondering buying tools such as iPartition or VolumeWorks to shrink your OS X partition enabling you to install Ubuntu. There is no need to spend your hard earned $$$ as 'parted' can do this for you for free.

Getting started:

You must login to OS X and disable Journaling on your hard drive. To do this, launch Disk Utility, select your drive and click File -> Disable Journaling. It should be noted that I had some issues with this: Disk Utility claimed my file system was Journaled but at the same time wouldn't allow me to disable it. The work around is to launch a shell and type:

```

cd /Volumes/

```

then type:

```

ls

```

this will show you all the Volumes on your computer, make sure you note the name of the Volume you want disable Journaling on. In my case it was called  "Macintosh HD".

Run this command:

```

sudo diskutil enableJournal Macintosh\ HD/

```

of course replacing Macintosh HD with your Volume name. Bear in mind that the above is not a typo, it is supposed to read "enableJournal" even though we are trying to disable Journaling, this is due to a bug (in at least my Tiger install) that labelled the Volume as Journaled when it wasn't. After you have run the above run:

```

sudo diskutil disableJournal Macintosh\ HD/

```

verify that it says Journaling has been disabled.

Now reboot your Mac ensuring you have your Breezy install CD in the CD drive. Just after you computer starts to boot up (e.g. before you even see the grey screen with the Apple on it) make sure you hold down the "c" key. This will make your Mac boot from the Breezy CD.

Follow all of the Breezy install steps up until the partitioner. Instead of clicking "Continue" hit "Go Back" this should take you to a screen with a small list of options. From here you want to select "Go to a Shell".

Once the shell has started type: "parted", from here I can't give you exact instructions as these steps might vary slightly depending on your setup but for me I then typed:

```

print

```

this showed me my list of partitions, locate the partition you want to resize (it should be obvious) and note down the "Minor" number. Then in parted type:

```

resize MINOR_NUMBER_HERE START_BLOCK_SIZE_FROM_PRINT_OUTPUT NEW_END_BLOCK_SIZE

```

I do apologise if this step makes no sense, but it should be clear from the "print" command what I mean by my caps'ed underscored commands. My final resize command ended up looking like this:

```

resize 3 128.032 37237.821

```

at which point I hit enter and was rewarded by a warning message that went something along the lines of:

> 
I have detected an HFS+ system with some strange characteristics, in theory I can still shrink this but it's still experimental, please email me if it all goes wrong

I hit "I" to ignore this message and let parted try and shrink my HFS+ partition. Literally within 2 seconds I was back at a parted prompt. Having experienced how long it takes PartitionMagic to shrink an NTFS partition I was assuming the worse! However hitting the "print" command again showed me parted (at least) thought it had resized my partition successfully.

Hit "q" then type "exit" to return to the installer where you should then return to the partition tool hopefully now with some free space you can install your Breezy on. All worked like a charm for me, I'm now dual booting Tiger and Breezy.

Hope this helps, sorry if I ramble.

cg

---

### Post by ssam on 2005-11-14
glad to see you figured this out. I hope you did a back up before you tried it.

you might want to put this in the [wiki]("https://wiki.ubuntu.com/"). thats the best place for storing howtos. and maybe also post it in the howtos section on the forum, and put a pointer to it in your last post (just so that if anyone searches for iPartition they can find this.)

---

### Post by closet geek on 2005-11-14
[QUOTE=ssam]glad to see you figured this out. I hope you did a back up before you tried it.

you might want to put this in the [wiki]("https://wiki.ubuntu.com/"). thats the best place for storing howtos. and maybe also post it in the howtos section on the forum, and put a pointer to it in your last post (just so that if anyone searches for iPartition they can find this.)[/QUOTE]

All good suggestions!

Andrew

---

### Post by ristosu on 2005-11-15
Nice photo.

That's around 37 GB, your HFS+ partition? May I ask, how much RAM do you have? The reason for asking: I tried to shrink an HFS partition running from liveCD, and received Out of memory error.

---

### Post by Down8ve on 2005-12-22
A few notes to make tris more clea.

 in Dapper, you choose "Execute a shell" instead of "Go to a Shell".

In parted entering "p" is the same as "print".

The numbers you enter at the resize command are Partition number, Start and ther End size you want.  Mine was:

P
NUMBER    START        END         AND SO ON...
10            135MB       40GB          HFS+

So my resize command was:

resize 10 135MB 20GB

which reduced my 40GB Mac OSX partition to 20GB.  It did think about it for a while, probably due to my 333mhz G3.

DS|M

---

### Post by zxee on 2005-12-22
Nice work!  I have sort of the reverse issue I created three different partitions when I installed ubuntu 5.04 on a G3 500Mhz imac.The three partiton sizes and uses are: partition1 5GB OSX, P2 3GB OS9, P3 20GB Ubuntu At some point I may try 5.10 I know however that my scanner is not supported and I never could get acel for the imac video. No complaints though-and I use linux exclusively on my homebuilt sempron. I wonder if someone can point me to a painless way to resize or even eliminate the ubuntu partition and reclaim the space for hfs+ OSX? Or will I need to invest in ipartition? Thanks in advance.
(And sorry if this is the wrong way to post this. The 5.04 PPC forum seems a little unused-and this thread looked like a good bet)

---

### Post by macheadPDX on 2005-12-23
[QUOTE=closet geek]Just thought I'd share my success.

You may have been pondering buying tools such as iPartition or VolumeWorks to shrink your OS X partition enabling you to install Ubuntu. There is no need to spend your hard earned $$$ as 'parted' can do this for you for free.

Getting started:

You must login to OS X and disable Journaling on your hard drive. To do this, launch Disk Utility, select your drive and click File -> Disable Journaling. It should be noted that I had some issues with this: Disk Utility claimed my file system was Journaled but at the same time wouldn't allow me to disable it. The work around is to launch a shell and type:

```

cd /Volumes/

```

then type:

```

ls

```

this will show you all the Volumes on your computer, make sure you note the name of the Volume you want disable Journaling on. In my case it was called  "Macintosh HD".

Run this command:

```

sudo diskutil enableJournal Macintosh\ HD/

```

of course replacing Macintosh HD with your Volume name. Bear in mind that the above is not a typo, it is supposed to read "enableJournal" even though we are trying to disable Journaling, this is due to a bug (in at least my Tiger install) that labelled the Volume as Journaled when it wasn't. After you have run the above run:

```

sudo diskutil disableJournal Macintosh\ HD/

```

verify that it says Journaling has been disabled.

Now reboot your Mac ensuring you have your Breezy install CD in the CD drive. Just after you computer starts to boot up (e.g. before you even see the grey screen with the Apple on it) make sure you hold down the "c" key. This will make your Mac boot from the Breezy CD.

Follow all of the Breezy install steps up until the partitioner. Instead of clicking "Continue" hit "Go Back" this should take you to a screen with a small list of options. From here you want to select "Go to a Shell".

Once the shell has started type: "parted", from here I can't give you exact instructions as these steps might vary slightly depending on your setup but for me I then typed:

```

print

```

this showed me my list of partitions, locate the partition you want to resize (it should be obvious) and note down the "Minor" number. Then in parted type:

```

resize MINOR_NUMBER_HERE START_BLOCK_SIZE_FROM_PRINT_OUTPUT NEW_END_BLOCK_SIZE

```

I do apologise if this step makes no sense, but it should be clear from the "print" command what I mean by my caps'ed underscored commands. My final resize command ended up looking like this:

```

resize 3 128.032 37237.821

```

at which point I hit enter and was rewarded by a warning message that went something along the lines of:



I hit "I" to ignore this message and let parted try and shrink my HFS+ partition. Literally within 2 seconds I was back at a parted prompt. Having experienced how long it takes PartitionMagic to shrink an NTFS partition I was assuming the worse! However hitting the "print" command again showed me parted (at least) thought it had resized my partition successfully.

Hit "q" then type "exit" to return to the installer where you should then return to the partition tool hopefully now with some free space you can install your Breezy on. All worked like a charm for me, I'm now dual booting Tiger and Breezy.

Hope this helps, sorry if I ramble.

cg[/QUOTE]

Hello,

This is an awesome how-to... I just have a couple of questions before I dive in... At what point in this process it is safe to cancel and get back to where you started without hosing OSX?  When you dual boot, how does it look like when you turn-on your Mac? Does it give you a boot menu? 

Sorry, this is all new to me. Any insight is much appreciated.

Thanks a bunch!

---

### Post by elwood_j_blues on 2005-12-23
[QUOTE=macheadPDX]When you dual boot, how does it look like when you turn-on your Mac? Does it give you a boot menu?[/QUOTE]

Exactly.

(Please, never ever full quote again! You should only cite what's important for what you are going to say!)

---

### Post by elwood_j_blues on 2005-12-23
For me, it worked too. Thanks for the howto. You should definitely add it to the wiki.

Anyhow, please mention there that it is a quite dangerous process. It worked for us two but for somebody else, it might just crunch the partition with all the data on it.

Happy holidays!

---

### Post by macheadPDX on 2005-12-23
[QUOTE=elwood_j_blues]Exactly.[/QUOTE]

Sorry, but what did you mean by this?

[QUOTE=elwood_j_blues](Please, never ever full quote again! You should only cite what's important for what you are going to say!)[/QUOTE]

Point taken! Thank you! I'll keep this in mind...

---

### Post by ubuntuben on 2005-12-23
This is an awesome hack. I've been using Breezy 5.10 on an old PC and have been wanting to test drive it on my iBook. DId a full backup of my disk and noted what size I wanted to shrink the partition to. Read and re-read your post to make sure I understood the steps and carefully followed them. It took awhile to shrink the partition, but it worked. I am amazed! This has saved me the pain of reformatting and reinstalling everything from scratch. (Next task is to look into getting a USB wireless dongle to work. Looks like there is no "easy" solution for this.) Thanks for this great hack.

--ubuntuben

Breezy 5.10
Mac OS X 10.3.9
ibook G3 600 MHz dual usb

---

### Post by jdp on 2006-01-24
For future readers who may be confused, this does work on OS 9 as well.  You just get to skip the Journalling steps and you can boot right to the CD and resized the partition.

I did this with an 8500/120 running 9.1 and I had to boot with BootX from the partition I was resizing.  It worked just fine.

[http://ubuntuforums.org/showthread.php?t=119357](http://ubuntuforums.org/showthread.php?t=119357)

---

### Post by spaceballl on 2006-01-30
Just wanted to say that I just used this method, and it worked WITHOUT A HITCH. However, the resizing took a long time. I have an iBook G4 1.25 ghz w/ a gig of RAM and resizing my 80gb hard drive took about an hour. However, it could just be because there's so much data on it and the drive is really fragmented or something. I don't really know... But it worked great, and i'm happily dual booting ubuntu!

-Kevin

---

### Post by manicka on 2006-01-30
[QUOTE=ssam]
you might want to put this in the [wiki]("https://wiki.ubuntu.com/"). thats the best place for storing howtos. and maybe also post it in the howtos section on the forum, and put a pointer to it in your last post (just so that if anyone searches for iPartition they can find this.)[/QUOTE]

This how-to will soon be archived at the  [URL="http://doc.gwos.org"]Forums Archive Facility
[/URL]

---

### Post by compwizz on 2006-01-31
There is something that I am a little unclear about.  When you are resizing the partition, is the "New end block size" the size you want your current partition with OS X on it, or is it the size of the new blank partition that you will be installing Ubuntu on?

Also, will this work using the Kubuntu install disk also?

Sorry, but I am new to Ubuntu and just wanted to clarify a few things.

---

### Post by compwizz on 2006-02-01
I was feeling adventurous and went ahead and tried it on my own.  I am pleased to report that I am typing this running Kubuntu on my dual boot OS X system!!

Now all that is left to do is play around and see what this system can do :D

---

### Post by bennyp on 2006-02-01
May we re-enable journalling on our HFS+ partitions after re-sizing?

---

### Post by compwizz on 2006-02-02
[QUOTE=bennyp]May we re-enable journalling on our HFS+ partitions after re-sizing?[/QUOTE]
I have re-enabled it on my system with no problems at all.  The Journaling only affects the partition that OS X is on, so enabling won't cause any problems with the Ubuntu partition.

---

### Post by Flipper on 2006-02-17
[QUOTE=ristosu]I tried to shrink an HFS partition running from liveCD, and received Out of memory error.[/QUOTE]

I to get the same error :| , i follow all the steps described in here, it starts to resize , and right at the end he just says "out of memory error" and does not complete the resizing process ..

Can anyone help? im using an ibook clamshell 366mhz 192Ram 60GB HDD

ps: im not using the live CD, im using the install CD

---

### Post by lotu5 on 2006-02-21
[QUOTE=closet geek]
```

resize MINOR_NUMBER_HERE START_BLOCK_SIZE_FROM_PRINT_OUTPUT NEW_END_BLOCK_SIZE

```

I do apologise if this step makes no sense, but it should be clear from the "print" command what I mean by my caps'ed underscored commands. My final resize command ended up looking like this:

```

resize 3 128.032 37237.821

```
cg[/QUOTE]


Can you please explain the second number a little better? What was the number printed out by parted? How did you calculare the new end block size? What size is your hard drive?  I'm about to do this, but I'm not sure about the second number. Thank you!

---

### Post by stevieg on 2006-02-26
Thanks for the info.

Worked great for me. No damage to my OS X partition and I now have Ubuntu installed. Thanks you so much.

---

### Post by cRoMo on 2006-03-16
If after rebooting "HFS+ partition error" message appears, you have to change OSX's partition system ID into "af", as it was probably set to "linux", which is wrong. You can do it with fdisk. Don't forget to save changes to partition table under fdisk after doing so.

---

### Post by simone.brunozzi on 2006-03-16
Hi,
I have some questions about this:

1) Why do I have to disable journaling in order to install ubuntu? 

2) Is journaling automatically re-enabled in some way after those operations?

3) Do you suggest to make a complete backup before doing those operations?

4) Do you usually have hardware problems or misdetections using an iBook?

Thanks!

---

### Post by jdp on 2006-03-16
[http://en.wikipedia.org/wiki/Journalling](http://en.wikipedia.org/wiki/Journalling)
A journal keeps a record of changed/unwritten files.  By turnig it off, you can guarantee that all files **should** have been written if it was a clean shutdown.  Thus, when **parted** does it's work, if files are moved they won't disagree with the info in the journal, because the journal is not active.  You will have to turn it back on after re-partitioning, which can be done in Disk Utility.  You shoulnd't need the Terminal to turn it back on.

---

### Post by simone.brunozzi on 2006-03-17
Thanks jdp, it is clear.
For "Disk utility", you mean the one inside Mac OS X of course?

Cheers,

---

### Post by jdp on 2006-03-17
Yes.  There is an icon at the top of the Disk Utility window, it's a green circle with a picture of a HDD and a "glint" star on it.  It'll be ghosted out until you select an OS X partition that doesn't have the ournal on yet.  You should be able to just click ti to turn it back on.  I have no idea if turning it back on will have any effect on your ability to cleanly write files to it from Ubuntu, though.  I'd guess it'd be ok.

---

### Post by itojun on 2006-03-20
Hello, I have tried 5.10 on my iMac G5(with iSight), but it did not boot.  I'll try with 6.04.  wish me luck!

---

### Post by shawnhcorey on 2006-03-21
I have an old PowerBook G4 I want to reconfigure as a dual-boot system. I want a 4GB swap partition and a 6GB Ubuntu/application one. Do I use your technique to create one 10GB partition and reconfigure it later in the install process or create the two using **parted**?

Thanks,

sc

---

### Post by jdp on 2006-03-21
By swap partition, do you mean the virtual memory swap partition, or do you want a 4GB partition to use to get files between Ubuntu and Mac OS?  If it's the latter, then just make your 4GB partition to share files, and let the installer configure the remaining 6GB as needed.  If it's the former, I'm sure you'll have many of us wondering what the heck you would do with 4GB of swap space on an "old" PB G4. ;)

---

### Post by shawnhcorey on 2006-03-21
I think I need a 4GB partition for swap because I read in the *Ubuntu Installation Guide* that's on my install disk, the minimum swap size should be 2GB, and I want to install a Developer's system. Hence, honking big swap. I'm one of those who gets the error, 'fork failed, exceeded quota' and sends the load (see `man uptime`) into triple digits during login.

However, my plans are not fixed, so any suggestions will be appreciated.

sc

---

### Post by jdp on 2006-03-22
There's [https://wiki.ubuntu.com/Installation/PowerPC](https://wiki.ubuntu.com/Installation/PowerPC) that doesn't say much of swap sapce.

Then, there's [https://wiki.ubuntu.com/LiveCDCustomizationHowTo](https://wiki.ubuntu.com/LiveCDCustomizationHowTo) which wold only apply if you are going to custom build your own LiveCDs.

For general software dev, you shouldn't need more than double you physical RAM, up to about 1GB or so.  Others might chime in, but with 640MB in my iBook, I rarely touch the swap in general use.

---

### Post by shawnhcorey on 2006-03-23
Oops.

After re-reading the documentation I realize I made serious mistake. On the Install CD, in the file /doc/install/manual/en/apbs03.html it says, "On 32-bit architectures (i386, m68k, 32-bit SPARC, and PowerPC), the maximum size of a swap partition is 2GB."

I thought it said, "... minumum size of a swap partition is 2GB." Oops. Now a swap of 1GB makes sense.

Thanks jdp for your patience.

sc

---

### Post by plush on 2006-03-31
Followed your instructions and POW, it all worked perfect.  +props

---

### Post by n00bWillingToLearn on 2006-04-07
I would just like to thank closet geek because not being able to resize my HFS+ partition was the one thing that kept me from useing linux for years. All went perfectly and from the dapper install cd there isn't even a warning about HFS+ resizeing being expiremental.

---

### Post by Matthewb57 on 2006-04-10
Thanks a lot guys!  With the help of some other sources to get my video to display nicer during install, the OldWorldMac wiki ([https://wiki.ubuntu.com/Installation/OldWorldMacs)](https://wiki.ubuntu.com/Installation/OldWorldMacs)), and parts of this how-to, I was able to resize my Mac OS 8.6 partition, and install Kubuntu on the remaining free space.

I had been searching for a couple days on how to get this accomplished because I have a couple slight problems that most of you don't have...and that is that I don't have any copies of Mac OS to boot and install from, and my computer is an "Old world" Mac (requires Mac OS + BootX).

Anyways, I just want to thank the creators of this thread for all your help.

Now my mac is no longer useless...

---

### Post by spencer on 2006-04-11
Just wanted to check in and Thank Closet Geek for this great HOWTO. I followed the steps given last night and all went well on another Pismo I have running Tiger. :D  Thank you!

-spencer

---

### Post by namluc on 2006-04-16
I've been trying out the technique outlined in this thread. But have come stuck in the breezy install. Everything has worked fine so far. I went to execute a shell not go to a shell as there wasn't this option i figured they all meant the same thing. 

Here is the big bad wolf.......


[QUOTE=closet geek]
Once the shell has started type: "parted", from here I can't give you exact instructions as these steps might vary slightly depending on your setup but for me I then typed:

```

print

```[/quote]

I got this far however the message I received from typing this was ```
not found
```
not what has been listed below
> 
this showed me my list of partitions, locate the partition you want to resize (it should be obvious) and note down the "Minor" number. Then in parted type:

```

resize MINOR_NUMBER_HERE START_BLOCK_SIZE_FROM_PRINT_OUTPUT NEW_END_BLOCK_SIZE

```

I do apologise if this step makes no sense, but it should be clear from the "print" command what I mean by my caps'ed underscored commands. My final resize command ended up looking like this:

```

resize 3 128.032 37237.821

```

 could somebody also explain what these numbers mean. I currently have a 40 gb hd with no partition


All help appreciated in my first time under the hood:mrgreen:

---

### Post by namluc on 2006-04-16
may have sorted it meself

---

### Post by jdp on 2006-04-18
The answer there would be, if your drive has no partitions then there is nothing to resize. ;)

---

### Post by megabenman on 2006-04-23
I have 2 questons:
1.Nobody has answered what the 2nd number is in the final parted command. What is it?

2. So... if I reduce my massive 230+ GB OS X partition down to 200 GB, it give me 30 GB of free space to install ubuntu on? If I want, can I increase/decrease the partition later without any damage?

---

### Post by gingerbread_man on 2006-04-24
hey... thanks so much for the info! I've been looking everywhere for a resource to get my mac dual booting with linux. 
please bear with me though, I have a few questions. :) 
I'm running tiger on a powerbook g4 with 2 equally split partitions on a 60 gig hard drive.

Tiger is installed on the first partition and I want to install linux on the 2nd.
I've read that kernel 2.6 has some support for HFS+ partitions. is it possible for me to use some kind of boot time parameters on the install CD to allow me to use my second HFS+ partition as my root partition?

if not... say i do take the resize route and make room for linux. What happens with the bootloader? Is it apple's own bootloader that decides which OS to boot into? i.e. i can pick using System preferences or will it be a linux boot loader (lilo/grub)?
If it is a linux bootloader is there a way for me to restore the OS X bootloader?

on my home pc, when i wanted to completely restore the windows boot loader i used to just fire up the recovery console and type 'fixmbr'. this made windows rewrite the boot sector. so i guess im asking if you know of an OS X equivalent. or do i have to reinstall OS X to get back the apple bootloader?

thanks so much!

---

### Post by gingerbread_man on 2006-04-24
[QUOTE=megabenman]
2. So... if I reduce my massive 230+ GB OS X partition down to 200 GB, it give me 30 GB of free space to install ubuntu on? If I want, can I increase/decrease the partition later without any damage?[/QUOTE]

I don't see why not. the tutorial above is about reducing the size of your partition in OS X. all you would need to do is follow the exact same instructions and then increase the size of your partition instead of decreasing it.

about the data loss, i doubt anything can be guaranteed but if nothing happened to your data during the 'downsizing' it should work fine the other way around too. but whatever you do... it goes without saying to always backup your important data. even commercial apps screw up.... parted is generally very reliable, but why take a chance.

---

### Post by jdp on 2006-04-24
[QUOTE=megabenman]I have 2 questons:
1.Nobody has answered what the 2nd number is in the final parted command. What is it?[/quote]

> resize MINOR_NUMBER_HERE START_BLOCK_SIZE_FROM_PRINT_OUTPUT NEW_END_BLOCK_SIZE

You type the **resize** command, then the partition number, then the starting block of the partition from the first printout, and the new ending block location.  The difference between the starting block and the ending block is size the partition will end up as.  This should work to move the start of a partition "up" to make room at the beggining of a drive.  I haven't tried it, but that's my theory. :)  You don't always have to resize a partition from the end of it.

---

### Post by megabenman on 2006-04-25
Oh, I see, thanks. But, if I wanted to do it easier, I could just keep the 2nd number as it appears in parted, without having to change it? As long as I change the 3rd number, right?

---

### Post by Goemon4 on 2006-04-28
i want to give this a shot, but i have 1 question, how do i find out info about my hfs partion

---

### Post by hotani on 2006-04-29
Just to clear things up (maybe), here's what the numbers mean:

1st number: the partition we're resizing
2nd number: where it starts
3rd number: its new end point

Take a look at this screenshot:
[img]http://static.flickr.com/49/137236270_a7a16b2013_o.jpg[/img]

Another way to think of the 3rd number (since that is the only one you have to figure out) is [End number - new Ubuntu partition size]. So in the pic I took away 20GB from the 300 for Ubuntu, and my final command was:

resize 3 134 280000

where 3 is "Number", 134 is "Start" and 280000 is "End - 20GB"

Now that I got that out of the way.... I've been trying to install ubuntu ALL FRAKKIN DAY and it's just not working out. I partitioned (it happens to be a secondary drive, not my primary), but then the installer was taking a reeeeeally long time "retrieving files" - like a couple of hours. Then guess what? It errored out. I've seen this happen enough times to know it can't be good. A couple of times it meant my whole drive was trashed, once it meant just repeating the install, but at 2-3 hours for a *possible* install I wasn't interested in doing that.

I tried the Live CD, but no go. It gets past the partition part then hangs (not the kind of behavior you expect from an installer really). If I quit it, it won't start again. Kill the process, start it up, then it hangs when scanning the partitions. So I appear to be stuck. I'll try the install disk again tonight but I'm not very hopeful.

---

### Post by gingerbread_man on 2006-04-29
hey,
maybe you want to check your partition table? could have got hosed with the resizing.

---

### Post by hotani on 2006-04-30
Actually to my surprise it's all there and intact. When I boot up in OS X I can see the drive fine, and even the swap and root partitions created by the installer. I'm about to go give it another shot so hopefully it'll blast through this time.

EDIT: Well, that was [NOT] fun. I tried installing again and was met by errors right and left. Of course the system did NOT install, and on many of the errors the options were "Go Back" or "Continue" - from what I can tell, they both do exactly the same thing. Neither lets you do a "get me the frak out of here because this install is so hosed."

On a lighter note - the installer was running normal speed. What took 3 hours this afternoon was a couple of minutes this time around. 

So far, my track record with Ubuntu has not been too good. It is making me appreciate OS X more and more every day. Especially the installation. Wow.

---

### Post by megabenman on 2006-04-30
hotani, is the command messured in KB, MB, or GB?

---

### Post by hotani on 2006-04-30
the resize command uses MB. So for 280GB I had to put 280000 in the example above.

I'm attempting yet another install now and it has just finished the base system  with no errors so my fingers are crossed....

---

### Post by Giles on 2006-04-30
I didn't really understand. I printed out the instructions and followed them. By the time I studied my partition table it became obvious what the command was. I am sure the drive resized in less thn 1 second.

I now have Ubuntu on a 10GB Partition and Tiger on the other 139GB.

The problem is, I am an iMac G% user and I am now stalled by the keyboard/mouse freezing issue. rrr

---

### Post by megabenman on 2006-04-30
Ok I get it now, thanks. Now onto another problem.
Breezy doesn't control the iMac G5's fans so I'm going to use dapper drake instead. Wheather I have to disable the sound thing, I don't know. I'll worry about that later lol. My question is, does the dapper drake flight 6 install disk contain parted? If it doesn't, can I use the breezy install disk, resize with parted, eject, and install with the dapper drake install CD?

---

### Post by hotani on 2006-04-30
I used the dapper 6.06 beta 2 disk and it worked (eventually).

---

### Post by megabenman on 2006-04-30
Which one is beta 2? Flight 2?

And what is the "eventually" part... did you have to do extra stuff to get it to work?

---

### Post by hotani on 2006-04-30
Beta 2 is [the latest dapper release](http://releases.ubuntu.com/6.06/). I had issues because something was wonky with my drive partitions, possibly because the install disk I was using was bad. After I burned a new one the system installed fine. So you should be ok. Seems that most of the people in this thread have not had any problems. 

The Live CD did NOT work - the installer [crashed](http://static.flickr.com/46/137820004_cc98c9b256_o.png) every time I tried to install with it after using the install disk to run the 'parted' trick.

---

### Post by megabenman on 2006-05-01
Thanks! Looks like I might have linux running after all!

---

### Post by _sickboy_ on 2006-05-03
Question: does the PPC 5.10 LiveCD have parted on it?

As much as Ubuntu would be great, I'm looking to simply free up space so I can install another distro (which doesn't have support for resizing HFS+ partitions on it's live/boot CD's).

And could this possibly be done with qtparted? I'm a CLI wuss...

---

### Post by amalagaura on 2006-05-06
I have a correction.  This entire thread is for SHRINKING a partition.  Is there anyway to INCREASE a HFS+ partition?  The parted program in 5.10 release only allows shrinking.  Can anyone help for increasing???

Thanks,
AGD

---

### Post by jdp on 2006-05-10
[QUOTE=jdp]You type the **resize** command, then the partition number, then the starting block of the partition from the first printout, and the new ending block location.  The difference between the starting block and the ending block is size the partition will end up as.  This should work to move the start of a partition "up" to make room at the beggining of a drive.  I haven't tried it, but that's my theory. :)  You don't always have to resize a partition from the end of it.[/QUOTE]


It seems I was wrong.  I tried moving "up" the start of the HFS+ partition on a fresh G3MT and it didn't do a durn thing.  I tried moving the start up 5Mb to leave space for a small boot partition, bit it just left it where it started at.  It went great to size the 4.5GB parition down to 2.3ish GB, and leave 2ish GB for Ubuntu.  The problem I had is that that wasn't enough space for the full standard install, after the swap was taken from that 2GB.  I'll size the HFS+ down a tad more and get it reinstalled.  Then, it's testing to see what quik is all about.  The one problem I see with quik is that it wants to be installed from Linux, or if you try the Mac OS install that is floating around, it wants Linux partitions already installed.  That means that you have to install and setup BootX anyway, so that you can boot the Ubuntu CD and run parted to resize the HFS partiton.  So, what would be the point of quik if it need BootX and a copy of MacOS already installed to even try it?  Chickens and eggs, it seems. :D

---

### Post by acorn22 on 2006-05-29
[QUOTE=closet geek]
Once the shell has started type: "parted", from here I can't give you exact instructions as these steps might vary slightly depending on your setup but for me I then typed:

```

print

```

this showed me my list of partitions, locate the partition you want to resize (it should be obvious) and note down the "Minor" number. Then in parted type:

```

resize MINOR_NUMBER_HERE START_BLOCK_SIZE_FROM_PRINT_OUTPUT NEW_END_BLOCK_SIZE

```

I do apologise if this step makes no sense, but it should be clear from the "print" command what I mean by my caps'ed underscored commands. My final resize command ended up looking like this:

```

resize 3 128.032 37237.821

```
[/QUOTE]


I downloaded the livecd by mistake so I have to wait to actualy try this. But just so i got it right, I will just copy "minor number" whch i wil see when i type "print". Then Just copy the other two from that output as well? It would be nice if someone posted the exact output they got (along with the size of their hd) So i can get a frame of refecence.

Basicaly i'm wondering if it is really self-explanitory when you see it.

Btw, Does this work to make a partition bigger? (after i delete another one)

---

### Post by n00bWillingToLearn on 2006-06-04
I don't know if it is polite to double post as I have alredy asked this here
[http://www.ubuntuforums.org/showthread.php?t=188750](http://www.ubuntuforums.org/showthread.php?t=188750)
but why can parted resize HFS+ but gparted can't?

---

### Post by pepijn on 2006-06-07
I got it working pretty simple after a while. Just started the terminal manually, then typed 'sudo parted'. And it showed up with the Macintosh HD. Worked fine after that. Although os x had some problems.

Thanx for the reply! (mounting trick worked.)

--------------

I'm trying to resize the mac harddisc in order to install Ubuntu 6.06 but I experience some problems.

After I boot the live cd and start the 'install app' I don't get the option to go to the terminal. If I start terminal over applications -> accessories -> terminal, parted won't recognise the mac hd. All it shows is the ubuntu (live) partition (734 mb) and a very little one from apple (1 kb).

In the File Browser though, I see the Mac HD but when i try to mount it it gives an error:  *error: device /dev/hda9 is not removable*
and:    *error: could not execute pmount*

Also i'm able to see all the partitions using the installer, but it is not able to resize although i've 8 gb of free space.

Can someone please help me out?? (i'm just getting started with linux...

----------------

System specs: powerbook G4, 500 Mhz, 512 mb ram, 20 gb hd.

---

### Post by n00bWillingToLearn on 2006-06-07
[QUOTE=pepijn]I'm trying to resize the mac harddisc in order to install Ubuntu 6.06 but I experience some problems.

After I boot the live cd and start the 'install app' I don't get the option to go to the terminal. If I start terminal over applications -> accessories -> terminal, parted won't recognise the mac hd. All it shows is the ubuntu (live) partition (734 mb) and a very little one from apple (1 kb).

In the File Browser though, I see the Mac HD but when i try to mount it it gives an error:  *error: device /dev/hda9 is not removable*
and:    *error: could not execute pmount*

Also i'm able to see all the partitions using the installer, but it is not able to resize although i've 8 gb of free space.

Can someone please help me out?? (i'm just getting started with linux...

----------------

System specs: powerbook G4, 500 Mhz, 512 mb ram, 20 gb hd.[/QUOTE]
For me Ubuntu thinks my HFS+ partition is EXT3 so it get's an error when I try to mount it through gnome but you can tell it to mount as HFS+ explicitly though the command line. Try:

```
 sudo mkdir /media/macdisk 
```

then

```
 sudo mount -t hfsplus /dev/hda9 /media/macdisk 
```

---

### Post by zachws on 2006-06-22
im on the live cd right now. im incredibly frustrated because i cant find this mysterious back area with a list of commands including go to shell. i want to install ubuntu so badly.

does this hack still work now that 6.06 dapper is out???

please help. if youve ever had that verge of punching window phenomenon before.
thanks

zach

---

### Post by zachws on 2006-06-22
well i finally got to the terminal. this is why no one uses linux. its a great idea. but jesus its stupidly complex. parted no longer works in 6.06. it tells me the drive is read only. awesome. great product here. oh yea and thanks for all the help.

---

### Post by iAlexander on 2006-07-01
Hey! running an iMac G5 (iSight) and wanted to install ubuntu. I've got the dvd and a 160GB HD (actually 152GB) if I want to leave 5ishGB for Ubuntu what would I type in parted (the nubers that aren't shown from print). Also can I install from the dvd? Thanks. P.S having problems loading from the live CD.

---

### Post by iAlexander on 2006-07-01
Just ran the installer for the DVD and got to the parted stage all went well then this came up.[IMG]http://img434.imageshack.us/img434/4308/screen3rh.jpg[/IMG] I pressed "no" then another window came and asked something like "write these changes" and "Undo these changes" well I un did them but I still lost 4GB of space in OS X. Should I have pressed "Yes"? Thanks. P.S Click image to enlarge (alot!) P.P.S I chose the option to install to largest amount of free space. P.P.P.S I'm a COMPLETE Linux newbie.

---

### Post by Digitallysick on 2006-07-03
i was confused myself, basicly follow the steps to turn off journaling, then starup dapper disk, when you get to the partition screen, open up terminal, and type sudo parted

this will show your mac HD mine is 100gb, i wanted to use about 10 for linux, so i typed

resize 3 134.00 90000.00

hopefully gave me 10 gb, will follow up

---

### Post by n00bWillingToLearn on 2006-07-04
I havn't read all the posts on this thread so I don't know if this has already been brought up, sorry if it has. Although gparted ( which comes with the dapper 'desktop' / live / install CD ) will not let you resize HFS+ partitions ( it should because it is just a front end for parted ) there is another program, qtparted, which is another graphical front end for parted, which does let you edit HFS+ partitions. I have not found any liveCD's for PPC that come with qtparted but if anyone is interested in a graphical way to resize thier HFS+ partition I could make one and host the iso. If anyone is intersted just reply to this post and I will get to creating the liveCD and post it in this thread. I agree that new users should learn to use the command line but not when they are trying to do something as dangerous as resizing partitions, also, if it were not for this thread I would not be a linux user today but the lack of a more user friendly solution almost kept me away.

---

### Post by meshica7 on 2006-07-09
nOObWilling To Learn,

I am willing to give this a try!

I have a few questions so forgive me if I appear to be a bit "needy":confused: .

 I do **not** have enough room on the main drive that houses OS X on my G4 so I want to use one of my other drives instead (The drive in question houses OS 9 and a TON of Pro Tools files).Is this possible? If so,how would I reboot in OS X from Ubuntu?I know that I can boot up in Ubuntu using my System Prefs.Does Ubuntu have a similiar option/application?
 So,will QTParted work for my scenario and is your offer still good?
You're right.Most of use newbiews are a bit shy when it comes to the term.I do have my copys of O'Reilly's Learning Unix for Mac and Sam's Teach Yourself Unix!
Thanx in advance!
 Juan R/ Leõn

---

### Post by n00bWillingToLearn on 2006-07-09
> **meshica7 said:**
> nOObWilling To Learn,

I am willing to give this a try!

I have a few questions so forgive me if I appear to be a bit "needy":confused: .

 I do **not** have enough room on the main drive that houses OS X on my G4 so I want to use one of my other drives instead (The drive in question houses OS 9 and a TON of Pro Tools files).Is this possible? If so,how would I reboot in OS X from Ubuntu?I know that I can boot up in Ubuntu using my System Prefs.Does Ubuntu have a similiar option/application?
 So,will QTParted work for my scenario and is your offer still good?
You're right.Most of use newbiews are a bit shy when it comes to the term.I do have my copys of O'Reilly's Learning Unix for Mac and Sam's Teach Yourself Unix!
Thanx in advance!
 Juan R/ Leõn
I am sorry to say that installing Ubuntu on an external drive is far from simple and requires much more terminal use than this guide and deals with things that are in some ways more dangerous than repartitioning.  To do it requires editing things in open firmware ( what BIOS is to 'windows' machines exept much smarter ) I have found a guide for doing it here: [http://macubuntu.blogspot.com/2005/11/nailed-howto-install-bootable-mac.html](http://macubuntu.blogspot.com/2005/11/nailed-howto-install-bootable-mac.html).
I believe, however, that yellowdog linux has an option to install onto an external firewire drive by default, and although I cannot say how easy it is to use or install ( I have not done either ) it will almost definately be safer and easier to install yellowdog than Ubuntu if you must install it to an external drive. Yet another option would be to move your OSx installation to the external drive using a mac utility called carbon copy cloner [http://www.bombich.com/software/ccc.html](http://www.bombich.com/software/ccc.html) and then install Ubuntu on your internal drive. And while looking at yellowdog it also seems to be able to graphically resize HFS+ partitions so I guess my advice to you would be to grab a yellowdog liveCD and use it to resize any partitions and if you still want to install to an external drive than try installing yellowdog also?

Again, I have no experience with yellowdog, and I am not trying to turn anyone away from Ubuntu, but you may find it suites your needs. I am still willing to help you try to install Ubuntu on an external drive or answer any other questions you may have. As for how you would choose to boot from Ubuntu or OSx, there is no startup disk utility for linux like there is in OSx, instead you can either set it to ask you which you want to boot into each time you boot, or set one as the default and hold down the option key at boot time to choose another disk to boot from. (BTW sorry for the long reply) :)

---

### Post by meshica7 on 2006-07-10
Thanx for the info!
Don't worry 'bout the long reply.That just indicates to me that you took time to think about what you wanted to relay.I appreciate that sort of consideration. :)
I did fail to mention that the drive that I am wanting to install Ubuntu onto is **not** an external drive.I have 4 internal drives (none are Firewire). The drive currently has OS 9 on it.Does this make a differance?
I appreciate you time and patience.I will also check into Yellowdog just in case.
Juan

---

### Post by n00bWillingToLearn on 2006-07-11
> **meshica7 said:**
> Thanx for the info!
Don't worry 'bout the long reply.That just indicates to me that you took time to think about what you wanted to relay.I appreciate that sort of consideration. :)
I did fail to mention that the drive that I am wanting to install Ubuntu onto is **not** an external drive.I have 4 internal drives (none are Firewire). The drive currently has OS 9 on it.Does this make a differance?
I appreciate you time and patience.I will also check into Yellowdog just in case.
Juan
I don't think that having OS 9 on it should make any difference but I have never tried a dual boot with OS 9 and Ubuntu. I will try to make the CD tonight, instead of just making it a small iso with the bare minimum to run qtparted ( since you can probably just use the yellow dog CD to resize your partition ) I have decided to try to remaster the 'Desktop' CD ( live / install CD for Ubuntu ) and just add qtparted so you would be able to resize and install from the same CD ( I don't know why the Ubuntu devs DIDN'T do this... ). My only problem is that I don't have room on my googlepage for the full desktop iso so if anyone could host it for me or point me to a good free hosting solution for large files that would be great.

---

### Post by meshica7 on 2006-07-11
:KS noobWTL

Here's a great,free,host site.I use it to archive my podcasts.

[Internet Archive]("http://www.archive.org/index.php").

Click the "Contributions" link at the top of the page to sign up (free,of course). If ya need any help,let me know.
Thanx again!
 Juan

---

### Post by n00bWillingToLearn on 2006-07-12
Thanks for the link and sorry for the delay. I found out that the newest version of gparted DOES support HFS+, but it isn't in the Ubuntu repos yet. I am trying to find a way to install the debian version ( which has been ubdated ) but it is turning out to be harder than I thought. If you want the CD sooner I can just do what I was planning before and install qtparted, but since the Ubuntu installer is built around gparted, updating gparted is a better permanent solution ( once I figure out how to do it ) and I plan on making a new thread if I end up finding out how to update gparted as that would mean that people could install completely through the standard installer ( which is the easiest installer I have ever seen ).

---

### Post by meshica7 on 2006-07-12
nooB

 Here is where I stand so far...

 Today I decided to move TONS of files from my 10 gig HD to my 80 gig HD which had been partitioned for OS X (at 60 gigs)and file storage (at 20 gigs).I then wiped out any remaining and useless files from the 10 gig HD.So,now I have an extra internal HD with 10 gigs of free space waiting for Ubuntu.Should be pretty straight forward now,right?

 Well....

 I went to install Ubuntu and when I got to the actual install portion of the process, QParted launched.How do I proceed from here? Is QParted even necessary at this point with a whole HD dedicated for Ubuntu?What option should I choose at this point?

 Sorry if I seem to ramble here.I just want to make sure that I do not wipe out my OS X system![-(  
 If this can save you from having to set up the ISO I figure that would be a big wieght off your shoulders as well.pf course,your efforts will benefit may rookies and timid folk (like me).
 Being new to the world of Linux,I am probably asking a simple question here:Does Linux need a partitioned HD to run on or is QParted intended for those situations where only a single HD is available?
 Man,I really appreciate your time here.Seems that the Ubuntu community is a friendly and most helpful group of people.Id only folks could be this willing to aid in all aspects of life!
 
:mrgreen: 

Juan

---

### Post by meshica7 on 2006-07-12
nooB

 I got as far as step 6 in the installer.This is my last chance to check things over and all looks good.The drive I have targeted is 100 percent free for the taking,my OS X System and files are all on a seperate HD,and I feel pretty good about it.

 Now, before I take the final plunge into dual boot bliss,I have a couple of questions...(of course :-k )

 1. I can pretty much guess that I will be using the Start-Up Disc option in Preferences while in OS X to choose Ubuntu for my next start up.How do I get back to OS X from Ubuntu?I know that holding the "C" key during booting presents me with an option for a start up disc and the Ubuntu Installer says that I will be presented a choice at start up for a prefered OS as well,but is there a way to do this within Ubuntu like there is in OS X?

 2. Can I still use free space on the Ubuntu drive to store OS X files or should I leave this drive strictly to Ubuntu?

 3.Why am I so nervous about this?](*,) 

 Well, I will await your input before proceeding.Until then I will continue to hunt the forums for more info.

Thanx again for your help!

 Juan

---

### Post by n00bWillingToLearn on 2006-07-13
> **meshica7 said:**
> nooB

 I got as far as step 6 in the installer.This is my last chance to check things over and all looks good.The drive I have targeted is 100 percent free for the taking,my OS X System and files are all on a seperate HD,and I feel pretty good about it.

 Now, before I take the final plunge into dual boot bliss,I have a couple of questions...(of course :-k )

 1. I can pretty much guess that I will be using the Start-Up Disc option in Preferences while in OS X to choose Ubuntu for my next start up.How do I get back to OS X from Ubuntu?I know that holding the "C" key during booting presents me with an option for a start up disc and the Ubuntu Installer says that I will be presented a choice at start up for a prefered OS as well,but is there a way to do this within Ubuntu like there is in OS X?

 2. Can I still use free space on the Ubuntu drive to store OS X files or should I leave this drive strictly to Ubuntu?

 3.Why am I so nervous about this?](*,) 

 Well, I will await your input before proceeding.Until then I will continue to hunt the forums for more info.

Thanx again for your help!

 Juan

Ubuntu does not have a startup disk like application like OS x does. This is what the default installer did on my machine, but I only have one drive with multiple partitions so it may be different with multile physical drives. When I boot, I get a prompt asking me what system I would like to boot into. I type L to boot into Linux, X to boot into OS x, and C to boot from CD ( I don't have OS9 installed so I don't know what you would type for that but it will have a list of choices ). If I just wait ~10 seconds it automatically boots into Linux. So you actually wouldn't even be using Apples boot disk preferences and, in fact, Apples boot disk utility Only recognises Apples Operating Systems so you can't use it to choose to boot Ubuntu. Furthermore this boot strap is actually a very small partition on the drive and so if you use set your computer to boot directly into OSx then you will not longer get the prompt to boot Ubuntu when you start up, and you won't be able to use OSx to change back to the bootstrap partitio although that can easily be fixed and there is also a built in option on macs ( that is very cool IMHO ) that if you hold down option while booting it will detect all bootable drives and partitions ( including Linux partitions, and removable firewire drives! ) Show thier icons on the screen ( linux partitions have a tiny tux penguin in the bottom left :) ) and let you use your mouse to select one and boot from it ( this is one of the many reasons I said that Apples open firware is like PC's BIOS but much smarter ) The only reason why you would want to use Yaboot instead of this option is that it usually takes 30+ seconds to find all your drives wheras Yaboot just looks for them when you install it, and remembers what you have so it only takes ~5 seconds to load. So basically the easiest way to go is just to let Ubuntu configure everything, choose your boot disk when you boot, and don't worry about Apples utility because you no longer need it :) Again sorry for the long, run-on, reply:)

[edit] To answer your second question, there are drivers to let OSx use EXT3 partitions ( what Ubuntu uses by default ) but they don't work for Tiger ( they do work in 10.0 - 10.3 though ). Likewise, there are drivers that let Ubuntu use HFS+ partitions but currently it is only safe to mount them as read only. You could make a fat32 partition for sharing between OSx and Ubuntu though if you want to.

---

### Post by meshica7 on 2006-07-13
nooB,

 Thanx again for the helpful info.That clears up a lot.
FYI: I removed OS 9 (it was on the drive I want to install Ubunto on).It has become obsolete to me and I got rid of all my OS 9 apps anyway :p .
 So I guess all I need to do now is take the plunge.I will let ya know how it goes....wish me luck!:mrgreen: 

Juan

---

### Post by meshica7 on 2006-07-13
nooB,
 A round of applause to you my friend! I am now a dual-boot fool.A roaring success as I have now installed Ubuntu 6.06 onto my 10 Gig Maxtar HD.And,just as you mentioned,I am able to select my OS at the start up prompt.No probleams so far.
 Now,how picky is Ubuntu with Apple's Airport Extreme? i wanted to configure my ubuntu system for internet access but I do not know where to do this.
 Thanx again for all your help.When I get my new Mac,I believe the Ubuntu HD will go back into it's old case ( A Quadra 800.Ah the days of beige towers!),the G4 will be relegated to a rack along with my Digi 001,a QSC CX502 power amp,and a Behringer Pro Bass V-Amp so I can use Pro-Tools for my effects processing (I'm a musician,could ya tell?:D ).I'll use the new Mac for everything else.So you can see why I want to have internet usage on the Ubuntu system.Heck,I may go all Ubuntu if I find some great pro-recording software.
 Take care,

 Juan

---

### Post by n00bWillingToLearn on 2006-07-14
> **meshica7 said:**
> nooB,
 A round of applause to you my friend! I am now a dual-boot fool.A roaring success as I have now installed Ubuntu 6.06 onto my 10 Gig Maxtar HD.And,just as you mentioned,I am able to select my OS at the start up prompt.No probleams so far.
 Now,how picky is Ubuntu with Apple's Airport Extreme? i wanted to configure my ubuntu system for internet access but I do not know where to do this.
 Thanx again for all your help.When I get my new Mac,I believe the Ubuntu HD will go back into it's old case ( A Quadra 800.Ah the days of beige towers!),the G4 will be relegated to a rack along with my Digi 001,a QSC CX502 power amp,and a Behringer Pro Bass V-Amp so I can use Pro-Tools for my effects processing (I'm a musician,could ya tell?:D ).I'll use the new Mac for everything else.So you can see why I want to have internet usage on the Ubuntu system.Heck,I may go all Ubuntu if I find some great pro-recording software.
 Take care,

 Juan

To use your Airport Card you need the firmware for it ( the drivers are already installed on your system but the firmware can't be bundled with the Ubuntu installer for legal reasons ) I have put my firmware files in a zip file on my web site here [http://trogdoor.googlepages.com/firmware.zip](http://trogdoor.googlepages.com/firmware.zip). Just take all the files in the firmware folder in that zip file and move them to /lib/firmware then restart. If you use the default network-admin program that comes with Ubuntu you need to enter the ESSID manually to connect to a network so once you have your internet working install a program called wifi-radar which will detect and connect to wireless networks. As for recording software, I use Audacity which is also available for windows and OS X.

---

### Post by n00bWillingToLearn on 2006-07-14
In going through the hassle of trying to remaster the Ubuntu liveCD I completely forgot that you can actually install programs on the running liveCD, so there is no remastering necessary! So here is how to resize your HFS+ partition the easy, graphical way.

Just boot from the Ubuntu / Kubuntu / Xubuntu 'Desktop' CD then open the terminal and type ```
sudo apt-get install qtparted
sudo qtparted
```

The qtparted application should open and it is fairly easy to use but If you have any questions just ask.

---

### Post by meshica7 on 2006-07-14
nooB,
 Thanx for the firmware files.
When I try to move the files to lib/firmware, I am told that I do not have sufficient permissions to do so.I checked the properties for the lib/firmware folder and it says that 'root' only can modifiy this folder. I thought that by default,since I did not create other login names,I was the root or admin at login.If not,how do I get root access?
 I also downloaded WiFi radar.Do you recommend this app?
 Thanx again and especially for all your patience.
 Juan

---

### Post by n00bWillingToLearn on 2006-07-14
> **meshica7 said:**
> nooB,
 Thanx for the firmware files.
When I try to move the files to lib/firmware, I am told that I do not have sufficient permissions to do so.I checked the properties for the lib/firmware folder and it says that 'root' only can modifiy this folder. I thought that by default,since I did not create other login names,I was the root or admin at login.If not,how do I get root access?
 I also downloaded WiFi radar.Do you recommend this app?
 Thanx again and especially for all your patience.
 Juan
Sorry, I forgot about that, In Ubuntu (and OSx for that matter) you can't really log in as root ( by default ) but this is actually a good thing, having the Administrator account enabled by default in Windows is the main way that viruses and trogans can gain control of your system so easily (for instance if someone gains control of IE through an expliot they can change / add / delete any System file they want but if someone gains controll of firefox in Ubuntu, since firefox doesn't have privaleges to change system files niether does this would be hacker ). To give an application super-user ( root ) privaleges you have to explicitly state that you want to do so and enter your password again. From within the GUI most Applications that need root privaleges to run will just show a dialog box asking you to enter your password when you try to run them. To explicitly open a program with root privaleges you use the 'sudo' command from the terminal. For instance, if you want to install wifi-radar from the terminal you would type ```
sudo apt-get install wifi-radar
``` if you just typed ```
apt-get install wifi-radar
``` You would get an error saying that apt-get needs to be run as root. So to open a file browser window as root you would go into the terminal and type```
sudo nautilus
``` because nautilus is the file browser application for Ubuntu, note that only that one window will have root privalages  and the rest will still be running as 'you'. "I also downloaded WiFi radar." I think you are about to fall victim to the first mistake EVERY new linux user makes, trying to istall an application by going to the website, downloading it, and running the installer. If the file you downloaded has a .deb extention then that will work, but there is a much cooler, and much easier way too install applications in Ubuntu see this link that explains it better than I can [http://monkeyblog.org/ubuntu/installing/#package_manager](http://monkeyblog.org/ubuntu/installing/#package_manager)

---

### Post by meshica7 on 2006-07-15
That's great info on the sudo subject.Very helpful.
Well I suppose I lucked out with Wi Fi Radar as it did have the .deb ext and installed without a hitch.I will check out the link you provided as that was going to be my next line of questions.It seems that there are a few options for installing apps in Linux.I was able to use **sudo mv -t** commands the move the firmware files you linked to me into the /lib/firmware directory.I could not do this as the non root user so I broke out my Unix books and gave it a try.It worked! I feel like a geek!:mrgreen: 
BTW I got WiFi to recognize my Airport Extreme.No I have to configure my network to br able to gain internet access.So far,no luck :-k .
 What app do you recommend for ripping and listening to mp3s?I also want to connect my i-Pod and be able to add/remove/listen to mp3s from my i-Pod.
thanx again!

Juan

---

### Post by meshica7 on 2006-07-15
WOW! What a great [link]("http://monkeyblog.org/ubuntu/installing/#package_manager") nOOb!This should appear in the new Ubuntu book for certain!I printed it out and will start reading it ASAP.I'll let ya know how it goes...
Juan

---

### Post by ravindran.k on 2006-08-05
> **ristosu said:**
> Nice photo.
 
That's around 37 GB, your HFS+ partition? May I ask, how much RAM do you have? The reason for asking: I tried to shrink an HFS partition running from liveCD, and received Out of memory error.
 
Hi ,
 
Im helping one of my friend to resize his MAC pArtition from 39 GB to 34 Gb .. and we are getting the same Out of memory error..This happens at 96%...
 
He has 128 Mb RAM. Any suggestions?  help!!!!
 
Meanwhile , I have asked him to try again..

---

### Post by jaumedejuan on 2006-09-06
My BIG problem is that I can't deactivate the journalizing.

The situation is that I used to have a firewire enclosure that contained a hd formated with hfs+, this enclosure was connected to my ibook.

The enclosure died, and now I want to get the disc working on my x86 xubuntu machine and move everything to ext3. To do this I want to split in two partitions the disc and work from there.

The thing is that I don't know how to deactivate the journalizing without mac os x, hence the mentioned method doesn't work.
If I try to resize with parted, this one complains about the journal being activated.

Do you guys know about any utility that allows me to deactivate the journal without having a mac?

---

### Post by cesarp60 on 2006-09-24
[SIZE="4"][FONT="Garamond"]Hello ... I want to install Ubuntu into my PowerBook G4, running Tiger 10.4.7. I really do not want to format my HD on my mac. Can you tell me step by step on how to do the whole process: partition, installing, dual booting, what bootloader to use and how. More like an HOWTO dual-boot MAC OS X and Ubuntu on PowerBook G4 (PowerPC) without formatting current HD. Also, how save is to do it? Is there a chance I might loose my data? If during the process something happens, how do I recover? Thanks, I greatly appreciate it. I need to use Ubuntu for school.:D 

Cesar E. Perez[/FONT][/SIZE]

---

### Post by cesarp60 on 2006-09-24
Hello ... I am looking into dual booting my PowerBook G4 (PowerPC) with MAC OS X and Ubuntu. Could please provide me with a step by step on how to do it. Baby steps ... Also is there a risk of loosing data? I do not want to format my HD and going through the process of backing up my data doesnt sound to appealing. Also, what bootloader to use and how. Thanks!

Cesar E. Perez

---

### Post by n00bWillingToLearn on 2006-09-24
> **cesarp60 said:**
> Hello ... I am looking into dual booting my PowerBook G4 (PowerPC) with MAC OS X and Ubuntu. Could please provide me with a step by step on how to do it. Baby steps ... Also is there a risk of loosing data? I do not want to format my HD and going through the process of backing up my data doesnt sound to appealing. Also, what bootloader to use and how. Thanks!

Cesar E. Perez

There is always a risk when repartitioning and you should **always **backup any important data before doing it. Ubuntu will install a bootloader called yaboot, but you don't need worry about how to configure it as that is done automatically by Ubuntu's installer. Beyond repartitioning, everything else about installing Ubuntu on a PPC mac is fairly straitforeward. I don't have time to give step by step instructions right now but I will probably be able to tomorrow. Also, just so you know, not many people pay attention to old threads like this one so you may get a faster answer by creating a new thread.

---

### Post by johnrobert on 2006-09-27
Big thanks to closet geek and everyone who contributed to this thread. I just used the procedure on my G4 Powerbook with Dapper, and am now writing to you from Ubuntu. I had thought I would have to buy Yellow Dog or something just to get my hard drive partitioned, but this worked beautifully.

One note. Closet geek's instructions have us using parted in the middle of the Breezy installation, but the Dapper installation doesn't offer the same option of getting to parted in mid-stream. But Wheli's note on the Dapper installation board explained that you can do your partitioning before you start the installation. Just boot the live CD, then open a shell and follow closet geek's instructions regarding parted. After that you can start the Dapper installation and confidently select "Use free space" when you get to the partition section of the installation, knowing that you have already created the free space you need.

Again, thanks to everyone.

---

### Post by iAndy on 2006-10-18
Great!  Thanks for this!...I've been looking into this here:

[http://ubuntuforums.org/showthread.php?p=1628614#post1628614]("http://ubuntuforums.org/showthread.php?p=1628614#post1628614")

Just a quick question first.

What does the journaling on the Mac partition actually do?...and therefore what will I lose by disabling it?

Ta!

---

### Post by iAndy on 2006-10-18
Scrap that journaling question!

Eventually got through the whole thread and it was all explained to me!

Had me going there for a sec with the Live CD, but I'm currently 12% shrinking my partition using parted!...all seems to be going well!...fingers crossed!

I've given 10Gb over to Ubuntu, which leaves me with 5Gb free for OS X!  (Yes, on my 100Gb hard drive I'm down to my last 15Gb and decided to dual boot!...logical!)

Thanks for this invaluable thread!  To the OP and to all those contributing to it. It has stayed quite concise and easy to follow, unlike a lot of threads elsewhere...I've learnt so much off it! (which is half the reason I'm doing this!!)

...baring in mind this happy optimism will be shattered if something goes wrong now!...currently at 15% now!  it's taking forever to shrink...not sure what the quick 1 second was about!...Maybe it's because my drive has become full numerous times so has got the data there, not just blank spaces like a fresh drive...I dunno.

---

### Post by Saba on 2006-10-20
So  'hotani' did you go thru? Im kinda in a sim situation here... While I couldn resize I went old school and bakup data to install from scratched. But guess what? Either I got Ubuntu or OSX. Never could get installed both for booting... I did every possible partition to see If I can install OSX after Ubuntu or reverse... but it seems I lack the knowledge to do that.. HELP!

---

### Post by vagery on 2006-10-29
if got 2 little problems, 1 is that when im installing i never get givin the option to open a shell, and second, if i just try it in terminal, my partion is read only...

and help guys?

quick edit* I am using a PowerBook G4 17" with ubuntu 6.06

Thnx

---

### Post by organicchunkysalsa on 2006-11-29
ok, for those of you having difficulties getting to your HD when running parted you need to do this once you are in the shell: 

first type "sudo -s" to gain root access

then type "parted /dev/sda" (assuming that sda is your HD, you can check in the Disks application located in System>Administration)

you can follow the main instructions from here starting with the print command

assuming you are installing dapper you can run the install after the partitioning is complete an tell the install to install on the empty space on the disk.

---

### Post by agordonxii on 2006-11-30
I'm runing a live CD with edgy and it has a resize option and is running right now, does anyone know how long this should take:confused:

---

### Post by roachjm on 2007-01-15
I successfully resized my partition for Mac OS X.  Is there a way to merge two Mac OS X partitions without deleting what is on them?

---

### Post by Gen2ly on 2007-02-28
NOTE: I had to use the actual disk identifier.  Had some prompt tell me I didn't have the ownership or what not.
> sudo diskutil disableJournal /dev/disk0s2

---

### Post by bodek on 2007-03-15
Hi,
just wanted to share that installing edgy was a breeze. Gparted didn't have any problems with resizing the HSF+ partition, only before I disabled journaling. Strangely what I had to type was:
> sudo diskutil disableJournal /
I was to delete osx from the drive completely, but thanks to this trick it will stay there till feisty will come.

---

### Post by LoneTrumpeteer on 2007-05-04
Hello,

I've recently come across this thread and have been trying to get all this to work, but no matter what I do I get the same error message.  I've gone throught this thread, but still haven't been able to get it to work.  As far as I know, I've followed the instrucions correctly.  I'm new to Ubuntu and relatively new to mac, so I'm not well versed in how to go about fixing my problem.

The error message:

[IMG]http://img501.imageshack.us/img501/4470/errortz4.jpg[/IMG]

I'm using a Powerbook G4 with 1gig or ram running OSX 10.4.9.

Thanks for any help.

---

### Post by stylecramper on 2007-06-03
> **closet geek said:**
> Once the shell has started type: "parted", from here I can't give you exact instructions as these steps might vary slightly depending on your setup but for me I then typed:

```

print

```

this showed me my list of partitions, locate the partition you want to resize (it should be obvious) and note down the "Minor" number. 

This sounds like exactly what I need. However, parted doesn't seem to work for me. When I try to do the "print" command, I get an error:

Unable to open /dev/hda - unrecognized disk label

And I can't get any farther. This is on a G5 with two internal  HDs and one Firewire external HD.

---

### Post by stmiller on 2007-06-03
> **stylecramper said:**
> This sounds like exactly what I need. However, parted doesn't seem to work for me. When I try to do the "print" command, I get an error:

Unable to open /dev/hda - unrecognized disk label


Powermac G5? Should be /dev/sda

---

### Post by stylecramper on 2007-06-04
> **stmiller said:**
> Powermac G5? Should be /dev/sda

Interesting...any suggestions?

---

### Post by stylecramper on 2007-06-04
BTW, I just tried it again and noticed another error message that I'd missed. Right away when starting parted, something like this appears:

Unable to open /dev/hda read-write, /dev/hda is being used read-only

---

### Post by stylecramper on 2007-06-04
I've given up on the parted trick and just used Disk Utility to create new partitions on my external Firewire drive (after full backup), and managed to successfully install Ubuntu on it. Now a new issue -

I can hold the Option key and reboot, and can click on the Linux startup disk. This takes me to a screen with a command prompt asking me to press L to boot into Linux, M for MacOSX etc. I press L (lowercase) and I'm immediately taken back to the startup disk choice screen. I can do this in a loop forever if I want...fun.

---

### Post by stylecramper on 2007-06-04
To be more specific, clicking the Linux startup disk button shows a black screen with this white text:

[COLOR="RoyalBlue"]First Stage Ubuntu Bootstrap

Press l for Gnu/Linux,
x for MacOSX,
c for CDROM

Stage 1 Boot:[/COLOR]

After pressing any key, or just waiting five seconds, this line appears:

[COLOR="RoyalBlue"]Loading second stage bootstrap...[/COLOR]

But then I'm immediately taken back to the startup disk choice screen again.

---

### Post by nico on 2007-06-16
Worked fine for me, a word of caution however, it took over 36 hours! I resized one external hard drive from 500GB to 211GB.

---

### Post by geira on 2007-07-07
> **stylecramper said:**
> I can hold the Option key and reboot, and can click on the Linux startup disk. This takes me to a screen with a command prompt asking me to press L to boot into Linux, M for MacOSX etc. I press L (lowercase) and I'm immediately taken back to the startup disk choice screen. I can do this in a loop forever if I want...fun.

Have you read this thread? Basically Firewire support is enabled only after the kernel has started and a root filesystem set up.

[http://ubuntuforums.org/showthread.php?t=29837](http://ubuntuforums.org/showthread.php?t=29837)

---

### Post by SurR3AL on 2007-08-18
> **stylecramper said:**
> This sounds like exactly what I need. However, parted doesn't seem to work for me. When I try to do the "print" command, I get an error:

Unable to open /dev/hda - unrecognized disk label

And I can't get any farther. This is on a G5 with two internal  HDs and one Firewire external HD.

i got this error message too but there's a way to get around it. Do not enter the parted prompt, but from the terminal type :
```
parted /dev/hdc print
```

(replace hdc with the drive which contains the hfs+ partition you are trying to shrink.

after u get the required information, just type ```
parted /dev/hdc resize (partition number) (start location) (end location)
```

and it should do the rest :)

(again replace /hdc with the drive you are interested in)

---

### Post by computer geek on 2007-08-24
does this HOWTO work with 7.04?

---

### Post by lex1 on 2007-08-29
This is a nice howto.

I would like just say with the advent of vmware fusion etc it may be more simple to use visualization
instead of dual boot, its a personal thing I guess


lex1

---

### Post by YoZeff on 2007-09-05
So this means that i'm able to drive both OS X and Ubuntu on the same (not-intel-)**PPC**(G4)?

---

### Post by altalchemist on 2007-12-07
Under OSX Leopard you can now resize your partitions using the disk utility. Open up disk utility - highlight your primary hard disk on the left hand side. Click the 'partition' tab. You can then click and drag your OSX partition to whatever size you like. Having left the free space you can go ahead and install alternative OS as required, or if you prefer you can create the partitions you want using disk utility.

---

### Post by anthonylane13 on 2007-12-08
I'm also having problems with this:

The partition to shrink is no 5:

Number Start End Size File System Name
1 1kb 32kb 32kb Apple
2 33kb 65kb 33kb Macintosh
3 66kb 98kb 33kb Macintosh
4 98kb 360kb 262kb Patch Partition
5 360kb 60GB 60GB hfs+ MacOS

and the command I entered in parted was:
resize 5 360kb 45MB

Then I got this error:
Error: Trying to register an extent starting block at 0xAF0429, but another one already exists at this position. You should check the file system!
Error: Could not cache the file system in memory.
Error: Data relocation has failed.
Error: Resizing the HFS+ volume has failed.

Any help would be very much appreciated. :confused:

---

### Post by VidiotGeek on 2007-12-31
> **compwizz said:**
> I have re-enabled it on my system with no problems at all.  The Journaling only affects the partition that OS X is on, so enabling won't cause any problems with the Ubuntu partition.

I've been interested in dual booting Tiger & Ubuntu for a while now but I'm just now ready to actually attempt it. I think I could follow these directions easy enough but I'm curious as to why you have to turn journaling off on the Mac OS partition first? I assume it's just to be able to repartition using the Ubuntu tools without erasing any data.

I make regular clones of my Tiger install to an external drive so I'm not terribly concerned about hosing my Mac OS install. Would it be much easier if I just cloned OS X, completely wiped my internal drive, partitioned, installed Ubuntu, & cloned my Mac OS system onto it's new partition? If I did it that way, would I be able to use Apple Disk Utility? I would want Ubuntu on the second partition, on the outer edge of the disk, since Mac OS will be my primary OS. If that process will work, I think it will be much easier for me. Thanks.

---

### Post by oswaldkelso on 2008-01-02
[this is how I do it]("http://forums.debian.net/viewtopic.php?t=18193&highlight=")

---

### Post by VidiotGeek on 2008-01-03
Super! This makes things so much easier. One other question, does Mac OS X recognize a partition with Linux on it as a boot volume option in the Startup Disk preference pane of System Preferences? I imagine that's a long shot but it would be awesome if it did.

---

### Post by oswaldkelso on 2008-01-04
> **VidiotGeek said:**
> Super! This makes things so much easier. One other question, does Mac OS X recognize a partition with Linux on it as a boot volume option in the Startup Disk preference pane of System Preferences? I imagine that's a long shot but it would be awesome if it did.

No. Not if my memory serves me right, but by having linux installed on the free space **after** osx. 

During boot you will get and option of:
X for osx
L for linux
C for cd

if you dont select one within so many seconds it will boot linux. (these options can be changed) this is a much faster option than holding down the option key (sometimes called to alt key)  on boot and selecting your boot drive from there.

---

### Post by havoc_joe on 2008-01-14
This is a great HOWTO. Thanks very much to everyone who contributed!

---

### Post by Jammy4041 on 2008-05-18
Does this still work? I mean, can I use this method in the Xubuntu 8.04 alternate cd. What's the difference between this guide and the Xubuntu 8.04 version?

---

### Post by LeSid on 2008-06-17
Partitioning worked for me on a PBook G4 1.6, but I had to use the liveCD of Ubuntu 7.04 (I don't know why the liveCD of 7.10 didn't load) to get parted starting. The first boot into OS X after the shrinking took longer than usual (I presume there was a disk check performed), but it worked fine. 

Going to install ubuntu now...

---

### Post by rbanavara on 2008-06-23
I tried this on my hackintosh... and it works (though gparted live CD refuses to do this). I did shrink the hfs+ and also moved it. Really a cool how to!

Also I could not shrink when the units in parted was set to GB, but worked when it was set to MB (not sure if I made a mistake while specifying start & end numbers).

---

### Post by juanitobanana on 2008-07-06
Unable to open /dev/hda - unrecognized disk label


Hello, I had exaclty the same problem after following all the instructions as described in this post. The only solution I found (after trying several things and falling into many dependency hells while booting on a live cd) was to download a gentoo live cd (the one from 2007) boot with it and use their version of parted which works fine. So the tool is out there somewhere. And it's open source. Please put it on the next ubuntu live cd's so we can go a step further on the "just works" concept!

by the way I have an ibook g4 ppc. I think from what I read the ppc are more problematic than the intel ones.

---

### Post by comer on 2008-07-09
I google partition manager find some freeware bellow:

paragon  [http://www.paragon-software.com](http://www.paragon-software.com)
I have not used,no comment!

easeus partition manager 
I download from brother soft 
[http://www.brothersoft.com/easeus-partition-manager-51814.html](http://www.brothersoft.com/easeus-partition-manager-51814.html)

It worked OK, but failed when i tried to  merge partition. so i have to allocated the free space to another partition. Partition magic may merge two partitions which will cost you $69.95

cute partition manager
[http://www.giveawayoftheday.com/freeware/partition_download.shtml](http://www.giveawayoftheday.com/freeware/partition_download.shtml)

---

### Post by applefat on 2008-07-10
Hello--

I'm attempting to shrink an os X partition to install Ubuntu 7.04, but when using print or p, parted tells me:

*error: unable to open /dev/hdb - unrecognized disk label*

I think that hdb is the cdrom, which would make sense since it's running from a cdrom. Must I somehow change the default volume that it looks at to be my main harddrive?

---

