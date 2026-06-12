---
title: "help I screwed up really really bad"
date: 2007-12-23
forum: Absolute Beginner Talk
---

### Post by Mattevt on 2007-12-23
Oh my god I'm such a moron. I need so much help. I partitioned my disk wrong when installing ubuntu and like a moron I didn't back anything up...I thought I would be able to mount my windows files to linux. Now I can't even get back to windows. If I restart the computer it shows the XP screen then it says that the disk chk is missing and it reboots and just cycles like that. I have to put in the ubuntu cd I made and load ubuntu (which is still not fully installed). All I really want is to just get back into windows which I know my way around. I know nothing about linux and just wanted to try something new. If I can't get back to windows how can I import my windows files to linux. I'm mainly just worried about my music. I feel that my sandisk sansa view is not compatible with linux which means I'm screwed.

If I could just get back to windows I could probably fix it. please help. if someone wants to call me at night (eastern time) and walk me through it. 802-233-9288. Just please...please I'm dying here.

*edit: I'm not turning off my computer until I figure a way to fix this. I'm leaving firefox open so I don't have to continue to go through using the disc to boot.

---

### Post by perlluver on 2007-12-23
If you have the XP disk, run the recovery mode off the disk.  If not then you will have to fix the partition for Ubuntu.

---

### Post by shareMenaPeace on 2007-12-23
Does the windows partition is mounted when you run the live cd?

Even if not maybe there are ways ...

---

### Post by Mattevt on 2007-12-23
I try to hit f10 when rebooting and it doesn't do anything. I can probably find an xp disk. How do I fix the partition for ubuntu?

---

### Post by perlluver on 2007-12-23
To fix the partition for Ubuntu, you have to go through the install, have it use at least 15GB all together, and make sure grub sets up properly.  If grub does not set up you will not be able to get into, Ubuntu or Windows.

By the way I thought it to be F8, to load safe mode, and other Windows options?

---

### Post by mLes-_- on 2007-12-23
just boot in ubuntu and find your HDD with your windows partition.  Take all your files you need and back them up to an external.  Then use an XP disc to repartition and reinstall.

---

### Post by Sef on 2007-12-23
Also check out [Test Disk]("http://www.cgsecurity.org/wiki/TestDisk").

---

### Post by Mattevt on 2007-12-23
> **mLes-_- said:**
> just boot in ubuntu and find your HDD with your windows partition.  Take all your files you need and back them up to an external.  Then use an XP disc to repartition and reinstall.
[B]
Okay, this sounds good. How do I do this.[/B]


f10 is system recovery i haven't tried safe mode.

I should probably admit I'm not a computer person. I just like them and I wanted to try linux. I'm in way over my head. I'd like to try the test disk but honestly I'd have no idea what to do with it. I have access to another computer now so I can reboot and try different things if needed. thanks for the help.

*Edit I tried to reboot in safe mode. I got this error message: "Setup cannot load keyboard layout file kbdus.dll" and I have to restart the computer.

---

### Post by Sabar on 2007-12-23
Just load your Ubuntu CD into the computer. Run off of live CD and using the Live CD dig around the hard drive and take everything off you want. Either burn to disk or move to thumb drives. 

After that reinstall windows. if you are still curious about Ubuntu save 15-20 gigs of drive unalocated and install Ubuntu in there.

Good luck I hope this works for you
Sabar
Trust me I was in your shoes before ( oh crap now what did I do?)

---

### Post by CCNA_student on 2007-12-23
Run Ubuntu off of the CD. You should be able to see the Partition with Windows XP, it might show up on the desktop as hda1, and copy files from that onto say, a flash drive. If this is a desktop and you have two drive, one a CD/DVD burner and the other a CD/DVD-ROM you could boot of of the Ubuntu disc from the ROM drive and write the files to a CD in the other drive if you have that many files to back up. I hope that this helps you.

       Sin Cere,

       CCNA

---

### Post by Mattevt on 2007-12-23
> **Sabar said:**
> Just load your Ubuntu CD into the computer. Run off of live CD and using the Live CD dig around the hard drive and take everything off you want. Either burn to disk or move to thumb drives. 

After that reinstall windows. if you are still curious about Ubuntu save 15-20 gigs of drive unalocated and install Ubuntu in there.

Good luck I hope this works for you
Sabar
Trust me I was in your shoes before ( oh crap now what did I do?)

Okay thanks. Although I don't know linux at all. I feel I could do this with guidance. How do I access the hard disk, how do I find my windows files, then how do I burn them to a cd in linux.

thank you!!!

*edit: okay I think I just need to know how to find the partition with my windows files and access them.

---

### Post by CCNA_student on 2007-12-23
If your Windows XP partition is still relatively unharmed after booting off of the Ubuntu CD 
you should see something on the desktop that says something like, hda1, and that should be your partition. Just click on that drive and start copy and pasting files to a flash drive or burn them to a CD. In Ubuntu to simply burn files look at "Places" on the top and you should see CD/DVD creator. I hope that this helps you.

        Sin Cere,

        CCNA

---

### Post by Mattevt on 2007-12-23
> **CCNA_student said:**
> If your Windows XP partition is still relatively unharmed after booting off of the Ubuntu CD 
you should see something on the desktop that says something like, hda1, and that should be your partition. Just click on that drive and start copy and pasting files to a flash drive or burn them to a CD. In Ubuntu to simply burn files look at "Places" on the top and you should see CD/DVD creator. I hope that this helps you.

        Sin Cere,

        CCNA


all that is on my desktop is "examples" and "install". i'll try elsewhere for hda1
 thanks

---

### Post by CCNA_student on 2007-12-23
Try going to Places>Computer and look for your Windows partition there. 

        Sin Cere,

        CCNA

---

### Post by mc4man on 2007-12-23
If your headed towards reinstalling xp your're gonna need to find the disk so it.s worth a try restoring the mbr. You'd insert the xp disk, reboot, let windows run it's little setup and then at the screen elect option  - ....recovery console type r. Do that and at the prompt type fixmbr. This may give you back xp like nothing happened.

edit: if you can't find the disk there are ways with xp to get to the recovery console, post if needed

---

### Post by Mattevt on 2007-12-23
> **CCNA_student said:**
> Try going to Places>Computer and look for your Windows partition there. 

        Sin Cere,

        CCNA


I did this every drive I double clicked came up with an error message: "unable to mount..."

Do I have to do a full install. I thought I already had but apparently I didn't.

everything in linux is running very slowly too.

---

### Post by Mattevt on 2007-12-23
> **mc4man said:**
> If your headed towards reinstalling xp your're gonna need to find the disk so it.s worth a try restoring the mbr. You'd insert the xp disk, reboot, let windows run it's little setup and then at the screen elect option  - ....recovery console type r. Do that and at the prompt type fixmbr. This may give you back xp like nothing happened.

edit: if you can't find the disk there are ways with xp to get to the recovery console, post if needed

This sounds great...except

I realized that we don't have xp disks for the computers. just recovery disks. My computer ignores them now. I hit f10 for system recovery, But the computer acts as if I didn't press anything when I hit do.

---

### Post by CCNA_student on 2007-12-23
The reason it ran slowly is that your are running Ubuntu off of the CD right? You looked where I told you to and it said it could not mount? Try right clicking on the drive that looks most like you Windows partition and tell us what it says or post a screenshot. 

         Sin Cere,

         CCNA

---

### Post by Mattevt on 2007-12-23
> **CCNA_student said:**
> The reason it ran slowly is that your are running Ubuntu off of the CD right? You looked where I told you to and it said it could not mount? Try right clicking on the drive that looks most like you Windows partition and tell us what it says or post a screenshot. 

         Sin Cere,

         CCNA

I tried to right click and it said the same thing. In fact the partition I saw was titled 46.8gig and I think it was sda3. Nothing in    Places > Computer    looks like a partition with stuff I want.:confused:

---

### Post by califman831 on 2007-12-23
Not to sound like a jerk but when doing any major changes using whatever operating system

[SIZE="7"]
BACKUP
BACKUP
BACKUP![/SIZE]

---

### Post by CCNA_student on 2007-12-23
From what you are saying your partition is now unreadable. If you have another hard disk with an OS on it you could boot from that and copy files from the Windows XP partition, other than that I have nothing left that can help you. Good luck.

       Sin Cere,

       CCNA

P.S: My Linux blog is a good place to learn about Linux and how to get it working.

---

### Post by Mattevt on 2007-12-23
I know. I heard that I could just install the two OS's side by side. I had no idea that it would be this complicated. I'll never make this mistake again.

---

### Post by CCNA_student on 2007-12-23
Actually it is very simple. I have dual boot with Windows XP and Ubuntu 7.10 on my desktop. I meant that if you had another hard disk that you could boot off of that. If you can, please try it.

        Sin Cere,

        CCNA

---

### Post by Mattevt on 2007-12-23
I was speaking to the person who was telling me that backing up is of utmost importance. I don't know how to boot off of another hard disk, so I'm going to guess that this is not the case for me.

If mc4man is unable to tell me how to access system recovery with out a disk I think I'll just try to rebuild my computer around linux.

---

### Post by Ertai87 on 2007-12-23
lol I did the same thing when I used Ubuntu the first time (this is currently my 3rd time using Ubuntu).  Basically you have to complete the install (go back and finish using the Live CD).  Once that's done, the GRUB menu will come up.  It should give you the choice of booting into Windows or Linux.  If you no longer want to use Linux at all, here's what I did to solve the problem:

1) Boot into Windows (the Linux GRUB should let you do this).  Install the Windows Recovery Console (there are instructions on support.microsoft.com).  Run fixmbr from recovery console.  This will erase the Linux GRUB and make your comp boot by default into Windows (note you will be unable to boot to Linux after doing this without reinstalling, so be sure you really want to do it)

2) Use a program like Partition Magic to reformat your Linux swap and re-add it to your Windows partition.  Note that you can't repartition the Windows C: drive while it's booted, so you might need a Partition Magic boot CD to do this.  You can try using the GParted app on the Linux boot disk, but I had issues with this when I did it, causing me to have to reformat, so I suggest Partition Magic if you can get your hands on it.

After doing that, your comp should be back to normal.

If you just want to access your Windows files in Linux, you can mount your Windows partition as a data drive.  I forget how to do it, but it is doable (I did it before once when I erased the Windows boot information from my Linux Grub and thought I erased my Windows partition by accident).

Good luck!

---

### Post by Mattevt on 2007-12-23
> **Ertai87 said:**
> lol I did the same thing when I used Ubuntu the first time (this is currently my 3rd time using Ubuntu).  Basically you have to complete the install (go back and finish using the Live CD).  Once that's done, the GRUB menu will come up.  It should give you the choice of booting into Windows or Linux.  If you no longer want to use Linux at all, here's what I did to solve the problem:

1) Boot into Windows (the Linux GRUB should let you do this).  Install the Windows Recovery Console (there are instructions on support.microsoft.com).  Run fixmbr from recovery console.  This will erase the Linux GRUB and make your comp boot by default into Windows (note you will be unable to boot to Linux after doing this without reinstalling, so be sure you really want to do it)

2) Use a program like Partition Magic to reformat your Linux swap and re-add it to your Windows partition.  Note that you can't repartition the Windows C: drive while it's booted, so you might need a Partition Magic boot CD to do this.  You can try using the GParted app on the Linux boot disk, but I had issues with this when I did it, causing me to have to reformat, so I suggest Partition Magic if you can get your hands on it.

After doing that, your comp should be back to normal.

If you just want to access your Windows files in Linux, you can mount your Windows partition as a data drive.  I forget how to do it, but it is doable (I did it before once when I erased the Windows boot information from my Linux Grub and thought I erased my Windows partition by accident).

Good luck!

Wow I was just about to delete everything and just rebuild with linux. Now how do I properly do this partition thing. I'm in the manual partitioner I have three partitions.

/dev/sda1  !  fat3   6gb
/dev/sda2     ntfs   136.72             used 122.45           unused 14.27
/dev/sda3     ext3   43.59              used 829.14mb      unused 42.78

What do I do from this screen


thanks.

---

### Post by CCNA_student on 2007-12-23
Install Ubuntu on the partition that is formatted for ext3. Create a linux swap file too.

    Sin Cere,

    CCNA

---

### Post by mc4man on 2007-12-23
you need a blank cd and access to burner
[http://www.webtree.ca/windowsxp/repair_xp.htm](http://www.webtree.ca/windowsxp/repair_xp.htm)
a 7.5mb boot iso that will get you to console in about 20 sec.
fully tested by me a few min. ago

about 20 lines down on page

---

### Post by Ertai87 on 2007-12-23
To be honest, I don't remember the step-by-step process (plus it's different depending on which partitioning app you use), but basically this is the idea: In order to boot, you need a boot loader.  From what it sounds like to me, you've screwed something up in your boot loader.  As such, you need to reset your boot loader.  This means, for as much as I know, you have to install an operating system and boot to it.  The Linux Grub is good in that it'll auto-recognize not only itself but other OSes as well.  The Windows boot loader only recognizes Windows (as far as I know).  Thus, you want to partition your drive and install Linux, which will let you boot to Windows, then boot to Windows and reset your master boot record (using fixmbr) to erase the Linux boot information, and then format the Linux partition and re-add the space to the Windows partition.  It sounds to me like you've already partitioned and started to install Linux, but that crashed somewhere, so you have to finish the install first.  I don't know which of your partitions is which, but I would guess that the ntfs one is the Windows partition and the ext3 one is either the Linux swap or an extension partition for Windows (if it's an extension partition then when you used to use Windows you should have seen a C: and D: drive; otherwise it's probably the Linux swap).  If it's the Linux swap, then install Linux to that and then run the fixmbr etc. and it should work.  Sorry I can't be of any more help than that :(

---

### Post by Mattevt on 2007-12-24
if I try to install on sda3 and I use sda2 as a swap it says that it found an error and I could either continue or go back. I went back. Any ideas on this.

okay...i have a lot of info here. I'm going to go to bed and deal with this in the morning when my head is more clear. Please feel free to load this thread with as much info as you care to give me. I really appreciate all the help. If all else fails I'll just reformat the entire disk and rebuild my computer life in linux. between my brother and I we have about 20-25 gigs of music of the 40 that was on the computer...It'll suck to lose the movies I had though. can winamp run in linux...what about portable mp3 players ( have an 8 gig sansa view)

---

### Post by Ertai87 on 2007-12-24
The drive you install on, I believe, *is* the Linux Swap.  "Linux Swap" is just a name for "drive formatted for Linux".  Here's what I suggest:

Run the Live CD.  Using the "Install" app, reformat the ext3 partition by deleting the partition table entry for that partition and recreating it, and then install Linux on that.  DO NOT touch the ntfs partition.  If you start to screw with that, you could wind up with more problems than you already have.  Let Linux install on that partition (just do whatever the installer asks you to do; it's pretty user-friendly).  Then everything should work as I said.

After getting to boot to Windows, I suggest taking all your important files (docs, music, movies, etc.) and back it up to an external HD to make sure this doesn't happen again.  Then, if you want to be extra-sure everything works properly, you might want to format.  The format isn't strictly necessary, but I had partition table issues after I uninstalled Linux the first time (which is why I recommend against GParted).  Formatting Windows is a bit of a pain in the butt though, so only do that if you think there are potential issues.

As for Winamp, I don't believe it runs on Linux (hence the "Win" part, as in "Windows"), but Linux has plenty of media players.  MPlayer is decent enough for music, but rumour has it Amarok works with iPod (and thus I would presume your mp3 player as well, although I could be wrong).  Don't ask me how, though; I haven't got it set up yet on my system.  If you want a good video media player, I recommend VLC (aka VideoLAN).  Totem is a pain in the butt to use properly, and MPlayer I found even more so.

---

### Post by Mattevt on 2007-12-24
Okay I reinstalled windows but now when I try to logon I get the error message:

"The specified domain either does not exist or could not be contacted"

I can't get past the logon screen.

I tried booting with the xp disk then accessing the user controls using shift+f10 to get to the command prompt. I removed the password but I still got the same error message.

---

### Post by mc4man on 2007-12-24
you may have a corrupted sam (Security Account Manager ) which could prove problematic with an oem installation. if you want some liinks for possible solutions post though your best bet now would be to procedd with re- installing ubuntu. There's a slight possibility if you can boot up to safe mode you can access windows - it's usually pressing f8 while booting (no disks in drive)

---

### Post by Mattevt on 2007-12-24
so theres a possibility that windows is no longer an option on my computer? I guess there are worse things...as long as I can get ubuntu up and running.

safe mode is inoperable.  

send me those links...if that doesn't work I'll go along with ubuntu and relearn computers all over again. Would anyone be willing to walk me through the installation of ubuntu step by step. 

thanks guys for your attention and assistance.


*I was able to get XP pro. The only thing is I now only have 130 gigs of space....I missing about 70 gigs. I lost everything and I have to rebuild from scratch. I'm due for a new computer this summer when that comes I'll use this computer to become versed in linux. what a wild ride.

Thanks for all of your insight. I no longer have the desire to be a computer poseur. I'll leave that to the people who know what they are doing.

---

### Post by mc4man on 2007-12-25
when you reformatted you probably didn't delete the partition(s) that ubuntu had created. 
 You can use the disk management tool in xp to reclaim the space as an add. drive (partition) 
[http://www.mcmcse.com/windows_xp/guides/diskmanagement.shtml](http://www.mcmcse.com/windows_xp/guides/diskmanagement.shtml)
read thru before acting

---

### Post by Yoke &amp; Chung on 2007-12-25
> **Mattevt said:**
> 

Thanks for all of your insight. I no longer have the desire to be a computer poseur. I'll leave that to the people who know what they are doing.

If you just want to copy your data, you can remove the hard disk and install that into a friend's PC, see if can recover any data from there.

The OS may be corrupted, but data could remain unscath.

---

### Post by Bartender on 2007-12-25
I agree with Yoke.  It appears to me that you're way out into areas which are not familiar, where you're likely to keep doing more damage.

Did you reformat the entire HDD?  Or do you still have this:

/dev/sda2 ntfs 136.72 used 122.45 unused 14.27

 sda2 is your important Windows data if you haven't overwritten it yet.

Remove the HDD from your PC and set it up as a slave in a friend's PC.  If your HDD has the wide ribbon cable coming off the back you'll need to find someone with PATA connections.  If it's a fairly new PC with the narrow (usually red) data cable, that's SATA and you'll need to find a PC with SATA connections.

Once the HDD is inside a friend's PC, with data cable and power connected to it, your friend should be able to start his PC up in Windows just like before.  Don't get anxious, let it fire up completely.  Then go into "My Computer" or Windows Explorer.  It should be showing your drive as "E" or "F" drive or something similar.  You should be able to explore the drive, recognize your folders, etc.  Burn the important personal data to DVD's or what have you.  If you could borrow an external HDD, that would be much better because it sounds like you have a fair amount of data.   Copying to an external HDD would certainly be cheaper/easier than churning thru a pile of DVD's.

There's probably a way to put your existing HDD back in order.  Once you've got a copy of your personal data off the drive, you can calm down and try to figure it out.  Or just re-install Windows and restore your data.

Either way, you need to save what you can now before the situation gets any worse...

EDIT:  You say you no longer have the desire to be a computer poseur, and will leave it to others who know what they're doing.  How do you think those "others" got there?  Books and YouTube will only take you so far.  The only way to learn this stuff is hands-on, and that'll blow up in your face every once in a while.  The only mistake you made was going into this with a HDD full of valuable data, and no clearly defined plan to retain the data if things didn't turn out as planned.  Don't give up!  Scrounge up an old blank HDD or an old test PC and get back on the horse.  If you acquire an old hand-me-down PC with no valuable data you can leave that gut-wrenching feeling behind and have some fun!

---

### Post by Mattevt on 2007-12-25
I unfortunately had to reformat the entire hard drive. I forgot that much of my stuff was backed up to an external hard drive on the network we have in the house. The music is on mine and my brothers mp3 players. I just have to find all the programs again...some I don't have the disk for because I borrowed them from friends Finale, Spin it again etc...(bit torrent anyone). And all the videos. But I'm using XP pro now and the computer runs really fast again (hmm I wonder why.) I will wait until I get a new computer to play around with things such as these.

I like bartenders idea of taking out the harddrive, unfortunately I didn't think of that and the entire drive was reformatted last night. Call it a learning experience. I'll never make that mistake again.

Thanks again guys for all of your insight...and patience.

---

### Post by Mattevt on 2007-12-25
> **mc4man said:**
> when you reformatted you probably didn't delete the partition(s) that ubuntu had created. 
 You can use the disk management tool in xp to reclaim the space as an add. drive (partition) 
[http://www.mcmcse.com/windows_xp/guides/diskmanagement.shtml](http://www.mcmcse.com/windows_xp/guides/diskmanagement.shtml)
read thru before acting


Wow...the things I don't know. Very useful thank you!

---

### Post by Mattevt on 2008-04-30
Sorry to bring up an old topic, but I just wanted to thank all the people that tried to help me. I learned a hell of a lot between then and now--and I'm now successfully running Hardy with Vista, using Hardy about 90% of the time. So, thanks again.

---

