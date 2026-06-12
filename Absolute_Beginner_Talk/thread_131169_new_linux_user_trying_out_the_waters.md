---
title: "new linux user trying out the waters"
date: 2006-02-15
forum: Absolute Beginner Talk
---

### Post by zmatt on 2006-02-15
OK i have used DOS and windows since i can remember, and i also used OSX (i have a iBook G4) and at the advice of my tech buddies im trying out linux, they told me Ubuntu was a good place to start cause it fairly powerful and isnt windows trying to be linux like linspire. so heres my setup Athlon64 3400+ 512mb of PC2700 RAM 200gb SATA hdd, DVD+-RW drive and CD-ROM drive an SIS salmon mobo with Nvidia 6600 256mb garphics, as i speak i am downloading 5.1 64bit live cd and install cd, i have partition magic and am running windows XP, can i make a linux partion (ext2 or ext3 i dont know) and will Ubuntu recognize it and after i install how do i make a boot menu to choose weather to use XP or linux?

---

### Post by ahood on 2006-02-15
[QUOTE=zmatt]OK i have used DOS and windows since i can remember, and i also used OSX (i have a iBook G4) and at the advice of my tech buddies im trying out linux, they told me Ubuntu was a good place to start cause it fairly powerful and isnt windows trying to be linux like linspire. so heres my setup Athlon64 3400+ 512mb of PC2700 RAM 200gb SATA hdd, DVD+-RW drive and CD-ROM drive an SIS salmon mobo with Nvidia 6600 256mb garphics, as i speak i am downloading 5.1 64bit live cd and install cd, i have partition magic and am running windows XP, can i make a linux partion (ext2 or ext3 i dont know) and will Ubuntu recognize it and after i install how do i make a boot menu to choose weather to use XP or linux?[/QUOTE]

Hey Zmatt,

**Step 1a.** If you have a single hard disk, the first thing to do it defrag Windows. It is extremely important to get those Windows files organized before you do anything. 

**Step 1b.** It is a good idea to backup your Windows partition or the important data that stored on it. 

It is easier if you have a second hard disk to install Ubuntu as defraging Windows would be unnecessary.

**Step 2.** We are going to assume your entire 200 Gb hard disk is  a single Windows partition. If this is the case, then you need to free up some space for Ubuntu. Use Partition Magic to shrink the Windows partition to say 150 Gb, the rest will be used by Ubuntu.

***DO NOT use Partition Magic to create a second partition or format a second partition.*** Just leave the freed up space (50 Gb) as empty space.

**Step 3.** Install Ubuntu. The installation procedure will ask you where on the disk to install Ubuntu. You will want to install it on the 50 Mb of free disk space. It should be evident from the install what this is, but should be something like hda2. ***DO NOT instruct Ubuntu to install on the entire disk.***

During the install, Ubuntu will format the unused space in the format that it prefers.

**Boot Menu** - Ubuntu will install the GRUB boot loader by default. You don't need to do anything special. Once the install is complete, the boot loader (GRUB) will appear on bootup and you will choose which OS to use (Ubuntu or Windows).

If you want Windows to be the default OS, then this can be configured after you log into Ubuntu. 

In Ubuntu, open up a terminal by going to Applications --> Accessories --> Terminal.

Type the following

> sudo gedit /boot/grub/menu.lst

You will be asked to enter a password. Enter your User password.

Then follow these instructions...

[grub  menu.lst config](http://ubuntuforums.org/showthread.php?t=122131&highlight=load+windows+default+grub)

[ Make Windows the Default OS w/ GRUB](http://ubuntuforums.org/showthread.php?t=108610&highlight=load+windows+default+grub)

Hope this helps.

Dr. Hood

---

### Post by zmatt on 2006-02-15
thanks for the help, the hard disk has 2 partitions one is 5gb and is a recovery partion the other 195gb is left to windows. so you say i can limit windows to a certain amount without making a new partion, how do i do this? i have already made a backup of my harddrive (i do this every month anyway) you nevr know what windows might do!

---

### Post by aysiu on 2006-02-15
The fifth link of my signature walks you through the entire dual-boot process... and it has screenshots.

---

### Post by Mr.X on 2006-02-15
[QUOTE=aysiu]The fifth link of my signature walks you through the entire dual-boot process... and it has screenshots.[/QUOTE]
Hehe, thats cool.
Where in australia are u from?

---

### Post by mwanafunzi on 2006-02-15
> Step 1a. If you have a single hard disk, the first thing to do it defrag Windows. It is extremely important to get those Windows files organized before you do anything. 

Just reading through the post and had a question ( as I am new as well). Why is it important to defrag?

---

### Post by jimrz on 2006-02-15
defrag will move data that is near the end of the disk, if any, towards the beginning. this reduces chance of lost data when you shrink the partition to make room for the ubuntu install.

---

### Post by aysiu on 2006-02-15
[QUOTE=Mr.X]Hehe, thats cool.
Where in australia are u from?[/QUOTE] I've never been to Australia before, actually, but it's on a list of "must-visit places" my wife and I have.

That excellent dual-boot tutorial is written by Herman, one of the other forum members here.

---

### Post by SMF on 2006-02-16
I am a super newbie and I had no Idea that I had to defrag my pc before installing my ubuntu 
never the less I was able to figure out the installation using this older tutorial for unbuntu, I was able to install the Ubuntu 5.10 "The Breezy Badger"
Using this older tutorial
Ubuntu Kubuntu 5.04 Hoary Newbie Install Guide
(This is not for dual booting so somethings in your installation will vary slighty) but this is basicly what you will be looking at when you install ubuntu
[http://www.mrbass.org/linux/ubuntu/install/](http://www.mrbass.org/linux/ubuntu/install/)

You sound like you have enough experience on a pc to know what you should do and what you should not do. After a whole day of reading here and there I was ready to install my box. I have used Partition Magic in the past and I think it sucks. I found a prog called Partition Commander that was so easy to use I did not even need to know what I was doing. All common sense.
Partition Commander used to prompt me on boot up if I wanted to run Windows or Linux XP desktop 2006 <---bad IMO

Now that I installed ubuntu I get a promp saying from new messege I think this is ubuntu promp asking me if I want to run Windows XP or Ubuntu.

I hope I am not confusing you cus I am so green it hurts. But I did get mine up and running and I am so very excited. I love ubuntu and I am glad I finaly took the chance to try it out.

Good luck hope you are successful too.

Peace.

---

### Post by steve.horsley on 2006-02-16
[QUOTE=zmatt]thanks for the help, the hard disk has 2 partitions one is 5gb and is a recovery partion the other 195gb is left to windows. so you say i can limit windows to a certain amount without making a new partion, how do i do this? i have already made a backup of my harddrive (i do this every month anyway) you nevr know what windows might do![/QUOTE]
The installer has an option to reduce the size of the windows partition, but if you have a copy, partition magic might be a better option because it will be more familiar to you. Just reduce the size of the windows partition and leave the rest of the space unallocated. Then choose the installer option to use the free space.

Just to reiterate, do **not** take the Ubuntu installer option to use the entire disk, as it will take you at your word!

---

### Post by dvarsam on 2006-02-16
Hello all !!!

Let me suggest something for one Moment.

I ASSUME that YOUR Windows is NTFS Partition.

Before you INSTALL Ubuntu, let me suggest, that **after** you Defrag Windows & reduce it's size:

1. Create 1 FAT32 Partition (& Format it from Windows - there is a limit though: MAX size is 32GB)

2. Create 1 **Empty** Partition (& Leave it Empty - THIS is the Partition to Format by Ubuntu & 
     Install Ubuntu).

Basically ALL I am suggesting is to HAVE 1 additional Partition as FAT32, to use it ONLY for the case that You want to transfer Files back & forth from Windows to Ubuntu (and opposite).

Windows (narrowminded mechanics & politics) is that NTFS does NOT work with Linux.

So, if you have a Linux file to copy to NTFS Windows, it has to pass first from your FAT32 (intermediary) Partition.
Linux can Read & Copy from NTFS but can NOT write to your NTFS.

That is why you NEED an (intermediary) FAT32 Partition.

However, I assume that you could probably do this ALSO after you have Installed Ubuntu.

Just decrease the Windows Partition more, create some NEW space, & Format it from Windows (DO **NOT** format it from Linux - Remember .... the narrowminded mechanics & politics of Windows....).

Hope I helped.

Dimitris.

P.S> One other advice: Since you are new, give yourself some time to get acqainted with Ubuntu.
         At first I thought it was too complicated, NOW I see its Superiority to Windows. So, do NOT
         panic, keep reading Posts in the Ubuntu Forums (this helps you familiarise with your NEW
         OS) & enjoy your Stay.

P.S2> ... Now that you are trying the "waters" - you will find out that it is pretty calm & safe here !!!

---

### Post by zmatt on 2006-02-16
thanks for all the help i will ebgin the insall today and will update if i run into anything. Yeah i agree the "narrow minded windows" thing is anoying to borrow a page from Job's book Think Different! i have found that it dosnt just apply to my mac either. NTFS stinks and Gates had the opportunity when they made win95 to totally overfaul the filesystem, from what ive heard a reason for Linux's superioity is its filesystem (among other things). i feel that this will prove to be sucessful and will look forward to doing more with linux.

Cheers.

---

### Post by Lord Illidan on 2006-02-16
[quote=zmatt]thanks for all the help i will ebgin the insall today and will update if i run into anything. Yeah i agree the "narrow minded windows" thing is anoying to borrow a page from Job's book Think Different! i have found that it dosnt just apply to my mac either. NTFS stinks and Gates had the opportunity when they made win95 to totally overfaul the filesystem, from what ive heard a reason for Linux's superioity is its filesystem (among other things). i feel that this will prove to be sucessful and will look forward to doing more with linux.

Cheers.[/quote]

NTFS is better than FAT 32. I am not sure if it is better or worse than Reiser 4 or Ext 3, need benchmarks to prove it.

 But it is harder for hackers to reverse engineer the drivers needed to write data on NTFS, that's all.

---

### Post by ahood on 2006-02-16
[QUOTE=zmatt]thanks for all the help i will ebgin the insall today and will update if i run into anything. Yeah i agree the "narrow minded windows" thing is anoying to borrow a page from Job's book Think Different! i have found that it dosnt just apply to my mac either. NTFS stinks and Gates had the opportunity when they made win95 to totally overfaul the filesystem, from what ive heard a reason for Linux's superioity is its filesystem (among other things). i feel that this will prove to be sucessful and will look forward to doing more with linux.[/QUOTE]

Good luck Zmatt!

Looking forward to hearing how it goes (good or bad). Ubuntu Forums are here to help, anytime.

Dr. Hood

---

### Post by zmatt on 2006-02-16
ok i have run into trouble, but its not with kinux, i tell partition majic to resize c drive and it gives a default 72gb free space, but when the machine reastarts partition magic starts making changes but encounters errors alot and aborts and boots to windows, i cant free up space, what should i do?

---

### Post by ahood on 2006-02-17
[QUOTE=zmatt]ok i have run into trouble, but its not with kinux, i tell partition majic to resize c drive and it gives a default 72gb free space, but when the machine reastarts partition magic starts making changes but encounters errors alot and aborts and boots to windows, i cant free up space, what should i do?[/QUOTE]

Hi Zmatt,

If the problem is Partition Magic, then trying a different partition editor/manager might do the trick....You have 2 options....

**Option 1** Give [[COLOR="Blue"]**Partition Logic**[/COLOR]](http://visopsys.org/partlogic/) a try, please note that version 0.6 is recommended rather than 0.61. Download 0.6 [[COLOR="Blue"]**HERE**[/COLOR]](http://visopsys.org/files/partlogic/partlogic-0.6-iso.zip)

**Option 2** Ubuntu has a partition editor/manager utility built into the installation module. During installation, again, Ubuntu will ask you how/where you install ubuntu. You can abort at any time should the option to choose not be obvious. To give you an idea of how Ubuntu will do this, please look at the Ubuntu installation screenshots [[COLOR="Blue"]**HERE**[/COLOR]](http://shots.osdir.com/slideshows/slideshow.php?release=305&slide=1). Specifically, it is [[COLOR="Blue"]**Screenshot 9 (Partition Disks)**[/COLOR]](http://shots.osdir.com/slideshows/slideshow.php?release=305&slide=9). You will want to select **Manually Edit Partition Table**. You then resize the partition that needs to be made smaller... See the [[COLOR="Blue"]**Linux4U Ubuntu Resize/Partition HowTo**[/COLOR]](http://www3.telus.net/linux4u/) - it explains the process in detail with screenshots.

Hope this helps....

Dr. Hood

---

### Post by AndyCooll on 2006-02-17
Hmmm ...why all the talk of Partition Magic? I didn't think you needed to use tools such as Partition Magic (as ahood mentions). If you follow Hermans dual boot instructions (as suggested in an earlier post) this avoids all that. Read through this page in particular:
[Ubuntu + NTFS]("http://users.bigpond.net.au/hermanzone/p3.htm")

As far as I'm aware the Ubuntu partitioner will do all this for you (just make sure you've defragged first!).

:cool:

---

### Post by Coelocanth on 2006-02-17
AndyCooll's right. The Ubuntu install disk will do the repartitioning for you - no need to use Partition Magic. Check out the link he provided. I used Herman's excellent tutorial to set up a dual-boot Ubuntu/Windows system on my SATA 250 GB hard drive and it worked perfectly.

---

### Post by ahood on 2006-02-17
[QUOTE=AndyCooll]Hmmm ...why all the talk of Partition Magic? I didn't think you needed to use tools such as Partition Magic (as ahood mentions). If you follow Hermans dual boot instructions (as suggested in an earlier post) this avoids all that. Read through this page in particular:
[Ubuntu + NTFS]("http://users.bigpond.net.au/hermanzone/p3.htm")

As far as I'm aware the Ubuntu partitioner will do all this for you (just make sure you've defragged first!).

:cool:[/QUOTE]

I wholeheartedly agree that AndyCool is correct. The Ubuntu installation module can do the job. However, I feel to explain the rational why I recommended Partition Magic for a Windows user......It basically comes down to 2 reasons.

(1) Familiarity Reason- If a Windows user already has Partition Magic installed, then it is likely that they have used this program in the past. Thus, a Windows user knows what to expect from Partition Magic; whereas a Windows user that has never used Ubuntu has no idea of what to expect which can be unsettling at first. Partition Magic labels partitions/drives in a manner that a Windows user can understand. In the linux/Ubuntu world, partitions/drives are labeled different, which is again unfamiliar to most Windows users who have never used linux/Ubuntu previously. Lastly, the user interface of Partition Magic will be more like what a Window user expect, whereas the Ubuntu partition module interface is spartan.

(2) Psychological Reason - There is a psychology at play for recommending Partition Magic first and Ubuntu installation second. The psychology goes like this....

Worst-Case Scenario - User uses Ubuntu installation to modify the partition table and it goes badly. User now cannot boot into Windows and Ubuntu linux is not installed. The user goes away feeling terrible and blames Ubuntu for causing the massive headache.

Best-Case Scenario - User uses Partition Magic and it fails to make the appropriate change to the partition(s). The user then uses Ubuntu installation routine and it works with no problem at all. The user then has a reason to like Ubuntu before even seeing the desktop. Can't ask for anything better than feeling super positive at such at early start.

In the end, it really doesn't matter how the user achieves the goal of partitioning the hard disk (using Partition Magic, Partition Logic or Ubuntu installation). 

I personally like to give new users options (more the better) and they can decide which one will work for them best. Again, psychology at work here. 

It is not my intention to give the impression that Ubuntu is not capable of modifying partitions. Ubuntu is a powerful program and can do this task, and many others.

I look forward to reading how it all goes for this user.

Dr. Hood

---

### Post by ahood on 2006-02-17
Sorry for the duplicat posting...

---

### Post by zmatt on 2006-02-17
thanks, i have gone throught he help giude and im about to proceed with the install, hope to see you on the other side :D

---

### Post by zmatt on 2006-02-17
ok i have tried everything including part logic and the ubuntu partition tool but it wont resize. could windows be blocking it in some strange way? when i manually resize in the ubuntu setup it it wont change it, im not ready to give up yet but i need some help.

---

### Post by ahood on 2006-02-18
[quote=zmatt]ok i have tried everything including part logic and the ubuntu partition tool but it wont resize. could windows be blocking it in some strange way? when i manually resize in the ubuntu setup it it wont change it, im not ready to give up yet but i need some help.[/quote] 
Hi Zmatt,

**You are commended for not giving up. **

Can you provide a bit more detail? Are there any specific messages that appear in these programs? More information may give other ubuntu users the information they need to suggest a solution. However, I think I may have some input.....

No, I don't think Windows is actively blocking the partitioning. At least, it would be news to me (hehe).

Can you still boot into WindowsXP (i.e., no real damage has occurred)?

This may be incorrect, but in an earlier message it is stated "...*the hard disk has 2 partitions one is 5gb and is a recovery partion the other 195gb is left to windows*.". Thus, there are 2 Windows partitions. One is for the Windows OS itself and the other is a small partition that contains rescue information (i.e., restore the Windows system should anything go bad). It isn't clear which of these partitions is first on the hard disk. This may be wrong, but I would expect that the Windows partition (195 Gb) is first and the 'rescue' partition (5 Gb) is second.

I did a bit of searching on the Ubuntu forums (not extensive) and there was one thread where a user deleted the 'rescue partition' and this resulted in WindowsXP not booting. So, it may be unwise to delete the small 'rescue partition'.

I did some more searching of the Ubuntu forums and came up with the following threads:


**Ubuntu Forum Threads to Read**

[[COLOR=Blue]**NTFS shrink and create Fat32 partit.**[/COLOR]]("http://ubuntuforums.org/showthread.php?t=119049&highlight=ntfs+shrink+partition")

[[COLOR=Blue]**my ubuntu wont install - free me from windows!**[/COLOR]]("http://ubuntuforums.org/showthread.php?t=116671&highlight=ntfs+shrink+partition")

[[COLOR=Blue]**Partitioning Problems**[/COLOR]]("http://ubuntuforums.org/showthread.php?t=110774&highlight=ntfs+shrink+partition")

The user Sef had the following instructions that might help....

> I) If there is no free space on the disk, do this:

A) Highlight the partition you want to shrink.

B) Highlight the disk size.

C) Erase the numbers on the screen and write in the new size of the partition - XX.X GB .

- Don't forget to put GB

4) Click on the button. (I think it says 'OK'.)

5) Then click on 'Done Partitioning This Disk' (or something similiar, it's the top option.)

II) Two Partitions Now

A) One which says NTFS and one that says Free Space.

1) NTFS is the XP partition
2) Free Space can used to set up Ubuntu Linux.

-) It's a good idea to maually partition, and set up a /home directory, so when you upgrade Ubuntu, your files and settings won't be overwritten. 

**NOT REALLY RECOMMENDED OPTION**

Assuming that the Windows partition (195 Gb) and the rescue partition (5Gb) is second on the hard disk, then it is seems the following would be in order....[LIST=1]
[*]Shrinking the large Windows OS partition
[*]Move the smaller 'rescue partition' so that it remains right after the Windows OS partition
[*]Make sure that free space is at the **end** of the hard disk.[/LIST]Step (c) above is very important. Free space must be at the **end** of the disk.

***If the Windows partition (195 Gb) is physically after (i.e., second) on the hard disk, then the above does not apply; however, I have no idea why the disk cannot be partitioned if this is the case (hopefully someone else does). ***

Now saying all this, I actually recommend that unless you are absolutely sure that partitioning will work, I suggest you go for a simpler option.

**SIMPLE OPTION**[LIST=1]
[*]Purchase a new hard drive at a cost you can afford. It may be only 40 or 80 Gigabyte, but plenty of room for now.
[*]Install second hard drive as a slave to the first one or as a master on a separate controller.
[*]Install Ubuntu onto second newly installed hard drive.[/LIST]No partitioning necessary, higher degree of success (IMHO) and less likely to mess up WindowsXP.

Hope this helps...

Dr. Hood

---

### Post by zmatt on 2006-02-18
when i manually try to resize, after im done it dosen tlist the new free space and the NTFS partition is the same size, oddly enough there is a 7.7mb free space that has always been there, it is courios and makes me wonder if HP was unable to format all 195gb. anyway i have a 45gb ide hdd that i loaned out to my freind until he gets a new one, i might just try and install ubuntu on it instead when i get it back.

---

### Post by nalmeth on 2006-02-18
Gparted is included on the knoppix liveCD, and ubuntu aswell I think. I don't know much about partitioning, so I won't even try to tell you what to do there...

If/when you get ubuntu64 up and going, get automatix:
[http://ubuntuforums.org/showthread.php?t=66563](http://ubuntuforums.org/showthread.php?t=66563)
and follow this howto for installing a 32-bit chroot environment to run 32-bit apps:
[http://ubuntuforums.org/showthread.php?t=24575&highlight=chroot+32bit](http://ubuntuforums.org/showthread.php?t=24575&highlight=chroot+32bit)

change *every single instance* of 'hoary' to 'breezy' --> don't forget any.

Note, I use the regular i386 ubuntu on my intel64, and it works great.

Have fun!

EDIT: do the chroot first, and if you want to run automatix, do it through your 32-bit chroot as its not meant for 64-bit users yet --> if, in fact you do this stuff

---

