---
title: "How to delete Ubuntu Partition without Grub error"
date: 2007-08-26
forum: Absolute Beginner Talk
---

### Post by Brightbelt on 2007-08-26
Hi,
 I'm unfortunately I'm having to delete the Ubuntu Studio partition on my HP DV9000 laptop because of a project I have to do with XP (long story; I need to minimize everything/every program). 

I went into XP into Disk Management and deleted the Ubuntu Studio partition but it messed up the Grub Manu and I got a Grub Error 22 when I rebooted. So now I can't access XP without fixing that somehow.

Right now I'm reinstalling Ubuntu Studio just to get the Grub menu back. So how can I delete Ubuntu without messing up my Grub/Boot menu? 

Please note: I do not have a standard XP Disk for this computer. Everything was OEM, so all I have are Homemade System Recovery DVDs that return the laptop to factory conditions. 

I'm almost positive there is no startup recovery option on those DVDs. It's all or nothing.

I appreciate any help. Btw, I did searches on this but didn't find what I needed.

Many Thanks, Frank B.

---

### Post by wolfen69 on 2007-08-26
you can delete the ubuntu partition as you did before. but now you must boot to xp cd, start the install process, but instead of installing, hit "r" for recovery console. then type fixmbr. reboot and you will be able to boot into xp normally.

---

### Post by Brightbelt on 2007-08-26
Thanks for responding Wolfen69, but I mentioned before that I do Not have a standard XP Disk. I only have 3 System Recovery DVDs that I made when I bought the computer.

I've been through this before and the Recovery DVDs I created do not I believe have a recovery console option. It either formats the whole damn thing or it doesn't.

I swear I've been through this and tried hitting 'R' etc but it goes straight into formatting. 

Actually my HP has already gone into System Recovery mode now. I seemed to have lost XP. It says it can recover my Data files so I'm trying that. 

Eventually I still may have to delete Ubuntu, in which case I'll try your option.

All I can do is see at this point,....:(

Keep an eye out for me here. I may pull this thread back up later for more assistance.

Many Thanks, Frank B.

---

### Post by anewguy on 2007-08-26
For future reference, and for anyone else wondering how to do this simply, please see this tutorial:

[http://ubuntuforums.org/showthread.php?t=508927]("http://ubuntuforums.org/showthread.php?t=508927")

---

### Post by Duck2006 on 2007-08-26
There is a way of doing it from windoze but i am not sure as to where i saw it.
Try to google it

---

### Post by kellemes on 2007-08-26
> **Duck2006 said:**
> There is a way of doing it from windoze but i am not sure as to where i saw it.
Try to google it

He can't start Windows..

---

### Post by anewguy on 2007-08-26
> **Duck2006 said:**
> There is a way of doing it from windoze but i am not sure as to where i saw it.
Try to google it

Try looking at the link in my post - it does exactly that.

---

### Post by Duck2006 on 2007-08-26
> He can't start Windows..

????????????????????????

Then how is he posting his postes?

Use that to do it.

---

### Post by Brightbelt on 2007-08-26
I'm posting from my other main computer - a glorious new 24" iMac. I love it, I admit.

Pardon me if I'm wrong Newguy, but isn't the first step in your 'howto' to "Boot into your Windows Installation"? 

I will be able to do it shortly because my HP seemed to go into the recovery by default - So I should have Windows again and still Ubuntu. So I'll try your method.

I do appreciate your posting it - I'll need it I think.

Many Thanks, Frank B.

---

### Post by Duck2006 on 2007-08-26
If it doesn't. Did you try to run the live CD and tell it to boot from the first HDD. I know you only have one drive but it sould boot from the first partition. Thats your win partition?

---

### Post by sailor2001 on 2007-08-26
another way.......good if you may be going back and forth at some future time is to download 'supergrub' and burn it.

---

### Post by julian67 on 2007-08-26
This is very easy to do.  You need [SuperGrubDisk]("http://supergrub.forjamari.linex.org/"). Using this  bootable CD you can restore the original Windows MBR so when you start your PC it boots straight into Windows.  It's a very small download and just takes a minute to do its job. 

The reason you cannot boot now is because GRUB bootloader is still installed in the MBR. GRUB points to  /boot/grub/menu.lst in your Ubuntu / partition. menu.lst lists the location of different OS on the PC and GRUB boots whichever one you choose.....but you deleted the list :)

---

### Post by anewguy on 2007-08-26
> **Brightbelt said:**
> I'm posting from my other main computer - a glorious new 24" iMac. I love it, I admit.

Pardon me if I'm wrong Newguy, but isn't the first step in your 'howto' to "Boot into your Windows Installation"? 

I will be able to do it shortly because my HP seemed to go into the recovery by default - So I should have Windows again and still Ubuntu. So I'll try your method.

I do appreciate your posting it - I'll need it I think.

Many Thanks, Frank B.

Yes - that's why it says "for future reference......".  I knew you were already beyond the point of using it THIS time (come on - don't more people than me end up doing this more than once?:) ).  I also wanted to post it so if others were reading the thread based on it's title so that perhaps they could catch things before they got to where you are and would then need an OS cd or the supergrubdisk.  I've been where you are more than once (call me stupid!:) ) and that's the reason I created that tutorial.  I was hoping it might come in handy to you should you need to delete Ubuntu again and start over.:)

I think I speak for MANY, MANY of us when I say we know your frustration!  There seems to be an assumption of knowledge to the newbie if he wants to do this (or perhaps it's just to stop him uninstalling Ubuntu?:):) )

Hope you get things working again without too much pain!:)

---

### Post by Brightbelt on 2007-08-26
OK, Possibly good news... XP did a recovery from the HP recovery partition, and my laptop has 2 internal hard drives, so my data is still there. And it seemed to fix the boot problem by wiping out Ubuntu, although the ubuntu partition is STILL THERE in XP Disk Management, but with all its space available, which leads me to believe Ubuntu was wiped clean.

This recovery did pretty much take all my applications back to factory specifications.  But the real question now is: If I delete the Ubuntu partition in Disk Management NOW, will it create a boot problem again?

My guess is no, it won't, since Ubuntu has been uninstalled, there is no Grub file to get in the way, but that's just my guess.

Any other thoughts?

Many Thanks for all your assistance,. Frank B.

---

### Post by Brightbelt on 2007-08-26
Bump?

---

### Post by julian67 on 2007-08-26
> **Brightbelt said:**
> OK, Possibly good news... XP did a recovery from the HP recovery partition, and my laptop has 2 internal hard drives, so my data is still there. And it seemed to fix the boot problem by wiping out Ubuntu, although the ubuntu partition is STILL THERE in XP Disk Management, but with all its space available, which leads me to believe Ubuntu was wiped clean.

This recovery did pretty much take all my applications back to factory specifications.  But the real question now is: If I delete the Ubuntu partition in Disk Management NOW, will it create a boot problem again?

My guess is no, it won't, since Ubuntu has been uninstalled, there is no Grub file to get in the way, but that's just my guess.

Any other thoughts?

Many Thanks for all your assistance,. Frank B.

Your guess is correct. GRUB is no longer installed as the restore process has restored the MBR to as it was when you bought the computer. btw GRUB isn't intrinsically part of Ubuntu and it's perfectly possible to have Ubuntu or any distro installed without GRUB being there. Easiest way would have been to use the Super Grub Disk and your Windows system would have been as you left it and you wouldn't have needed to use the restore partition.

---

### Post by Brightbelt on 2007-08-26
Thanks Julian67. I'll go with Super Grub next time for sure.

Many Thanks, ;) Frank

---

### Post by anewguy on 2007-08-26
For anyone viewing this thread that wants to delete their Ubuntu, please see the link I mentioned in my previous post.  This link provides you with a very simple way of setting your mbr BEFORE you delete Ubuntu, without the need for a supergrubdisk.  You can only follow that procedure if you have not already deleted Ubuntu and now find you can't boot.  It's fast, it's easy, and it will save your bacon (or maybe just your patience!!):)

---

### Post by Duck2006 on 2007-08-26
You can always run gparted from the live CD or run 

fdisk -l

From the terminal to see if the ubuntu partition is gone.

---

### Post by julian67 on 2007-08-26
> **anewguy said:**
> For anyone viewing this thread that wants to delete their Ubuntu, please see the link I mentioned in my previous post.  This link provides you with a very simple way of setting your mbr BEFORE you delete Ubuntu, without the need for a supergrubdisk.  You can only follow that procedure if you have not already deleted Ubuntu and now find you can't boot.  It's fast, it's easy, and it will save your bacon (or maybe just your patience!!):)

I think it's just as quick to use a boot CD, and I prefer the SGD method as it doesn't involve installing yet another closed source utility on Windows.  SGD is a very useful CD anyway. I use it so I can try out various distros on a dedicated partition and let them do whatever they like to the MBR, knowing I can always restore it in a minute or two.

---

### Post by Brightbelt on 2007-08-26
The irony of all this is that, from what I understand, you cannot extend a system volume in XP. So there's almost 20 GB of unallocated free space now in the C:\ drive (where Ubuntu used to be)  which I cannot use. 

The story here is that I use this laptop for a portable recording studio, hence my decision to try Ubuntu Studio for a while.  But I'm trying to get the processor fan to quiet down, because I've got real projects coming up, and I want to minimize the amount of programs installed on the laptop.

So even though there's space there for Ubuntu, I'd rather it be empty for now while I try to get my  processor fan under control.

This used to be the most quiet laptop until I (gulp) updated it to Vista one day. Of course, I took Vista off and reformatted, hoping the processor fan would return to normal, but it seems to have passed the point of no return....

Thanks, Frank B.

---

### Post by julian67 on 2007-08-27
> **Brightbelt said:**
> The irony of all this is that, from what I understand, you cannot extend a system volume in XP. So there's almost 20 GB of unallocated free space now in the C:\ drive (where Ubuntu used to be)  which I cannot use. 

The story here is that I use this laptop for a portable recording studio, hence my decision to try Ubuntu Studio for a while.  But I'm trying to get the processor fan to quiet down, because I've got real projects coming up, and I want to minimize the amount of programs installed on the laptop.

So even though there's space there for Ubuntu, I'd rather it be empty for now while I try to get my  processor fan under control.

This used to be the most quiet laptop until I (gulp) updated it to Vista one day. Of course, I took Vista off and reformatted, hoping the processor fan would return to normal, but it seems to have passed the point of no return....

Thanks, Frank B.

You should be able to manipulate the disks and partitions pretty much any way you like, but not with Windows' own disk management tool which is extremely basic. Try [Parted Magic]("http://partedmagic.com/") or [GParted Live CD]("http://gparted.sourceforge.net/"), both are small downloads, between 30 and 50 MB for each iso.

Having Ubuntu (or any other OS) installed on the free space will not affect the system's fans.  Having multiple services/applications running *within* Windows *will*.

---

### Post by anewguy on 2007-08-30
> **julian67 said:**
> I think it's just as quick to use a boot CD, and I prefer the SGD method as it doesn't involve installing yet another closed source utility on Windows.  SGD is a very useful CD anyway. I use it so I can try out various distros on a dedicated partition and let them do whatever they like to the MBR, knowing I can always restore it in a minute or two.

I guess I would say that it has been super easy for me - it requires no intelligence to do it, and the software is FREE, so I personally don't feel I'm getting locked into a utility on Windows.  The truth of the matter is, going by the posts on this forum, most people do this more than once.  And the people who are doing it are definitely using Windows as well as trying Linux.  So it just comes down to making something as friendly and fool proof as possible.  SGD may be that for some, the approach I took may that for others (it has been pointed to by some Ubuntu members also, so it must not be useless:)).  In fact, the how to I wrote could use an additional post saying here is another way, and in particular, here is what to do if you have already lost your Linux partition and can't boot  - that would be greatly appreciated if you want to post a reply on that how-to with step by step for SGD.  It is meant as a reference for not getting into a quandry, and if already there how to get out.  Your input there would be greatly appreciated.  Try not to just post a link, but rather give the instructions in the post.  That way it keeps it a single read-me to help them fix their problem.  Thanks:)

Either way, thanks for the information.  Getting all available choices out there is what the Ubuntu community is all about.  Have a good one!:)

---

### Post by julian67 on 2007-08-30
> **anewguy said:**
> ...... the software is FREE, so I personally don't feel I'm getting locked into a utility on Windows. 

The software is no cost and is redistributable  but there is no source code available, so it is not Free software.

---

### Post by anewguy on 2007-08-30
> **julian67 said:**
> The software is no cost and is redistributable  but there is no source code available, so it is not Free software.

Yeah, well enough already!!!!!  The damn process works and it works good and is SUPER easy!  I didn't get on here to get in a pissing contest with someone - just offering a SIMPLE solution that works.  Grow up.

And let me see - it's at no cost but it's not free??  Who gives a damn about the source when you are trying to get back to Windows (it ain't been free in my lifetime) so why should it matter - the program is FREE TO USE and it seems to me that in this instance, trying to get back to Windows, that should be all that matters.  I can't imagine ANYONE in that situation saying "no, thanks for a solution that's easy and works, but I'm not going to use it because I can't get the source code".  Do you REALLY think that is going to happen!

Let's see, a 10 second download and then a 30 second execution in Windows and everything is done somehow doesn't stand a chance against the time it takes to download a CD image, burn it, and then jack with it??????

---

### Post by julian67 on 2007-08-30
> **anewguy said:**
> Yeah, well enough already!!!!!  The damn process works and it works good and is SUPER easy!  I didn't get on here to get in a pissing contest with someone - just offering a SIMPLE solution that works.  Grow up.

And let me see - it's at no cost but it's not free??  Who gives a damn about the source when you are trying to get back to Windows (it ain't been free in my lifetime) so why should it matter - the program is FREE TO USE and it seems to me that in this instance, trying to get back to Windows, that should be all that matters.  I can't imagine ANYONE in that situation saying "no, thanks for a solution that's easy and works, but I'm not going to use it because I can't get the source code".  Do you REALLY think that is going to happen!

Let's see, a 10 second download and then a 30 second execution in Windows and everything is done somehow doesn't stand a chance against the time it takes to download a CD image, burn it, and then jack with it??????



I just made a simple statement, that's all. It was to explain my earlier reasoning as to preferring a FOSS solution. I'm not being competitive or aggressive and I'm very surprised at your response.

---

### Post by julian67 on 2007-08-30
> **anewguy said:**
> Yeah, well enough already!!!!!  The damn process works and it works good and is SUPER easy!  I didn't get on here to get in a pissing contest with someone - just offering a SIMPLE solution that works.  Grow up.

And let me see - it's at no cost but it's not free??  Who gives a damn about the source when you are trying to get back to Windows (it ain't been free in my lifetime) so why should it matter - the program is FREE TO USE and it seems to me that in this instance, trying to get back to Windows, that should be all that matters.  I can't imagine ANYONE in that situation saying "no, thanks for a solution that's easy and works, but I'm not going to use it because I can't get the source code".  Do you REALLY think that is going to happen!

Let's see, a 10 second download and then a 30 second execution in Windows and everything is done somehow doesn't stand a chance against the time it takes to download a CD image, burn it, and then jack with it??????

I'm quoting this while it is still there because I reported it as rude and offensive.

---

### Post by anewguy on 2007-08-30
Well, read your responses again if you want to know why I got angry.  You were giving the impression that there was no way anything was going to work as good as SGD, and that quite simply isn't true.  I appreciate reporting me - they are kicking me off the forums altogether as I write this.

---

### Post by Bachstelze on 2007-08-30
> **anewguy said:**
> Well, read your responses again if you want to know why I got angry.  You were giving the impression that there was no way anything was going to work as good as SGD, and that quite simply isn't true.  I appreciate reporting me - they are kicking me off the forums altogether as I write this.

No, we are not. You recieved a one-point infraction, and it takes ten points to be put on moderation and fifteen to be banned. And next time you think someone insulted you in a message, just report it instead of answering with another insult.

---

