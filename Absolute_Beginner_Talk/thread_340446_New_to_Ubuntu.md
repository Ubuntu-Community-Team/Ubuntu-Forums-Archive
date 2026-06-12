---
title: "New to Ubuntu"
date: 2007-01-17
forum: Absolute Beginner Talk
---

### Post by tidge87 on 2007-01-17
Hi Everybody,

Im very new to Linux and have only used Ubuntu (Edgy Eft) for about 3 hours and so far I'm loving it.

I switched from Windows XP basically because it was slow and I couldnt stand the vulnerabilities.

Linux is providing to be a great alternative :) 

I started fresh and deleted XP off my system and allocated 100% of my HDD to Ubuntu.

As much as I like it I would still like to run limited XP space just for those few Windows apps I like (and some games) (I think its cool you can DB) 

My HDD space is 80GB I was hoping to allocate half to Ubuntu, half to XP.

If I wanted to partition my space again how would I go about this? :-k  And how would I reinstall XP?

(I have the XP install disk and the serial number)

Another question: I have used the: sudo apt-get install *program* line for a few things like firestarter etc etc.

When a new release of programs come out for these programs do I have to manually update them through terminal or do they update themself?

Sorry if this is extreme noob talk but I just started :-| 

Kind Regards.

---

### Post by oilchangeguy on 2007-01-17
the best way is to reinstall windows first. then add ubuntu. when you install ubuntu you'll be prompted to partition the drive to allow both windows and ubuntu, or just ubuntu. this would probably also work in a windows install because you have the option of setting partitions. it's just easier to follow a couple of simple prompts while installing ubuntu.

---

### Post by xyz on 2007-01-17
Hi and Welcome!
A partition tool:
[GPARTED]("http://gparted.sourceforge.net/")
You'll need to set your BIOS to boot off CD-ROM and you'll than be able to resize your Win partition. Backup important stuff just in case. No need to remove Win in order to install Ubuntu.

When updates are available, a small orange icon will appear + a balloon!
Good luck and feel free to ask questions.

---

### Post by tidge87 on 2007-01-17
> **oilchangeguy said:**
> the best way is to reinstall windows first. then add ubuntu. when you install ubuntu you'll be prompted to partition the drive to allow both windows and ubuntu, or just ubuntu. this would probably also work in a windows install because you have the option of setting partitions. it's just easier to follow a couple of simple prompts while installing ubuntu.

OK thanks, so I will have to install XP over this installation and then install Edgy again and create the partition from there, sounds good.

Does this set up the dual boot automatically?

I'll try it now, thankyou

---

### Post by xyz on 2007-01-17
[Illustrated Dual Boot Site]("http://users.bigpond.net.au/hermanzone/")

---

### Post by stalkingwolf on 2007-01-17
This is how **I** do it. I use Ultimate Boot Disk to format and partition my HDD.  There are many other utilities available QParted etc.  I set the first partition for 50% , a second partition for most of the rest of the available space, and a third (the remaining space at least 512 mb as i recall)for use as as swap partition (required by most linux distros) then during the install I identify the 2nd and third partitions as ./ and swap respectively and format them
accordingly (i use reserf as i recall) .

This may not be the best way but it works for me.

---

### Post by saadakhtar on 2007-01-17
here is a direct link to the Gparted Live Cd download.
[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)
simply download the ISO image file and burn it to a cd then boot off this cd (make sure that your bios setup has your cd rom to be the primary boot device). once you have booted off the cd it will load its GUI and there you can easily resize the partition.
You have 2 options when trying for another operating system:

1) Install another operating system (i.e. Windows) on a seperate partition and dual boot b/w both the OS's.
2) Create a virtual Operating system (Virtual Machine). I would suggest this option if your computer is considerably fast.

if you are going for option 1 then its simple just repartition the drive and install the other OS on the newly partitioned drive, make sure that you setup your dual boot correctly.

if you decide that you donot want to reboot your computer everytime you want to use windows then you will need to create a virtual machine. The Software that i would recommend is VMWARE.
for more info please check these links out:
[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Virtual_Machine_Manager_.28VMware_Server.29](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Virtual_Machine_Manager_.28VMware_Server.29)

for trouble shooting and general help for the above mentioned installation please visit:
[http://www.ubuntuforums.org/showthread.php?t=183209](http://www.ubuntuforums.org/showthread.php?t=183209)

Hope this helps

---

### Post by neilq101 on 2007-01-17
Hi, I'm even newer to this sort of thing, and decided to post my uber-noob questions on this thread instead of irritating everybody by starting my own,  I'm trying to install Edgy Eft from a boot cd, but if I am going to install it, it has to be on top of an existing install of Windows XP.  I have read the community documentation on how to set up a dual boot with windows, but the partitioning procedure during install seems to have changed considerably from Badger so I'm pretty stuck.  My computer is a Dell Inspiron 1300, with a 60gb HDD, a large proportion of which is filled with Windows stuff, and I have just over 7gb left for Ubuntu.  My problem is that    being completely new to partitioning, I don't really know how to create a swap-file partition and a root partition for Ubuntu.  I resized my Windows partition to leave 3gb free,and created an extended partition from this space which I then divided into logical partitions of 512 and 2.5 gb (approx), hoping to create a swap-file and an install partition respectively; will this happen automatically? Or do i need to do something else to put everything in its place? :-?

Basically, I'm afraid of formatting my hard drive within being certain of what will happen when I do, and my Windows install is very important to preserve.  From reading the thread it sounds like there is another stage after partitioning, but.... I'm just nervous

Thanks in advance

Neil

P.S., while I'm here, can anybody give me a definitive solution to the 1024x768 resolution problem?  I'm aware it needs some fix concerning the 915 graphics chip, but all the help I've found seems to be out of date.  A link to another thread would be appreciated.

---

### Post by bodhi.zazen on 2007-01-18
See here for a great guide:

[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

But ...

you will need a little more space for Ubuntu, i usually advise 5 Gb as minimal for root.

512 Mb for swap is likely sufficient ...

And, yes the installer will auto partition free space :p

HTH

---

### Post by ekka on 2007-01-18
Don’t worry if you are new to Ubuntu or Linux, you have a lot of company here!

So are you going to install Ubuntu on just 3GB? I am not sure if that will be enough. Try to free up some more space by deleting unnecessary files in windows. May be you should try the live CD for some time before installing on the system.

---

### Post by rccharles on 2007-01-18
> **neilq101 said:**
>  I resized my Windows partition to leave 3gb free,and created an extended partition from this space which I then divided into logical partitions of 512 and 2.5 gb (approx), hoping to create a swap-file and an install partition respectively; will this happen automatically? Or do i need to do something else to put everything in its place? :-?


I'd avoid extended partitions if you need only three partitions.  You can have four partitions per disk.

The partitions tool will lead you by the hand.  You should format the 2.5gig partition to ext3. This should be the default.  Format the 512meg partition to swap.  This is on the pull down or selector.  The Ubuntu install will then pick these for installation.  

Alternatively, you can set the 3gig area to free and set install Ubuntu to the free area.  You may have to go back a step or two to see this option.

> 

Basically, I'm afraid of formatting my hard drive within being certain of what will happen when I do, and my Windows install is very important to preserve.  From reading the thread it sounds like there is another stage after partitioning, but.... I'm just nervous


You need to backup you critical files in Windows!!!  
Robert

---

### Post by neilq101 on 2007-01-18
Thanks for the quick replies! Hmm, the guide seems good but the menus he gets look different to mine; once I get to the 'Prepare disk space' screen, I am not given the option to resize the master and use the free space, but only to delete the entire disk or an option to 'use the largest continuous free space'.  This sounds like it will take all the remaining space on the drive, and i want to leave at least another 1gb as breathing space for windows.  Is this what would happen? Or would I be able to restrict the new partition without using the manual partition editor?  I understand the need for more space for Ubuntu, I just want to leave a little space for XP.

And if I did use the manual editor, set up a 5.5gig partition, and then let the installer do its stuff, that would work?  Or would i need to create logical partitions myself for the root and swapfile?

Just checking!

Neil

---

### Post by riven0 on 2007-01-18
> **tidge87 said:**
> When a new release of programs come out for these programs do I have to manually update them through terminal or do they update themself?

Sorry if this is extreme noob talk but I just started :-| 

Kind Regards.

I see everything else has been answered so I just wanted to add: the update manager will automatically detect what programs you have installed and alert you of the new version when they become available. You can update them through there.

---

### Post by neilq101 on 2007-01-18
@Robert, I have a slight problem with avoiding extended partitions; whenever i try to create my swap file after creating the root, it tells me I can only have 4 partitions, as the HDD has Windows installed on a separate partition to the main part the disk, and there is another random partition with 7meg of it's 78meg used.  I have no idea what this is, and therefore don't want to mess with it, so I can't create the two new partitions.  Will creating them in an extended partition cause a problem?

---

### Post by riven0 on 2007-01-18
That 7Mbs unknown partition is something XP sets aside. I know that gave me a host of problems when I tried partitioning my hd because it somehow locked my hd from being messed with. I corrected this problem by running chkdsk in XP, and I was able to partition after that. 

As for creating swap in an extended partition; I really don't think it should cause a problem as long as you label it right. But maybe someone else will have a better idea on this.

---

### Post by ekka on 2007-01-18
> **neilq101 said:**
> Thanks for the quick replies! Hmm, the guide seems good but the menus he gets look different to mine; once I get to the 'Prepare disk space' screen, I am not given the option to resize the master and use the free space, but only to delete the entire disk or an option to 'use the largest continuous free space'.  This sounds like it will take all the remaining space on the drive, and i want to leave at least another 1gb as breathing space for windows.  Is this what would happen? Or would I be able to restrict the new partition without using the manual partition editor?  I understand the need for more space for Ubuntu, I just want to leave a little space for XP.

And if I did use the manual editor, set up a 5.5gig partition, and then let the installer do its stuff, that would work?  Or would i need to create logical partitions myself for the root and swapfile?

Just checking!

Neil

What are your windows partitions like? Is the total 60GB in under C?
What I suggest is to go for manual partition editor
•	Create an extended partition of 5.5 GB or what ever you have decided.
•	Allocate 500(or whatever) MB for swap partition, the file type will be ‘swap’
•	Allocate the remaining to ‘/’ and this will be ext3 file type
•	As long as you are not formatting your windows under Fat32 or NTFS, your windows will remain safe.
After you have done that, the final screen will show the options you have selected, click ‘forward’ and the rest is done automatically.

---

### Post by neilq101 on 2007-01-18
Hmm, this seems to make sense, only one question:rolleyes: ; I have created the extended partition, allocated a swap file section (I eventually decided on 768 to match my 512 RAM) and selected linux-swap as the file system, but when i create the partition intended for the root, do i just select ext-3 and leave it? There doesn't seem to be any option to label either partition.

Sorry about this, but it is 5:45 in the morning here and I've been up all night!

---

### Post by neilq101 on 2007-01-18
Oh, and yes, it is all one 60gig C: drive

---

### Post by riven0 on 2007-01-18
> **neilq101 said:**
> Hmm, this seems to make sense, only one question:rolleyes: ; I have created the extended partition, allocated a swap file section (I eventually decided on 768 to match my 512 RAM) and selected linux-swap as the file system, but when i create the partition intended for the root, do i just select ext-3 and leave it? There doesn't seem to be any option to label either partition.

Sorry about this, but it is 5:45 in the morning here and I've been up all night!

Yeah, select ext3 since that's what the root partition should be in. Linux should automatically detect it as root. 

Don't stress it, though, you may want to come back tomorrow. Sleepiness can cause accidents.

---

### Post by neilq101 on 2007-01-18
AARRGGGGHHH!!! I followed your advice and started the install, but it gave me an error message telling me it couldn't resize the Windows partition!:confused: 

Is it somehow impossible to resize a partition when it isn't empty? Is that it? Or should i run the checkdisk utility like you mentioned before?

---

### Post by neilq101 on 2007-01-18
Ok, this seems completely random but when i went back the installer i discovered i had the same menus as in the psychocats guide!  Not that I have any idea what to do with them, as the guide doesnt cover dual-booting...

---

### Post by riven0 on 2007-01-18
> **neilq101 said:**
> AARRGGGGHHH!!! I followed your advice and started the install, but it gave me an error message telling me it couldn't resize the Windows partition!:confused: 

Is it somehow impossible to resize a partition when it isn't empty? Is that it? Or should i run the checkdisk utility like you mentioned before?

:lol: I bet it's that 7Mbs unknown partition that's giving you problems. That was a headache for me. ](*,) 

Yeah, so go ahead and try **chkdsk** in Windows and see if it allows you to partition after that. I know it didn't work for another guy on these forums, but it did work for me, so it doesn't hurt to try.

EDIT: Also, try running the defrag, too.

---

### Post by neilq101 on 2007-01-18
Ok, thanks for all the advice, unfortunately chkdsk did nothing, so if defragging doesnt work ill prob have to give up.  Gonna put defrag on now, ill prob post in this thread again if i do manage to get it working just so you know. thanks

Neil

---

### Post by neilq101 on 2007-01-18
Ok, I tried defragging, and it hsn't made any difference.  Basically, the problem is that when i try to partition, regardless of what I put in the free space, the program fails, and gives an uninformative error message telling me that it could not resize my main hard drive partition. This partition is formatted in NTFS, is currently 52.80gb out of a total 55.89gb, and has 43.41gb used, leaving 9.39gb free.  I am trying to reduce it by 5.75gb, leaving 3.64gb still unused by that partition.  I think I saw a guide somewhere for dealing with NTFS problems, but can't remember where... Any suggestions?

Neil

---

### Post by stalkier on 2007-01-18
Here is what I did to install Ubuntu on my desktop. First of all I have been running a dual harddrive setup for many years. I have an 80 gig main and a 40 gig backup. On the 80 gig I left it NTFS for Win XP Pro, I then partitioned the spare drive with 2 gig swap and the remaining for Ubuntu. After the installation you install GRUB and then in Ubuntu you can set it up for either XP or Ubuntu to load by default (after like 30 seconds). I believe the default OS would be Ubuntu. I changed mine to XP. 

The only problems I have run into is a Broadcom driver problem on my laptop using Linux. I hope this helps a little.

---

### Post by Darko Beta on 2007-01-18
> **neilq101 said:**
> the program fails, and gives an uninformative error message telling me that it could not resize my main hard drive partition.

I had the same problem, where I was unable to resize my ntfs partition.  The ubuntu installer did not give me much information, but when I ran gparted from the menu it at least gave me some additional info after it failed.  You have to expand the messages after the failure to see more information.  I recommend you try this to find out what's going on.  It may not be obvious from the error messages, but either google or other forum dwellers will probably be able to help.  Good luck.

---

### Post by neilq101 on 2007-01-18
Thanks stalkier, however as I only have one hard drive on my laptop I am forced to take some of the windows partition and split the spare space into swap and root within an extended partition.  I need to know if there is a known problem with repartioning NTFS, as there is no indication of exactly why it won't resize the Windows partition and it seems to have nothing to do with Ubuntu itself.  I have never tried repartitioning my hard drive before, so I don't know if I should use any other programs to prepartition the hard drive before the Ubuntu installation?

---

### Post by neilq101 on 2007-01-18
Ok, thanks Darko, I'll do that when I'm back at my desktop.

---

### Post by riven0 on 2007-01-18
Also, if everything else fails, you can try repartitioning through Windows with [one of these free programs]("http://www.thefreecountry.com/utilities/partitioneditors.shtml"). 

Again, I have to add this didn't work for me; I tried partitioning with Partition Magic 8 on XP, and it constantly gave me errors. Still it wouldn't hurt to at least try it.

Best of luck, I know how frustrating it can be. :(

---

### Post by foofy on 2007-01-18
Sorry I haven't read through the whole thread, but if you can, try using only Ubuntu for a week and see if you can manage without Windows at all.  There are probably lots of alternative programs to the ones you use and if you're having trouble finding one just search or ask the forum and I'm sure there are lots of people here that can help you.

All the best with Ubuntu and Linux.  I hope you get many years of pleasure from it. :D

---

### Post by neilq101 on 2007-01-18
Ok, I ran the gparted app from the menu and it did indeed give me more information, which showed me that everything was ok up to:

'ERROR: Extended record needed (1048 > 1024), not yet supported!
Please try to free less space'

I assume this means that this app cannot take that much off one partition at once; could I just do 2 resizes? It seems very illogical that it can't partition that much, but...
I guess if i can't do it in stages I will have to use a 3rd-party app- NTFS Resize sounds pretty good...

---

### Post by riven0 on 2007-01-18
> **foofy said:**
> Sorry I haven't read through the whole thread, but if you can, try using only Ubuntu for a week and see if you can manage without Windows at all.  There are probably lots of alternative programs to the ones you use and if you're having trouble finding one just search or ask the forum and I'm sure there are lots of people here that can help you.

All the best with Ubuntu and Linux.  I hope you get many years of pleasure from it. :D

:lol: I'm sure he would, foofy, if he could get his hd partitioned. That's the problem here. :D

---

### Post by neilq101 on 2007-01-18
@ Foofy; I would quite like to ditch windows, but...games, inc. Call of Duty, UT2004, C&C Generals etc, WMP11 (heretical I know, but i like using it to sync with my mp3 in MTP mode) other compatibility issues i prob won't be able to or have time to sort out... I will never be able to.

I just tried resizing a smaller chunk of my NTFS partition....same outcome.  NTFS Resize then?

---

### Post by riven0 on 2007-01-18
> **neilq101 said:**
> Ok, I ran the gparted app from the menu and it did indeed give me more information, which showed me that everything was ok up to:

'ERROR: Extended record needed (1048 > 1024), not yet supported!
Please try to free less space'

I assume this means that this app cannot take that much off one partition at once; could I just do 2 resizes? It seems very illogical that it can't partition that much, but...
I guess if i can't do it in stages I will have to use a 3rd-party app- NTFS Resize sounds pretty good...

No, this was the exact same error I was getting before I ran chkdsk. Your hd is locked, I'm sure of it. :( 

On a second thought, have you tried looking through the BIOS? I know some laptop companies, like Lenovo, create a small partition for a Windows repair. This could sometimes cause problems, too. I know Thinkpad owners like me are recommended to delete these partition because problems may crop up later.

Anyway, it's something to try when you've got the time.

---

### Post by neilq101 on 2007-01-18
Ok, well i can quite easily believe my hard drive is locked, although I have seen many pages on the internets (from Google) reporting almost completely successful installs on my laptop- a Dell Inspiron 1300, Pentium M processor, and (so GParted tells me) a Samsung hard drive.
However, I have a main partition of 52.80gb and another partition taking 3gb, 2.31 of which is used, leaving 705.24mb free- I initially assumed this was for Windows, which it probably is, but does that sound familiar?  There is also 7.84mb unallocated for some reason.

---

### Post by neilq101 on 2007-01-25
AAAARRRRRGGGGHHH!

I have really screwed up my computer now; i used Symantec Partition Magic to try to repartition my hard drive, and it got as far as 100% complete, before reporting an error when trying to load the batch file, or something along those lines.  I made the complete n00b error of not writing down the message exactly, but when i pressed a key to get it to reboot, I got my first ever BSOD, which informed me that it had encountered a problem and shut down windows to prevent damage to my computer.  However, when rebooting again, I was asked to restart in safe mode, use last working settings etc; all options lead me to that screen again.  I have completely lost the ability to boot windows!  When loading gparted in Ubuntu, it shows that the drive is still partioned the same as previously, when Partition Magic was supposed to be taking around 5.5gb off the NTFS partition.  This was a pretty stupid thing to do in the first place, but does anybody know how I can get windows back? Am I going to need to obtain a recovery disk and reinstall Windows?

Neil

---

### Post by riven0 on 2007-01-25
Hey, I completely lost track of this thread! Good to see you back. :D 


Alright, the BSOD sounds like a bad one. I've gotten multiple BSOD's in my windows days, but never one that prevented from booting into windows after a restart. This sounds bad, and if you can't get into to safe mode, this will require a recovery disk, at the least. 

It's possible your master boot record was messed up, or at the very worst, your data is corrupted. Hopefully, you did a backup. :( 

See if you can get your hands on an XP cd. If your successsful,[ this is a good guide]("http://www.michaelstevenstech.com/XPrepairinstall.htm") to follow for a complete repair.

---

### Post by neilq101 on 2007-01-25
So it's as bad as I thought then... My friend has a install disc for XP Pro, but it'd probably not get past product activation as he is using it, so hopefully if I phone Dell they should send me one, that's what I've heard anyway.  I backed up all my important documents, but unfortunately-nay, tragically-I didn't have the materials to image my HDD, so I have lost about 5gb of music, a few game saves, and many installed programs.  Which is kind of why I shouldn't really have done it after gparted failed! I guess I can handle reinstalling Windows, but I am at a loss to why it crashed and what has happened; will I ever run linux?

---

### Post by neilq101 on 2007-01-30
w00t! I have installed Ubuntu and it's working great!  As my windows partition was basically dead if i used a repair disk, i thought i might as well delete it and replace it with half a smaller NTFS and half a ReiserFS-containing Edgy.  After some tweaking it worked, although i still haven't got my rescue disk so i don't know if DB is possible yet, but i won't miss it that much if i can sort my wireless out (broadcom chipset, which apparently = hell).  Should be manageable tho.  Thanks for all the help, shouldn't have to post in this thread again hopefully!

---

### Post by stalkier on 2007-03-20
I have had zero trouble repartitioning my HDD on my laptop. Currently I have no NTFS partition so... However, in the past I partitioned the 80gig NTFS into 3 partitions (NTFS, EXT3, and 512MB swap). If you have to use Cute Partition Manager. It is free. I hope this helps.

---

