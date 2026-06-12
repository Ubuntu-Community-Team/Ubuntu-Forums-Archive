---
title: "First Time Install -- NTSF drive help"
date: 2006-10-09
forum: Absolute Beginner Talk
---

### Post by SaltyMcCracker on 2006-10-09
So when I first built this computer I partitioned my drive into three parts:

C:/ For windows install and important programs
E:/ For music, videos, and docs
F:/ For the hell of it.

I recently decided to install Ubuntu and give this free os thing a go.  I was impressed by the live cd and thought all these people can't be wrong.

When I went to do the install, I read some stuff about NTSF and the possibility of problems arising.  While I can build computers and install according to detailed instructions, I really don't know the difference between NTSF and FAT32.  

I want to install Ubuntu on the F:/ partition.  When I go through the install though it just lists the single HDD (no specific partitions) and so I am hesitant to go much further (don't want to lose anything I currently have).

Is there a way for me to install just on the F:/ partition, or is my best route to go out and buy another HDD for $50?

Thanks for the help in advance.

---

### Post by aldegaz on 2006-10-09
wich Ubuntu version are you trying to install? Dapper had a nice GUI to move around the partitions.
It should tell you something...

---

### Post by Kateikyoushi on 2006-10-09
You can install it by replacing your F partition with the partitions Ubuntu requieres. Backup your data from the F partition.
Select partition manually during installation.

[Read this]("http://users.bigpond.net.au/hermanzone/") for more information.

---

### Post by SaltyMcCracker on 2006-10-09
OK.

So I'm trying to manually edit the partitions.  Still only the actual harddrive shows up, not the actual partitions.  

See below.

[ATTACH]17234[/ATTACH]

Also, it's telling me I only have about 800 MBs free on the hard disk.  When I'm in windows my F:/ partition says it has about 23 GB free (not to mention the space on my other partitions)

see below.
[ATTACH]17235[/ATTACH]

When I try the automatic format it tells me I don't have enough space for the install, and when I lower the space on the sliderbar the busy wheel comes up but nothing happens (waited a good 40 minutes).  

If I try to resize this partition, it only lets me resize it to that 800 MB lower number.

Any advice?

Should I use that alternate install CD that is suggested in the link you provided? Or should this install CD work?

---

### Post by ruraltodd on 2006-10-10
new to ubuntu too - i have vista installed on c drive and installed ubuntu on the same - when i got to the option to select petition for inststall  i choose petition and install on free space - i selected it and end result was vista was still there - on boot a dialogue came up to select os - ubuntu first then windows os - my d drive has xp pro so the windows os choices were vista on c or xp pro on d  - i could choose either and all booted to desktop and all was ok - i took the risk of not saving anything but if you have the option to save your data say on external hard drive do so - hope this 
will help - my only prob with ubuntu is not being able to connect my wireless adaptor - hope this is of some help - ruraltodd ;)

---

### Post by SaltyMcCracker on 2006-10-10
I'm just a little bit confused.  From what I understand all of my partitions should be showing up in the installer, but they aren't for whatever reason.  I understand that I may be doing something wrong but I just don't know what.

When I first built the computer I bought 1 80 gig hard drive.  I split it into two 30 GB partitions and a 10 gig partion.  They show up as C:/, E:/, and F:/ when I am using windows.  

However, when I use the installer all that shows up is the 80 GB hdd.  On top of that it says it is completely full, which it most definitely isn't.  

Can anyone provide any insight?

---

### Post by SaltyMcCracker on 2006-10-10
Well, a new day has arrived.  Does anyone have any ideas?

---

### Post by Straevaras on 2006-10-10
That's strange that Ubuntu isn't recognizing your partitions.  What did you use to partition your HD with?

---

### Post by Kateikyoushi on 2006-10-10
Oops, now I saw the screenshots.
That's unusual...

---

### Post by CatKiller on 2006-10-10
You'll need to remove that F: partition. The option to do this is called something like "manually edit the partition table". That will give you a big bunch of unallocated space. That is what Ubuntu needs to install - it won't install on an NTFS partition.

---

### Post by SaltyMcCracker on 2006-10-10
> **CatKiller said:**
> You'll need to remove that F: partition. The option to do this is called something like "manually edit the partition table". That will give you a big bunch of unallocated space. That is what Ubuntu needs to install - it won't install on an NTFS partition.

The problem is Ubuntu doesn't even recognize the partition.  It is just showing it as one big drive (despite it being partitioned into 3 parts).

I can't remember the exact program I used (this was more than 3 years ago) but it came with the HDD.

Maybe my iso file is bad?

---

### Post by Straevaras on 2006-10-10
> **SaltyMcCracker said:**
> The problem is Ubuntu doesn't even recognize the partition.  It is just showing it as one big drive (despite it being partitioned into 3 parts).

I can't remember the exact program I used (this was more than 3 years ago) but it came with the HDD.

Maybe my iso file is bad?

When Ubuntu boots off the Live CD there should be a utility that you can use to verify your CD, make sure that all the data on it is correct.  I doubt that's the problem though.

The only thing I can think of as to why Ubuntu can only see one partition is that the entire hard drive is an extended partition and/or it has something to do with the partitioner you used.  I recommend using PartitionMagic 8.0.  It's probably the best partioner out there.  Unlike GParted, or likely the partitioner built into Unbuntu, PartitionMagic isn't a destructive partitioner.  How you would get a hold of that software though, well, is up to you, legal or not. ;) 

But use that utility to verify your live CD, so we can determine whether or not that's actually a problem, although I doubt it.

---

### Post by SaltyMcCracker on 2006-10-10
> **Straevaras said:**
> When Ubuntu boots off the Live CD there should be a utility that you can use to verify your CD, make sure that all the data on it is correct.  I doubt that's the problem though.

The only thing I can think of as to why Ubuntu can only see one partition is that the entire hard drive is an extended partition and/or it has something to do with the partitioner you used.  I recommend using PartitionMagic 8.0.  It's probably the best partioner out there.  Unlike GParted, or likely the partitioner built into Unbuntu, PartitionMagic isn't a destructive partitioner.  How you would get a hold of that software though, well, is up to you, legal or not. ;) 

But use that utility to verify your live CD, so we can determine whether or not that's actually a problem, although I doubt it.


Checked the CD, it's good.  This is really weird.  Extended partition sounds familiar, I looked it up in wikipedia but don't really know how to tell if I have that or not.  
> An extended partition is able to contain several file systems, known as logical disks (though the terminology may vary slightly with operating systems).

I'm almost about to just go buy a new harddrive to use for Ubuntu.  Is this a safer option anyways?  I mean, I could get a 40 GB HDD for $50 at a Walmart and save myself alot of trouble (although I'm already pretty broke as a college student, just have to cut down on the drinking for several weekends).

So yeah, if anyone knows anything to help it would be greatly appeciated.  I realize I'm probably getting pretty annoying at this point, I was really psyched to get started on Linux and this is definately killing my excitement, but I don't think I'm going to give up now, I have too much time invested.

Thanks for attempting to help my computer illiterate self though, I really appreciate it.

---

### Post by guysmiley25 on 2006-10-10
The only this I can think of is do you have more than one hard drive and some of your partitions are on the other?

if so you can see the partitions on your other hard drives by seleting the pull down on the top right.

The different between FAT, FAT32 and NTFS mainly is that NTFS can support purmissions and large files. (Not sure what the limit is). FAT32 does not support permissions and can only have files of the size of 2GB and I think there is a limit on how big a FAT32 partiton can be. And FAT (FAT16) can only have a partiton about 2GB in size.

Let me know how you get on.

---

### Post by CatKiller on 2006-10-10
Another hard drive is a pretty safe option - it means that should one of them fail, you can still boot into the other operating system. Or if you mess up one of the operating systems and need the other to fix it, or whatever. Take out the first before you install Ubuntu in the second, though. It'll save you a lot of headaches.

It's weird that whatever you used to make the partitions before made a table that GParted couldn't read, but still allowed Windows to function. But life's full of weird things.

---

### Post by SaltyMcCracker on 2006-10-10
> **guysmiley25 said:**
> The only this I can think of is do you have more than one hard drive and some of your partitions are on the other?

if so you can see the partitions on your other hard drives by seleting the pull down on the top right.


Just one HD.  I tried using the top guy to see if maybe it was recognizing partitions as seperate drives.  They weren't there either.

> **CatKiller said:**
> Take out the first before you install Ubuntu in the second, though. It'll save you a lot of headaches.


So will it still ask me if I want to install GRUB?  Or do I just change my boot order in my BIOS to CD, Ubuntu HD, Windows HD?  Also, if I format half of the new drive into a FAT32 partition windows and ubuntu will share it right?

---

### Post by CatKiller on 2006-10-10
> **SaltyMcCracker said:**
> So will it still ask me if I want to install GRUB?

It depends. I suspect that you only get asked the question with the Alternate cd, and not with the Desktop one. I could well be mistaken though - I installed with Hoary and upgraded later.

> Or do I just change my boot order in my BIOS to CD, Ubuntu HD, Windows HD?

That will work, although you may have to go into the BIOS to switch them round on the few occasions that you wanted to boot into Windows.

A lot of BIOSes, including mine, have an option to give you a menu each time for which drive you want to boot from. Mine is called "HD Boot Sprite".

With some BIOSes there is a key you can press to get this menu, regardless of whether you've got that option turned on. I'm told that this is often F8.

With this method, each OS can be intalled in the way that it is most comfortable with. Ubuntu can install GRUB into the MBR of your Linux drive, and Windows can use the Windows bootloader in the MBR of your Windows drive. No conflicts, hopefully.

> Also, if I format half of the new drive into a FAT32 partition windows and ubuntu will share it right?

Yes, once both drives are in, both operating systems will be able to access that partition.

At some point, you'll need to decide where in the Linux filesystem you would like that partition to be mounted. /media/shared might be a good option, which will put an icon on your desktop. /mnt/shared is also a good option, which won't put an icon on your desktop.

In a similar vein, Windows will probably need to know what drive letter you would like to assign to that partition. It's been a while since I've used Windows, but I believe it was in Disk Management or similar.

---

### Post by Malta paul on 2006-10-11
Hi, You should be able to install Ubuntu on an unformated area of your HD. If it was me I would boot into windows, right click on my computer>manager>disk managment>delete your F partion (if you have backed up your files!). Exit windows.
Boot with the Ubuntu live dsk and it should now pickup an empty sector of your HD. Select this for Ubuntu to use as a linux partion
and install. Should now be OK. Remember linux does not name dsk patitions as 'C' but hda etc. Good luck Paul :)

---

### Post by SaltyMcCracker on 2006-10-11
> **Malta paul said:**
> Hi, You should be able to install Ubuntu on an unformated area of your HD. If it was me I would boot into windows, right click on my computer>manager>disk managment>delete your F partion (if you have backed up your files!). Exit windows.
Boot with the Ubuntu live dsk and it should now pickup an empty sector of your HD. Select this for Ubuntu to use as a linux partion
and install. Should now be OK. Remember linux does not name dsk patitions as 'C' but hda etc. Good luck Paul :)

Ok tried that, windows came up with an error (seen below) should I go ahead or am I getting myself in deep shit?  When I open the drive I can't see anything, but somehow 3 GB are being taken up on it.

[ATTACH]17347[/ATTACH]

---

### Post by SaltyMcCracker on 2006-10-11
> **SaltyMcCracker said:**
> Ok tried that, windows came up with an error (seen below) should I go ahead or am I getting myself in deep shit?  When I open the drive I can't see anything, but somehow 3 GB are being taken up on it.

[ATTACH]17347[/ATTACH]


Ok looking over my windows stuff, it says that I have 3 partitions, but they are all listed as primary partitions.  When I try to delete the F partition it says it is in use.

Should I force delete it?

EDIT:  Ok, checked windows and there is no paging file on the F:/ drive.  So that rules out one thing.

EDIT2:  Ok, so C:/ is my system drive, and no boot drive is identified so that means C:/ is my boot drive as well.

Is there a difference between a crash dump file and a paging file?

---

### Post by SaltyMcCracker on 2006-10-11
Ok, 

I think I may have found what is going on with giving me the warning about deleting the partition.

I have norton systemworks installed, and it has a "RECYCLER" file in the F:/ drive.

Within that folder is an NPROTECT folder, and that has a word pad file in it.  So I assume Norton is trying to protect my F:/ drive or something.

The F:/ drive also has a "System Volume Information" folder that it won't let me open.  

Both of these folders were hidden.

---

### Post by SaltyMcCracker on 2006-10-11
Does anyone have any experience with this sort of thing?

---

### Post by CatKiller on 2006-10-12
> **SaltyMcCracker said:**
> Does anyone have any experience with this sort of thing?

Not of deleting partitions in Windows XP, no. You should probably use a partitioning utility from your hard drive manufacturer rather than trying to delete it while its currently in use.

---

