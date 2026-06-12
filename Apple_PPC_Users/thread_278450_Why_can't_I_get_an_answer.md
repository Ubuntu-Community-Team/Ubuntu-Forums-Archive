---
title: "Why can't I get an answer?"
date: 2006-10-16
forum: Apple PPC Users
---

### Post by mph66 on 2006-10-16
Hi,

It's been a long week and a half.  I wiped the hard drive on my eMac and reformatted the drive using the LiveCD (Dapper) and installed Ubuntu.  I really love it, but I still need some Mac programs.  So I thought, "Well, I'll just reformat the HD for two partitions and start over..."

Famous last words.  Let this be a warning to anyone out there with a Mac-> If you format your drive and install Ubuntu without creating another partition for OSX, YOU WILL NEVER BE ABLE TO REFORMAT YOUR DRIVE FOR OS X AGAIN!

I've tried several different threads, and no one really helps you out beyond the obvious.  For reasons of posterity, I'll list what I've done, to date:

After reformatting drive for Linux and installing Ubuntu, I began my journey in backward-migration by:

1) Putting OS X cd in drawer and holding down "C" key on startup.  Black screen offers two options: l for Linux, c for cd.  Press "c" key.  Computer "waits" then, after "..." appears on screen, it goes back to that same black boot screen.  Won't recognize OS X cd.  Holding down c key indefinitely also does not work.  These two attempts represent seperate, individual attempts at booting from cd.

2) Putting OS X cd in drawer and holding down "option" key at startup.  Blue "classic" screen shows HD formatted for Linux, but never recognizes/mounts OS X cd.  Restart just produces maddening infinite loop.

3) Putting "restore" disks in drawer and attempting both startup routines listed in #s 1 and 2 produce same results.

4) Put Live CD (again, Dapper) in drawer.  Boot from CD.  Attempts to reformat drive, or create HFS + partition on which to install Mac OSX fail because partitioner won't allow you to create HFS+ partition (option is grayed-out).

To date, I've gotten responses from people who are genuinely trying to be helpful, and I'm thankful, but they're usually obvious things I've already done ("Have you held down the "c" key long enough?"  "Are you using a PPC live disk?").  I still haven't gotten an answer, and I'm suspicious that it's going to take a real guru to step up with some terminal commands before my hd ever sees a Mac OS X install cd again.  I'm wondering if I don't need to create a mount point for the cd in yaboot?  Or when I boot to Ubuntu, is there a way I can configure the OS to recognize another startup disk in another platform language?

Ultimately, this is a cry for help from the developers.  Please put in a pathway for transmigration so that users like myself aren't stuck in limbo somewhere, waiting, at the mercy of the gods of the forum, for an answer.  This should be really straightforward- put the LiveCD in the drawer, choose a portion of unused space in the partitioner, right-click, make an HFS+ partition, and get on with it.  

If anyone out there has a clue, I'd LOVE to hear from you right about now.  ](*,) 

Very Best,

Marc

---

### Post by taurus on 2006-10-16
Move this one to Mac section since it's a Mac question and you could get better answers over there...

---

### Post by mph66 on 2006-10-16
Thanks, Taurus!

---

### Post by taurus on 2006-10-16
You're welcome.  I hope somebody here can help you with your problem, mate.

---

### Post by mips on 2006-10-16
> **mph66 said:**
> If you format your drive and install Ubuntu without creating another partition for OSX, YOU WILL NEVER BE ABLE TO REFORMAT YOUR DRIVE FOR OS X AGAIN! 

If I ever heard a load of BS then that is it !!!

---

### Post by stmiller on 2006-10-16
> 
Quote:
Originally Posted by mph66 View Post
If you format your drive and install Ubuntu without creating another partition for OSX, YOU WILL NEVER BE ABLE TO REFORMAT YOUR DRIVE FOR OS X AGAIN!

If I ever heard a load of BS then that is it !!!

No kidding. The fact that it will not recognize the boot CD (OS X) is odd. This has NOTHING to do with the hard drive, or partition tables. You should be able to boot from ANY boot cd. In fact, you can disconnect your hard drive, and still boot from the boot CD of course.

Also, make a specific title to your problem. Having " Why can't I get an answer?" is a pretty poor title. If you said something like 'cannot boot from blah blah' that would be more specific, and you would get better help.

---

### Post by munchbach on 2006-10-16
> **mph66 said:**
> Hi,
Let this be a warning to anyone out there with a Mac-> If you format your drive and install Ubuntu without creating another partition for OSX, YOU WILL NEVER BE ABLE TO REFORMAT YOUR DRIVE FOR OS X AGAIN!

I've tried several different threads, and no one really helps you out beyond the obvious.
](*,) 

Very Best,

Marc


1. Boot to your OS X CD.

2. Open Disk Utility.

3. Select your Main HD (not the 2 linux partitions that appear underneath it in gray).

4. Select the "Partition" tab.

5. Select one partition.

6. Click the "Partition" button.

7. Edit your post so you aren't spreading falsehoods ;) 

Cheers.

---

### Post by mph66 on 2006-10-16
Thank you, but I wasn't trolling.  I am, in fact, looking for answers.  This eMac will not boot from the OS X cd.  But thanks for the help.

Is there a piece of information you need to understand that this machine will not boot from an OS X cd?  Perhaps I'm not telling you something you need to know in order for you to help me?

-Marc

---

### Post by mph66 on 2006-10-16
> **stmiller said:**
> 
Also, make a specific title to your problem. Having " Why can't I get an answer?" is a pretty poor title. If you said something like 'cannot boot from blah blah' that would be more specific, and you would get better help.

Tried that.  Do an "advanced search" on these forums and read the other threads I've posted this week with much more descriptive titles.  See what kind of results those "descriptive titles" have produced.  I still cannot boot from an OS X cd. 

-Marc

---

### Post by Jason_25 on 2006-10-16
My friend has a 700 mhz G3 Emac that boots from the CD.  How else would you reinstall the system if you can't boot from the CD?

---

### Post by mph66 on 2006-10-16
> **Jason_25 said:**
> My friend has a 700 mhz G3 Emac that boots from the CD.  How else would you reinstall the system if you can't boot from the CD?

Good question.  As soon as I find the answer to that question, I'll stop harranguing you folks! :D 

-Marc

---

### Post by mph66 on 2006-10-16
> **munchbach said:**
> 1. Boot to your OS X CD.

2. Open Disk Utility.

3. Select your Main HD (not the 2 linux partitions that appear underneath it in gray).

4. Select the "Partition" tab.

5. Select one partition.

6. Click the "Partition" button.

7. Edit your post so you aren't spreading falsehoods ;) 

Cheers.

Thank you for illustrating "genuinely well-meaning but obvious". Or "oblivious".  If I can't boot from the OS X install disk by holding down the CD when restarting the machine, I'm not likely going to get to Disk Utilities, now am I?  If you'd like to help, answers that go beyond 

-Marc

-Marc

---

### Post by Jose R on 2006-10-16
ok, have you tried the following:

*From Apple's support page on start-up shortcuts.*

Mac OS X keyboard shortcuts 
Learn about common Mac OS X keyboard shortcuts.

Startup Keystroke Description 

Press X during startup - Force Mac OS X startup  

Press Option-Command-Shift-Delete
during startup  - Bypass primary startup volume and seek a different startup volume (such as a CD or external disk)
 
Press T during startup - Start up in FireWire Target Disk mode
 
Fro target disk mode, you would need a separate external HD on which you have OSX install.

---

### Post by xinix on 2006-10-16
It could be your CD, it could be something else.  Reformatting a drive on an Apple does not lock you out of being able to reinstall MacOS or booting from the CD.  I did it many times when I was on the PPC platform.
Try this:

Put the CD in the drive.
Boot the computer holding the Option key.
It should bring up a screen with icons for the OS's that are available to you. Select the cd from there.  It can take a while to fully load so be patient.

---

### Post by munchbach on 2006-10-16
> **mph66 said:**
> Thank you, but I wasn't trolling.  I am, in fact, looking for answers.  This eMac will not boot from the OS X cd.  But thanks for the help.

Is there a piece of information you need to understand that this machine will not boot from an OS X cd?  Perhaps I'm not telling you something you need to know in order for you to help me?

-Marc

My recommendations:

1. Does your CD drive work otherwise?  If you insert a CD when Ubuntu is booted does it mount it?  (I'm going to assume yes cause you managed to get Ubuntu onto your machine).

2. Are you using either: 1. the gray CD's _that came with your computer_ or are you using someone elses?  These are OEM CD's and only the ones that came with your comptuer will boot your machine. 2.  A generic copy of OS X purchased for about $129, has a big black X on the CD (most likely a DVD).

3. Boot your comptuer with the OS X cd in and hold down the "option" key.   See what options come up.  If you see the OS X CD then select it and hit the right arrow and report what happens.

4. Is the CD scratched?

Good luck.

---

### Post by mph66 on 2006-10-16
> **munchbach said:**
> My recommendations:

Thanks Munch.  All good suggestions.  See answers to what I've tried/done below:

1. Does your CD drive work otherwise?  If you insert a CD when Ubuntu is booted does it mount it?  (I'm going to assume yes cause you managed to get Ubuntu onto your machine).

Works fine.  And yes, I got Ubuntu LiveCD booted and installed using this cd drive.  Today.  For the fifth time.  While trying to repartition.

2. Are you using either: 1. the gray CD's _that came with your computer_ or are you using someone elses?  These are OEM CD's and only the ones that came with your comptuer will boot your machine. 2.  A generic copy of OS X purchased for about $129, has a big black X on the CD (most likely a DVD).

Both.  First, the OS X Jaguar (10.2 cds) and then the gray "restore" disks.  I've also booted from the Mac Hardware inspector cd.  All seems to be fine in hardware-ville, but the machine won't boot from an OS X cd rom.  There is no combo drive on this thing, so I can't boot from an OS X.3 DVD. I have one.  No can do here.

3. Boot your comptuer with the OS X cd in and hold down the "option" key.   See what options come up.  If you see the OS X CD then select it and hit the right arrow and report what happens.

Yep.  Did that.  See original post.

4. Is the CD scratched?

Nope.  Checked that, but good idea.

Good luck.

I've also tried to install an HFS partition (allows me to do that).  This, as you will recall, is the OS 9 and lower disk format.  I have tried booting from OS 9 and 8.5 cds and still no luck there, either.

-Marc

---

### Post by xinix on 2006-10-16
Also, if you are not using the keyboard that came with the emac.  Try the one that did.  Sounds silly but sometimes apples don't play well with other keyboards when it comes to this kind of thing.

---

### Post by xinix on 2006-10-16
Stolen from the apple user forum
> See if resetting PRAM helps, since volume settings are stored there (see What's stored in PRAM?). Restart, then immediately hold down command-option-p-r keys until you hear three sets of chimes, then release the keys and let the computer finish starting up.


There is also a deeper reset you can do but I also can't guarantee it wouldn't blow up the world too.

---

### Post by mph66 on 2006-10-16
> **xinix said:**
> Also, if you are not using the keyboard that came with the emac.  Try the one that did.  Sounds silly but sometimes apples don't play well with other keyboards when it comes to this kind of thing.

Using OEM keyboard, but thanks.  Good to know for future ref.

-Marc

---

### Post by mph66 on 2006-10-16
> **Jose R said:**
> ok, have you tried the following:

*From Apple's support page on start-up shortcuts.*

Mac OS X keyboard shortcuts 
Learn about common Mac OS X keyboard shortcuts.

Startup Keystroke Description 

Press X during startup - Force Mac OS X startup  

Tried this.  Nothing.

Press Option-Command-Shift-Delete
during startup  - Bypass primary startup volume and seek a different startup volume (such as a CD or external disk)

This causes alternating blinking "?"/startup folder.  Can't get to CD to boot up, but the hd seems to have been circumvented.  Interesting result.  What is this saying about the computer seeing the cd drive?  If, as everyone here maintains, the cd should boot no matter what?
 
Press T during startup - Start up in FireWire Target Disk mode
 
Fro target disk mode, you would need a separate external HD on which you have OSX install.

No target disk mode.

-Marc

---

### Post by mph66 on 2006-10-16
> **xinix said:**
> Stolen from the apple user forum


There is also a deeper reset you can do but I also can't guarantee it wouldn't blow up the world too.

This, I thought, held promise.  I held down the requisite keys and listened for the restart chord 3X (as we used to do back in the pre-OSX days) and nothing.  Thanks, though.

-Marc

---

### Post by xinix on 2006-10-16
No guarantees that monkeys won't become master rulers of earth there is this option as well.

> if resetting PRAM doesn't help, I'd bump it to resetting NVRAM and resetting Open Firmware. Restart holding down the command-option-o-f keys until you see the "Welcome to Open Firmware" black text on a white screen; at the command line prompt, type in the following commands and press return after each (case sensitive, no spaces):
reset-nvram
set-defaults
reset-all
The Mac should restart after reset-all (if it doesn't, type mac-boot and press Return)

It's starting to sound like you might have more luck here: [http://discussions.apple.com/category.jspa?categoryID=119]("http://discussions.apple.com/category.jspa?categoryID=119")

---

### Post by anurse on 2006-10-16
Someone else suggested this but ... it sounds to me like the problem lies in your hardware or your disks. The fact that you can't book from OS 9, X, and 8.5 suggests to me that your cd drive is broken. I use an eMac and have had no troubles rebooting from the Mac install CD. 

I would be interested to know what finally happens and where the problem lies (when you figure it out). Best of luck.

---

### Post by stmiller on 2006-10-16
> 
Quote:
Originally Posted by stmiller
Also, make a specific title to your problem. Having " Why can't I get an answer?" is a pretty poor title. If you said something like 'cannot boot from blah blah' that would be more specific, and you would get better help.

-----------------
Tried that. Do an "advanced search" on these forums and read the other threads I've posted this week with much more descriptive titles. See what kind of results those "descriptive titles" have produced. I still cannot boot from an OS X cd.

-Marc

I don't care to waste my time searching for your other posts. But in general, always use a specific title. This goes for any posting ANYWHERE on the internet, for any forum. Internet 101.

---

### Post by mph66 on 2006-10-17
> **stmiller said:**
> I don't care to waste my time searching for your other posts. But in general, always use a specific title. This goes for any posting ANYWHERE on the internet, for any forum. Internet 101.

Thank you!  You're such a helpful person!  It must be difficult, lording all that intelligence over everyone, pooping gold bars everywhere, having to lug a giant cranium (and equally ponderous ego) about all day.  Does it require any special assistance?  Probably not, as I'm sure you're the very picture of physical sartorial perfection.  My God, turn down the blinding rays of light...Someone pass me my welder's goggles...

-mph66

---

### Post by mph66 on 2006-10-17
> **anurse said:**
> Someone else suggested this but ... it sounds to me like the problem lies in your hardware or your disks. The fact that you can't book from OS 9, X, and 8.5 suggests to me that your cd drive is broken. I use an eMac and have had no troubles rebooting from the Mac install CD. 

I would be interested to know what finally happens and where the problem lies (when you figure it out). Best of luck.

This is also curious, because I want so badly to believe it, but how does it explain how I've installed (and re-installed 5 times or so) Ubuntu from the same cd drive?  Why is it that I can ONLY boot from the LiveCD?  Why can I ONLY boot from the hard drive into Ubuntu?  It's like the OS has taken over?  Hal...? ;-)

-Marc

---

### Post by stmiller on 2006-10-17
> 
Quote:
Originally Posted by stmiller
I don't care to waste my time searching for your other posts. But in general, always use a specific title. This goes for any posting ANYWHERE on the internet, for any forum. Internet 101.


--------
Thank you! You're such a helpful person! It must be difficult, lording all that intelligence over everyone, pooping gold bars everywhere, having to lug a giant cranium (and equally ponderous ego) about all day. Does it require any special assistance? Probably not, as I'm sure you're the very picture of physical sartorial perfection. My God, turn down the blinding rays of light...Someone pass me my welder's goggles...

-mph66

Yes, what I posted in that original post above is true. Use a specific title. This is how things work on internet forums, and mailing lists all over.

---

### Post by shadie on 2006-10-17
I had some issues booting from my OS X DVD after installing ubuntu, if I remember correctly there is an open firmware command to boot the DVD, at startup try command+option+O+F and type help, boot cd-rom or boot cdrom


Edit that title, and grow up.

---

### Post by mph66 on 2006-10-18
Got an answer.  I'd like to thank all the folks who contributed in a really positive way to this discussion.  As it turned out, There's a freak problem running amok.  I took my Apple-original OS X.2 cds to another lab of eMacs (same generation as mine) and it would boot *some* of the machines, but not all.  Thinking this odd, I went back to my machine and tried the system restore disks.  That wouldn't boot either.  It should be said that these system disks came with the machines when we purchased them.  No dice (!!!).
I went back to the other lab and, sure enough, NONE of the machines booted from what were supposed to be Apple's "life ring" cds.  Yikes!  Then, in the same package were OS 10.3 install disks.  These finally worked.  You can imagine, after a week, my feelings of amazement and rage and embarassment, all at the same time.  I mean, what are the odds that two seperate OS disks, stored securely in two seperate places would be entirely bad?  And why wouldn't system restore disks MADE for that machine not work?

Anyway, I thought people here should know, and know that I'm sorry for any trouble caused, but moreover, I'm appreciative of the brainwork many applied trying to be positive.  I'm happy to report I've got a fine dual-boot system going, with MOL running quite well.  The irony is that now that I've got the two partitions and MOL in full force, I may never have to boot into OS X again.

Thanks,

Marc

---

### Post by Martin A on 2006-10-19
> 
Thank you! You're such a helpful person! It must be difficult, lording all that intelligence over everyone, pooping gold bars everywhere, having to lug a giant cranium (and equally ponderous ego) about all day. Does it require any special assistance? Probably not, as I'm sure you're the very picture of physical sartorial perfection. My God, turn down the blinding rays of light...Someone pass me my welder's goggles...


Now THATs funny :P

Glad you got it sorted.

---

