---
title: "How to get rid of Ubuntu?"
date: 2005-07-21
forum: Absolute Beginner Talk
---

### Post by hoplouie on 2005-07-21
I´ve installed Ubuntu and I dont like it. It doesn´t work properly, and it is too slow.
Now I want to install Windows instead, but I cant. I´ve tried with 2 different windows CDs, but none of them starts running or installing when I put them in. 
I´ve also tried to run them in Ubuntu, but it doesnt work.
When I choose "shut down" in Ubuntu, it restarts and I have to take out the battery in my laptop to shut down the computer.

So how do I get rid of Ubuntu?

(I like the idea of free programs, but this one is crap)

/ Hop Louie, Sweden
 (i dont know how often i´ll be in this forum, so if you have the time and energy, could you mail a really good and helpful answer to [email]hop_louie@yahoo.se[/email]?)

---

### Post by poofyhairguy on 2005-07-21
[QUOTE=hoplouie]I´ve installed Ubuntu and I dont like it. It doesn´t work properly, and it is too slow.
Now I want to install Windows instead, but I cant. I´ve tried with 2 different windows CDs, but none of them starts running or installing when I put them in. 
[/QUOTE]

Well...sounds like you need to change your bios.

And reinstall Windows.

---

### Post by jatos on 2005-07-21
[QUOTE=poofyhairguy]Well...sounds like you need to change your bios.

And reinstall Windows.[/QUOTE]
 I would suspect you have become a victim of Ubuntu's annoying habit of mucking up your MBR. I have just posted a thread on this subject, which I will be giving you a link to, as soon as I find it.

EDIT:
heres the thread: [http://www.ubuntuforums.org/showthread.php?t=50693](http://www.ubuntuforums.org/showthread.php?t=50693)

Also you may want to try kubuntu ([www.kubuntu.org](www.kubuntu.org)), I  think its much better than ubuntu but make sure you install on a computer with a hard drive you don't need, also ubuntu uses gnome and kubuntu uses KDE, and its my OPINION that gnome is ****,  and KDE is the best thing since sliced bread.

---

### Post by codejunkie on 2005-07-21
[QUOTE=jatos]I would suspect you have become a victim of Ubuntu's annoying habit of mucking up your MBR. I have just posted a thread on this subject, which I will be giving you a link to, as soon as I find it.

EDIT:
heres the thread: [http://www.ubuntuforums.org/showthread.php?t=50693](http://www.ubuntuforums.org/showthread.php?t=50693)

Also you may want to try kubuntu ([www.kubuntu.org](www.kubuntu.org)), I  think its much better than ubuntu, because ubuntu uses gnome and kubuntu uses KDE, and its my OPINION that gnome is ****, but make sure you install on a computer with a hard drive you don't need.[/QUOTE]

well it's good that you like kubuntu and i do to, but it's basically the same distro as ubuntu except it uses kde as the desktop environment instead of gnome. and about ubuntu mucking up the mbr being the problem it's not. if the boot order is set correctly in the bios and the cd is bootable then it will boot from the cd installing grub to the mbr of the hard drive doesn't affect the boot order of the computer that is controlled by the bios.

---

### Post by benplaut on 2005-07-21
one could also truthfully say that it's Windows mucking up [K]Ubuntu's MBR  ;-)

---

### Post by codejunkie on 2005-07-21
[QUOTE=benplaut]one could also truthfully say that it's Windows mucking up [K]Ubuntu's MBR  ;-)[/QUOTE]
I agree ;-)

---

### Post by jatos on 2005-07-21
[QUOTE=codejunkie]I agree ;-)[/QUOTE]
 I can install Ubuntu after installing Windows, I have never had problems installing any OS after windows. But I cannot install anything other than Linux after Ubuntu on my hard drives which have had Ubuntu. This is quite a serious and valid problem, don't try to hide from it and it needs fixing ASAP. I may add I seem to remember when I installed knoppix, the first distro I ever tryed (before anyone says that knoppix is live only, I found an installer on the net), I had no problem returning to Windows with that hard drive.

---

### Post by GrootBrak on 2005-07-21
Hi sweetie. I had the same problem that windows "dissapeared" after I moved to LILO in stead of Grub. In the end I reinstalled Grub and then the original MBR re-appeared giving me the choice between Windows and Linux.

The problem is with windows. Even the XP rescue disk won't see the hard drives, but an Fdisk show it is there. Windows only want to see the disks if you partition and re-format a disk. Don't ask, I don't know either. But unless you partitioned and formatted over your original windows system, your MBR is still there. So don't run change disk info with Fdisk in windows. 

If you forcefully removed Ubuntu or Grub, insert your Ubuntu boot disk. Boot from it. Go straight to your partitioner, it will probably see the windows partition. If its there, you have lost nothing. Don't dispair. If you know about writing MBR's, go that way and get windows back. I still don't know a hoot about MBR, so I simply re-installed Ubuntu and had Ubuntu write the MBR. When firing up your PC, you should get a prompt asking you which sytem to load. Work from windows and then re-partition and format the Linux bit. That is to say if windows can see the Linux partition at all!!! Mine only see an "unusable" portion of disk, that's where Linux sits. Partition it to NTFS or whatever, and format it.

Hope it works for you.

BTW. I have lots of problems in a short period of time with Ubuntu/Linux. But it is solvable free of charge. Sometime from this forum, many time not. But do yourself a favour. Ask the sweet people that give MS support. The bit they give you free is quoted verbatim from the help files, the other bit you pay for, and it won't work. I still have my original problems, engineered around, but still there lurking in the background. The favorite line is after hours of trying is, Why don't you re-install Windows? Yeah right.

---

### Post by codejunkie on 2005-07-21
[QUOTE=jatos]I can install Ubuntu after installing Windows, I have never had problems installing any OS after windows. [COLOR=SlateGray]But I cannot install anything other than Linux after Ubuntu on my hard drives which have had Ubuntu. This is quite a serious and valid problem, don't try to hide from it and it needs fixing ASAP[/COLOR]. I may add I seem to remember when I installed knoppix, the first distro I ever tryed (before anyone says that knoppix is live only, I found an installer on the net), I had no problem returning to Windows with that hard drive.[/QUOTE]

Installing ubuntu on your hard drive doesn't lock it down to only ubuntu or linux, all you have to do is delete or resize the linux partition that you created on that hard drive and create a windows partition and install windows. and the only thing that i said is the grub being installed on the MBR of a Hard Drive, has nothing to do with a cd not being able to boot and it doesn't it's controlled by the bios.

---

### Post by jatos on 2005-07-21
[QUOTE=codejunkie]Installing ubuntu on your hard drive doesn't lock it down to only ubuntu or linux, all you have to do is delete or resize the linux partition that you created on that hard drive and create a windows partition and install windows. and the only thing that i said is the grub being installed on the MBR of a Hard Drive, has nothing to do with a cd not being able to boot and it doesn't it's controlled by the bios.[/QUOTE]

On the hard disk that I installed Linux I did try deleting all the partitions, I tryed quite a few other things, whatever happened I could not get rid of the MBR that grub put there. I tryed every nearly every trick I could think to get the disk to run windows again, frankly I should have this much trouble restoring Windows after installing Linux.

I have also had several other problems, all the root cause of GRUB. Most notable of my other problems is that I some very minor changes to my HD configuration have stopped GRUB from booting.

---

### Post by codejunkie on 2005-07-21
[QUOTE=jatos]On the hard disk that I installed Linux I did try deleting all the partitions, I tryed quite a few other things, whatever happened I could not get rid of the MBR that grub put there. I tryed every nearly every trick I could think to get the disk to run windows again, frankly I should have this much trouble restoring Windows after installing Linux.

I have also had several other problems, all the root cause of GRUB. Most notable of my other problems is that I some very minor changes to my HD configuration have stopped GRUB from booting.[/QUOTE]

on a normal hard drive that's not a problem, you might have some bad sectors on it or a drive going bad. I'm just saying that this is not something that ubuntu intentionally does locking down your hard drive so you cant reinstall windows or another OS. try autoclave [http://staff.washington.edu/jdlarios/autoclave-discontinued/](http://staff.washington.edu/jdlarios/autoclave-discontinued/) this is a great product that helps a great deal in cases like yours it will completely erase all data on the disk sector by sector this will completely erase the whole hard drive making it just like a new disk, or [http://ultimatebootcd.com/](http://ultimatebootcd.com/) it's a bootable cd with autoclave and tons of other tools for repairing any PC problem these might help.

---

### Post by jatos on 2005-07-21
I very much doubt whether the problem was caused by any delliberate act to lock down my HD, as far as I can see its just a bug, but one that you can't afford to have in the OS. Though I will say this a problem I had with Warty, and I haven't tryed restoring my HD after Hoary. 

One thing though, thanks for showing me that app, I will at some test on this hard disk to see if it fix's the problem. I might add, I have delibrately installed hoary on the hard disk of mine that I could get GRUB off, and Windows is currently installed my other hard disk.

To the developers: Please don't take attitude problem fixed and forget about the problem. Other users may have this prob so you may want to look into this prob and try and fix it.

---

### Post by codejunkie on 2005-07-21
[QUOTE=jatos]I very much doubt whether the problem was caused by any delliberate act to lock down my HD, as far as I can see its just a bug, but one that you can't afford to have in the OS. Though I will say this a problem I had with Warty, and I haven't tryed restoring my HD after Hoary. 

One thing though, thanks for showing me that app, I will at some test on this hard disk to see if it fix's the problem. I might add, I have delibrately installed hoary on the hard disk of mine that I could get GRUB off, and Windows is currently installed my other hard disk.

To the developers: Please don't take attitude problem fixed and forget about the problem. Other users may have this prob so you may want to look into this prob and try and fix it.[/QUOTE]

it's aggravating yes but not a bug with Linux or ubuntu it could have happened with windows, its happened to me in windows where i couldn't write data to a part of the hard rive when that happens you just have to zero out the drive, repartition it, and format it most of the time that fixes it, unless the drive is physically damaged.

---

### Post by dcraven on 2005-07-21
Why are issues involving Linux and Windows immediately attributed to Linux? Windows does/doesn't do many things intentionally so that it can't play nicely with other operating systems. I don't mind people moaning and complaining.. I do it plenty too. Just be cautious about who you are pointing at.

~djc

PS: I hope you get the problem figured out and fixed. Good luck :D

---

### Post by hoplouie on 2005-07-22
Hm... I still dont get it. You´re using some words I didnt know existed.
I have to admit the windows I desperatly want back is a pirate copy one. I have a disk with windows 2000 and one with windows xp, none of them work. I´ve got deamon tools too, but I cant get any .exe-files running in this crappy Ubuntu. I just want windows back. Could someone write a simple, step to step understandable guide in how to kick Ubuntu out and windows in? I´d be very happy.

---

### Post by jatos on 2005-07-22
[QUOTE=hoplouie]Hm... I still dont get it. You´re using some words I didnt know existed.
I have to admit the windows I desperatly want back is a pirate copy one. I have a disk with windows 2000 and one with windows xp, none of them work. I´ve got deamon tools too, but I cant get any .exe-files running in this crappy Ubuntu. I just want windows back. Could someone write a simple, step to step understandable guide in how to kick Ubuntu out and windows in? I´d be very happy.[/QUOTE]
 1: Use that autoclave program codejunkie is referring to
2: Locate you windows CD, reboot into windows setup
3: Setup windows and you should be finished.

---

### Post by codejunkie on 2005-07-22
[QUOTE=jatos]1: Use that autoclave program codejunkie is referring to
2: Locate you windows CD, reboot into windows setup
3: Setup windows and you should be finished.[/QUOTE]

They don't want to use that autoclave program if they have anything that they want to keep because it will completely erase everything i mean everything. the only time you should use that app is don't have anything to worry about keeping or you have backed up everything.

---

### Post by hoplouie on 2005-07-22
I have nothing to fear, I have saved all my good stuff on my 250 GB extrernal harddrive. I´ll try that programme, but when I´ve tried to run programmes in Ubuntu there is always a error message and the programme doesnt run.

---

### Post by codejunkie on 2005-07-22
[QUOTE=hoplouie]Hm... I still dont get it. You´re using some words I didnt know existed.
I have to admit the windows I desperatly want back is a pirate copy one. I have a disk with windows 2000 and one with windows xp, none of them work. I´ve got deamon tools too, but I cant get any .exe-files running in this crappy Ubuntu. I just want windows back. Could someone write a simple, step to step understandable guide in how to kick Ubuntu out and windows in? I´d be very happy.[/QUOTE]

OK i need a little info from you, what kind of computer you have, the model number and the manufacture how many hard drives you have and what hard drive you installed ubuntu on. and if your trying to get windows back on there without reinstalling/overwriting everything  tell me a little bit about how you installed ubuntu for instance did you tell the ubuntu installer to use the whole hard drive or just free-space.

---

### Post by codejunkie on 2005-07-22
[QUOTE=hoplouie]I have nothing to fear, I have saved all my good stuff on my 250 GB extrernal harddrive. I´ll try that programme, but when I´ve tried to run programmes in Ubuntu there is always a error message and the programme doesnt run.[/QUOTE]

OK now that i know that your not trying to save anything put your windows xp cd in reboot the computer when it starts booting a message will appear saying press any key to boot from the cd when you first see this message you have about five seconds to press a key on the keyboard or it will boot from your hard drive from here it will walk you through an installer you have to choose a hard drive to install to and it will pretty much do the rest for you. if you have any more trouble let me know whats happening and ill try to help you.

---

### Post by hantms on 2005-07-22
> I still dont get it. You´re using some words I didnt know existed.

Yes, I tend to agree that the replies so far aren't too clear..  Let me try :

The reason so many responders go all techno is because they assume you actually still have Windows installed, but you simply cannot access it anymore.  Is this the case, or do you just want to completely get rid of everything and anything that's currently on your computer and start afresh with a clean new Windows installation?

If that's the case then you're in luck, 'cause it's easier. :)  Also because it means it has nothing to do with Ubuntu anymore, you're at a point where you have a virgin but currenly comatose computer and just want to put Windows on.

INSTALLING WINDOWS:

Normally, when you insert a Windows installation disk and turn the computer on, the computer will start up from the CD, initially displaying some blue screens with instructions.

If this doesn't happen, then chances are your basic basic hardware settings are set to not try to start from CD.  These basic basic hardware settings are called "BIOS", though for today you can call it anything. :)  Different computers have various ways of getting into those BIOS settings but it invariably involves pressing some specific key when you first turn on your computer. Often a message is displayed saying which key to press.  Often this is the DEL key.  Another common one is the F10 function key, or F2.   Try it. 

Once in the BIOS you have to look for the part where you select which disk is used to try to start the system.  Often this is called 'Boot', 'Boot sequence', 'Boot priority', 'Boot device', so in short something that seems footware related.  (Boot means 'startup', God knows why we don't just use 'start'. I guess that'd be too easy or something)

Anyway, when you locate that setting then you need to make sure that your CD-ROM is higher up in the list of disks to try than your main harddisk. Your computer starts whatever device is at the top of the list first, so if this is your harddrive and your harddrive is dead or runnign Ubuntu then you will not get to installing Windows from CD.  So you'd make your CD-ROM first, floppy second and harddisk third.

Save your BIOS settings. This is often F10, or go through the menu system to save and exit. Restart computer, making sure your Windows CD is in the drive.  

Now then: 

OPTION ONE : For a clean virgin install you'd want to wipe everything off and reformat the whole thing. The Windows installer takes you through the steps.  **NOTE AGAIN** this will completely wipe out anything you had on that disk, so Ubuntu will be kicked off, along with ALL OTHER FILES and PROGRAMS you may have had in Windows before trying Ubuntu. 

OPTION TWO: If you did still have WIndows on here like all other respondents thought then you wouldn't reformat everything, but just get to where you can do a 'Repair', where you'd go into the repair console.  There you'd type "FIXMBR" and press Enter. Then you'd type "FIXBOOT" and type enter.  Then you pray while taking out the CD and restarting the computer. :)

Good luck.. .:)

By the way... Installing Ubuntu went a lot smoother than installing Windows, wouldn't you say?  \\:D/

---

### Post by jsimmons on 2005-07-22
[QUOTE=hoplouie]Hm... I still dont get it. You´re using some words I didnt know existed.
I have to admit the windows I desperatly want back is a pirate copy one. I have a disk with windows 2000 and one with windows xp, none of them work. I´ve got deamon tools too, but I cant get any .exe-files running in this crappy Ubuntu. I just want windows back. Could someone write a simple, step to step understandable guide in how to kick Ubuntu out and windows in? I´d be very happy.[/QUOTE]

You can't run Windows programs under Linux unless you've installed a Windows emulator (like Wine, or Crossover Office), and even then, some of your Windows apps simply might not be compatible.

If you want Windows back, first go out and buy a legal copy.  During the Windows install, it will give you the opportunity to remove all existing partitions.  Do that, and then use the entire hard drive for Windows.

If all else fails, donate your computer (hopefully, you didn't steal that like you did Windows) to a charitable organization, and find something else to do with your time.

---

### Post by hoplouie on 2005-07-22
Im trying to download that programme that erases everything to a disc now.
I really hope it will work.

jsimmons, why would I buy a legal copy of windows when I can get if for free? Im unemployed, and I honestly think Bill Gates will be able to eat tonight even if I dont give him my money.

---

### Post by dcraven on 2005-07-22
[QUOTE=hoplouie]
jsimmons, why would I buy a legal copy of windows when I can get if for free? Im unemployed, and I honestly think Bill Gates will be able to eat tonight even if I dont give him my money.[/QUOTE]

Ugh.. My interest in this thread quickly evaporated.

~djc

---

### Post by hoplouie on 2005-07-22
Thanks a lot hantms, I understood that. 

I made everything you said, went into the bios and the CD Rom was in the top of the list... but still this Ubuntu-nightmare keeps starting up instead of the windows thing. ](*,)

---

### Post by damonw5 on 2005-07-22
[QUOTE=hoplouie]Thanks a lot hantms, I understood that. 

I made everything you said, went into the bios and the CD Rom was in the top of the list... but still this Ubuntu-nightmare keeps starting up instead of the windows thing. ](*,)[/QUOTE]
 Maybe your problem is not with "this Ubuntu-nightmare" but with your PIRATED copies of Windows which aren't working properly.

Try a real copy that you have obtained LEGALLY and tell us if that works.

By the way, why would you steal when the best things in life are free?

The reason we like Ubuntu is that we can obtain it legally for free (as in beer), it is free (as in "libre") and it doesn't run most Windows programs such as spyware, adware, malware, viruses, etc. It doesn't support Bill Gates and yet it is one of the best operating systems around.

But if you want to go back to Windows, seriously get a non-pirated copy that works.

---

### Post by Jussi Kukkonen on 2005-07-22
[QUOTE=hoplouie]
jsimmons, why would I buy a legal copy of windows when I can get if for free?[/QUOTE]

This far to the thread I was actually thinking of trying to help you out... Not interested anymore.

I'm not trying to offend, just wanted to let you know of a downside to illegal copying (since it seemed like you couldn't think of one).

---

### Post by WirelessMike on 2005-07-22
It sounds as though the Windows installer is detecting no free space on which to install.  This isn't a bug if you actually installed an OS on the harddrive.  As you said, there is an mbr on the drive, so if the mbr isn't reconfigured or the existing install removed completely, Windows will recognize nothing to install on.

The space on the disk to which you installed an OS is called a partition.  Partitions can be resized, copied, or erased.  If you wish to get rid of what's currently on the disk to make it blank and therefore recognizable as a clean slate on which Windows will make its own partition, you need to erase the existing partition.  If you wish to install Windows in addition to what is already installed, you need to resize the partition to leave a blank space for Windows to recognize.  If you wish to make a snapshot of everything on the harddrive in order to put it on a different harddrive and use the old drive for Windows, you need to copy the existing partition to a dvd or blank space and erase the original afterwards.

Some free software that will allow you to do this is [QTParted](http://qtparted.sourceforge.net/) and [PartImage](http://www.partimage.org/).  You can find these apps in a live Gentoo cd called ["SystemRescueCD"](http://www.sysresccd.org/).  It will require a little reading and probably some experimentation to use the tool if you're unfamiliar with partitions, but the tool works fine and doesn't cost anything.

If you're willing to pay for a tool that is much easier to use and graphical, get [Partition Magic](http://www.symantec.com/partitionmagic/) from Symantec (they bought PowerQuest, the original maker of Partition Magic).

I certainly won't be a part of any how-to or step-by-step that will include the installation of a pirate copy of any OS, Windows included, but I don't mind helping to identify the original problem, though I've added little that hasn't already been mentioned in this thread.

Again--  The nature of partitions and mbrs on partitions are not OS bugs.  This is simply how an OS is put on to a harddrive and how that harddrive knows what to do when you power it on.  You would think a foreign OS (such as that on an install cd) would recognize that there is an OS already installed and offer to wipe it out and install itself...  Why Windows is refusing to do this, I don't know, but I concur that it may have something to do with the nature of your version of Windows, and further that you'll find little support for discovering inadequacies in illegal versions of legitimate software.

A legitimate copy may make all the above completely unnecessary.  At the very least, if it still doesn't work, you'll have official MS support to MAKE it work.

---

### Post by poofyhairguy on 2005-07-22
I won't lecture you about piracy, but I will tell you that your problem rest in the bios. You HAVE to figure out how to get your computer to boot from a CD on your own.

We can't help, every computer is different. After you do that, Windows should install if that pirate CD you have is any good.

If then it does work....the problem is your Windows CD.

Not to offend.....but....how did you get Ubuntu on there in the first place? Your level of technical knowledge seems below the minimum needed to install Ubuntu.

Again...the bios.

---

### Post by poofyhairguy on 2005-07-22
[QUOTE=WirelessMike]It sounds as though the Windows installer is detecting no free space on which to install.  This isn't a bug if you actually installed an OS on the harddrive.  As you said, there is an mbr on the drive, so if the mbr isn't reconfigured or the existing install removed completely, Windows will recognize nothing to install on.

The space on the disk to which you installed an OS is called a partition.  Partitions can be resized, copied, or erased.  If you wish to get rid of what's currently on the disk to make it blank and therefore recognizable as a clean slate on which Windows will make its own partition, you need to erase the existing partition.  If you wish to install Windows in addition to what is already installed, you need to resize the partition to leave a blank space for Windows to recognize.  If you wish to make a snapshot of everything on the harddrive in order to put it on a different harddrive and use the old drive for Windows, you need to copy the existing partition to a dvd or blank space and erase the original afterwards.

Some free software that will allow you to do this is [QTParted](http://qtparted.sourceforge.net/) and [PartImage](http://www.partimage.org/).  You can find these apps in a live Gentoo cd called ["SystemRescueCD"](http://www.sysresccd.org/).  It will require a little reading and probably some experimentation to use the tool if you're unfamiliar with partitions, but the tool works fine and doesn't cost anything.

If you're willing to pay for a tool that is much easier to use and graphical, get [Partition Magic](http://www.symantec.com/partitionmagic/) from Symantec (they bought PowerQuest, the original maker of Partition Magic).

I certainly won't be a part of any how-to or step-by-step that will include the installation of a pirate copy of any OS, Windows included, but I don't mind helping to identify the original problem, though I've added little that hasn't already been mentioned in this thread.

Again--  The nature of partitions and mbrs on partitions are not OS bugs.  This is simply how an OS is put on to a harddrive and how that harddrive knows what to do when you power it on.  You would think a foreign OS (such as that on an install cd) would recognize that there is an OS already installed and offer to wipe it out and install itself...  Why Windows is refusing to do this, I don't know, but I concur that it may have something to do with the nature of your version of Windows, and further that you'll find little support for discovering inadequacies in illegal versions of legitimate software.

A legitimate copy may make all the above completely unnecessary.  At the very least, if it still doesn't work, you'll have official MS support to MAKE it work.[/QUOTE]


Windows can do this itself. Well....my official copy can...

---

