---
title: "[SOLVED] Windows 98SE aa a 4th boot option"
date: 2008-03-17
forum: Absolute Beginner Talk
---

### Post by Arch Parsons on 2008-03-17
I already have Windows XP, Vista and Ubuntu 7.10  triple booting successfully.  They are all on separate partitions on  my master drive a Sata2 WD320GB drive. I also have a 40GB IDE slave.  Is it possible to unplug the Sata drive and install Win98 to the second drive and later plug the Sata drive back in and  use BCEdit to  edit the Vista loader to include 98 on the second drive  as well as Vista and XP on the main drive?

---

### Post by Calash on 2008-03-17
Is there a SATA driver for 98?  You may need to run it in compatability mode to get the OS to even read the drive.

---

### Post by drubin on 2008-03-17
> **Calash said:**
> Is there a SATA driver for 98?  You may need to run it in compatability mode to get the OS to even read the drive.

> I also have a 40GB **IDE slave**. Is it possible to unplug the Sata drive and install Win98 to the second drive


I don't think windows 98 would have a problem on a IDE drive would it?

As for eating the Vista loader..... Your guess is as good as mine.

---

### Post by Duck2006 on 2008-03-17
Yes you should be able to set it up that way.

---

### Post by Arch Parsons on 2008-03-17
I had a go at this yesterday. First problem I had was that my Win98 boot floppy did not include a driver for my DVD drive, so I could not run Setup from the DVD drive. I tried some foolish stuff.  I copied the Win98 to the IDE disk and then copied the Win98 CD.  It said I had to create an MSDos partition. In the process of connecting and disconnecting the IDE drive, I had problems with the connector and at one point my computer wouldn't boot.  After that I read a post that suggested that trying to install Win98 after XP, or Vista, or Linux was a big mistake.  I have reformatted the drive now and I am waiting for further comments.  Speaking of not seeing the Sata Drive, I am seeing the oddity now that my POST is not showing this drive, It only shows the IDE drive and the DVD, although the 320GB disk does show up in BIOS and does boot normally....

---

### Post by drubin on 2008-03-18
May i ask why you need to have windows 98?

---

### Post by Arch Parsons on 2008-03-18
Good question. Probably for fun more than anything else. I feel a certain nostalgia for old operating systems. I remember also with fondness Windows 3.1. I guess the floppies are still around here someplace.  I think it was possibly more stable than XP, to be honest. Before that I spent a ton of time with the Tandy Color Computer when 64K RAM was considered great.  Now we're taking in the gigabytes and soon it will be terabyes..  I still have 3 or 4 of these computers in a box down in the basement. One thing about them, they didn't crash. I brought one up for the grand children a few months ago.  It was so difficult to rekindle any interest.  Evem the kids were bored.   I think it's the lousy graphics. I dp think it would be interesting to have several of the various Windows editions on the one machine, though,  if for no other reason than to compare them and see where we've come and where we're going. In some respects, shut down time for example, I think we're going backwards! One thing about Ubuntu, it has a muich faster shut down and startup time than any version of Windows.  I acknowledge the fact that Windows 98 is obsolete of course. Thanks for asking.

---

### Post by Arch Parsons on 2008-03-18
I think the subject of adding an additional operating system on a second drive, was what I was primarily interested in, rather than installing Win98 per se. Actually I have a Win98 system working only 3 feet away from me, which I could use, but seldom or never do.   What about if I were to consider adding a 64-bit version of Windows XP or Vista. for ecample,  as an alternative to booting the 32-bit version.  What about another Linux version?  Could I add that  to a  second drive?. BTW, I just ordered a second matching SATA drive, so hopefully I will soon have the option of using a partiton on a  newer more dependable drive, although my primary purpose for buying the second drive was for backing up an image  of drive C. The more work I put into my present setup, the more concerned I am about not having to wipe it out and do it all over again.

---

### Post by LowSky on 2008-03-18
I actually have Windows XP  starting up quicker than Ubuntu, shutdown seems about the same. Might be my settints but honestly  the last few Ubuntu Releases have become more and more system hogs.

I find it funny that back in the late 1980s a machine could boot into DOS within 10 seconds... Windows came along and it took 30-60 seconds... then it got worse with each release. I dont understand how all of our machinery is getting faster and faster yet our operating systems are getting slower and slower?

Just this thought make me want to find an old 486 machine and speed test it against my Athlon 64 machine (I wonder if Win 3.11 will even run on it...)

---

### Post by Arch Parsons on 2008-03-19
Thanks for the comments I'm a pack rat, and I actually have system units in my basement with 386, 486  processors and one beside me running Win98 with a Celeron 400 cpu, and I actually do boot them up from time to time.  The boot up times depend, as you know, on the operating systems installed, but Gawd the Internet performance is bad on those old machines!  It's funny, though, how we used to pay $2000 or even $3000 for an old AT running DOS and now it's possible to get something running Vista for $200!  Even though we grumble, not all is going backwards.  The goal of course, as we know,  is revenue based with obsolescence being a planned objective. Your computer will always be obsolete by the time you get it out of the box.  Somehwhat like buying a car, I find the best bang for the buck comes from buying something that was manufactured around 2 or 3 years previoulsy. I didn't want to get off the topic too much, though, because I do intend to further my understanding of multibooting as well as learning Linux. Thanks again.

---

### Post by 1875 on 2008-03-19
Why not install Win98 on a virtual machine? Then then you fell like a bit of nostalgia just fire up VirtualBox. No need to reboot and good performance.

---

### Post by Arch Parsons on 2008-03-20
I nerver heard about VirtualBox.  I will look it up.  Thanks

---

### Post by Arch Parsons on 2008-03-20
I tried to install it in the XP partition but I got warnings about it not being compatible with XP so I stopped the installation.

---

### Post by Andavane on 2008-03-20
> **LowSky said:**
> I actually have Windows XP  starting up quicker than Ubuntu, ... I dont understand how all of our machinery is getting faster and faster yet our operating systems are getting slower and slower (I wonder if Win 3.11 will even run on it...)

Indeed! There must be thousands of people who are quite happy with what they have and the way things are working, without all this need for change.

Why cannot Linux remain slick and slim? 

Regards

John

---

### Post by Golem XIV on 2008-03-20
Hmmmm

I think that you need a primary FAT16 or FAT32 partition to boot Win9x (i.e. to install DOS 7.x so it can then start Win9x). 

Since you already have one primary for XP, another primary for Vista and 2 more for Linux (/ and swap) you ran out of primary partitions.

The solution may be in having one NTFS boot partition (that would boot XP or Vista), one FAT16/32 for Win9x and one ext3 for /.  Then a secondary with at least 3 logical partitions: XP, Vista and swap.

I'm not sure if this is doable, but it may be worth a try.

As for boot times:  in my experience, XP appears to boot faster because the desktop appears faster, but from the moment the desktop appears to the moment when the system is actually usable, you have to wait quite a while until all background apps get loaded.

---

### Post by Steve Angelidis on 2008-03-20
Can't help with getting Windows 98 running issue.

But I was interested to read about the general OS comments...particularly about Ubuntu getting to be a "hog" and taking a long time to load.

I guess its all relative. I'm coming from Vista on a six month old Toshiba laptop (2Gbytes RAM, 200 Gbyte HD, Intel Centrino core 2 duo etc... etc...). When I would start it up, it would take so long to get going that I'd go off and do dishes or make coffee or read a section of the newspaper or whatever.

And when everything was finally up and running, nearly 40% of my RAM was consumed by Vista and the CPU was churning away also at 20 -40 % doing who knows what. Shutting down would often take even longer. I'd occasionally get worried and check in on the computer to make sure that it hadn't gotten hung up or frozen.

In contrast, Gutsy takes less than a minute to load, consumes about 15% of my RAM after its booted,  CPU activity is well below 5% and the machine shuts down in about 10 seconds. So if Ubuntu is getting to be a hog, its still got a long way to go in catching up to Windows.

I think I go back as far as Arch, except I had a Kaypro II running CP/M in 64 kbytes of RAM with 2 single-sided double density 5.25 inch floppy drives. It was a portable (27 pounds) and had a 9 inch black and white screen. Ran mostly WordStar 3.3 and Perfect Calc. Bootable disk with WordStar went into drive A and data disk went into drive B. Paid $2700. Wish I'd kept it.

---

### Post by PmDematagoda on 2008-03-20
If you want to run Windows 98 then you will have to really get serious with the compatibility tweaks in the BIOS. 

For example when I wanted to install Windows 98 on a school PC I got errors with the Windows installer freezing when it was trying to detect the hardware. I then went to the BIOS and turned on everything I knew that concerned compatibility for legacy OSes, after that Windows 98 started working well, but come on, sacrificing new features and performance just to run Windows 98? In my opinion that is a bit much.

In other words, it can be done, but I really do not think it is worth it.

---

### Post by Arch Parsons on 2008-03-20
Thanks for the clarification. I assume you talking about starting over from scratch.  I may have to do that soon - the way my XP (still the one with most of my stuff on it) is behaving.  Ditto on the slow loading of the starup apps, and XP has a bug that you have to log off and then log on again if you want to be able to see all your systray icons.  I've tried everything to fix that bug, but apparently there is no universal fix. I hate having to use Ctrl-Alt-Delete to search for and then close certanin startup apps that you may need to close at a given time.  I much prefer being able to use the icons in the systray.  I also have the problem of restarting at shutdown, and I've spent hours researching and trying to narrow down the cause of that.  I suspect there's an offending driver somewhere, but XP doesn't tell you which one. Although a clean install generally works,I think if one were to make a list of all the issues in XP, I'd be willing to guess that the list would be over 100. Vista is better.  I don't think there's any doubt about that.  As far as Ubuntu is concerned, as M$ knows, it's harder to learn.  I still don't understand how to install programs from the web, except when I see them in the Synaptic Package Manager.

---

### Post by caravel on 2008-03-20
> **PmDematagoda said:**
> If you want to run Windows 98 then you will have to really get serious with the compatibility tweaks in the BIOS. 

For example when I wanted to install Windows 98 on a school PC I got errors with the Windows installer freezing when it was trying to detect the hardware. I then went to the BIOS and turned on everything I knew that concerned compatibility for legacy OSes, after that Windows 98 started working well, but come on, sacrificing new features and performance just to run Windows 98? In my opinion that is a bit much.
Initially when installing Win9x this is the way to do it, usually the only thing you need to disable in the BIOS is the ACPI, if there is an option available, (this isn't required but it makes the OS more stable as it causes it to detect and install APM Support and leave out all of the ACPI system drivers).  Also you can run the setup program in PIC mode (x:\setup /p i), to disable the A-PIC which Win98 doesn't handle well.  It is also a good idea to disable all onboard peripheral devices from the BIOS then enable them one by one and install the drivers one at a time, rebooting between each one.  Once all of this is done ACPI can be turned back on for the other OSes to use and Win98SE will ignore it and still run in APM mode regardless.  The next issue will be the memory and the vcache will have to be limited in order to stop it from crashing.

The OP said that he had a spare PATA HDD, or am I reading this wrong?  Therefore the best way to go about this would be to remove/unplug the SATA drive(s) and any other PATA drives and install Win98/SE as a standalone to this drive.  Once this is done all other drives can be reconnected and an entry added to grub in order to boot to Win98.  This also means that Win98 does not touch your other windows partitions or overwrite your bootloader.

-Edit:  It may be that Win98 won't be able to see your SATA controller, and thus your SATA drives once it's booted.  You could resolve this by installing the driver if it's available, but if those drives are formatted in NTFS or ext3 etc, then there isn't much point as Win98 won't be able to read/write to them anyway.

---

### Post by Arch Parsons on 2008-03-20
Hello all,  

Thank you very much to everyone for the informative and detailed information.  I am persuaded now that installing Windows 98 is definitely not worth it, and really I had no reason for doing it in the first place.  I might as well mark this thread as solved because, in this case, deciding against the install was the best solution.  As for the possiblity of adding another OS other than Win98, that would form the basis of a new thread if I end up going that route in the future and having problems.  Thanks again.

---

