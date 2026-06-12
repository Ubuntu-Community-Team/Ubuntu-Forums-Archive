---
title: "How do I install Ubuntu?"
date: 2005-10-09
forum: Absolute Beginner Talk
---

### Post by Fortigurn on 2005-10-09
I have downloaded both the CD 'install' and the CD 'live' packages.  I understand that the next step is to unpack them and burn them to CD.

My question is, do I simply drop all the data onto the CD and put it in a machine?  Will it automatically boot, or do I have to set the CD to 'bootable' when I burn it?

If the latter, which CD boot option should I use?  When attempting to burn a copy of the install version, I've tried 'HD emulation', I've tried 'Floppy 1.44 emulation', I've tried 'Win98 emulation', and I've tried 'No emulation - WinXP/NT', but none of these CDs would boot to the install screen.

I ended up with four useless disks.  Suggestions welcome.

---

### Post by heimo on 2005-10-09
You need to burn it "from disk image" or "from iso file". Sometimes you can do this by drag'n'droping the iso file to the window area of burning software where you add files to burn - in that case, the program should ask if you want to create cd from that image file (/ iso file). But you should _not_ burn the .iso file to the CD (as a file) - you need to create whole CD image from the iso-file. Use slow burning speed, max 8x. After burning, check what you have on the disc - you should see multiple directories and files, not just one iso-file.

Here are some instructions (with alternative burning program for Windows):
[https://wiki.ubuntu.com/BurningIsoHowto]("https://wiki.ubuntu.com/BurningIsoHowto")

---

### Post by Fortigurn on 2005-10-09
Thanks.  I actually downloaded it as a compressed file, and unzipped it to a folder, and there it was with all the subfolders, no drama.  That's what I burned to a CD (I didn't burn the .iso file to a CD).

I've now burned the 'install' and 'live' files to separate CDs, and didn't set them to 'bootable', so I'll see what happens next.  :)

---

### Post by Kyral on 2005-10-09
A compressed file? Not an ISO? Wierd.....

I'd personally download ISOs only from Ubuntu BitTorrent Streams or cdimage.ubuntu.com

---

### Post by Fortigurn on 2005-10-09
[QUOTE=Fortigurn]I've now burned the 'install' and 'live' files to separate CDs, and didn't set them to 'bootable', so I'll see what happens next.  :)[/QUOTE]

Ok, neither of those disks will boot.  The 'live' CD will run if I double click on the 'start' application while viewing it in Windows, but it won't boot if I put it in the drive and restart my computer.  Neither of them will.

I burned these CDs without setting them to 'bootable' in any way.  Is there any way to burn this data to a CDROM and have that CDROM actually boot?

---

### Post by Kyral on 2005-10-09
Go to [http://cdimage.ubuntu.com/releases/](http://cdimage.ubuntu.com/releases/), download either a Colony out of 5.10 or an install out of 5.04, then burn it using the HOWTO that was posted earlier

---

### Post by heimo on 2005-10-09
As Kyral says, install and Live CDs are usually iso files - one of the reasons is that it's easy to get a bootable CD using disc image. I strongly recommend downloading iso file.

---

### Post by Fortigurn on 2005-10-09
[QUOTE=Kyral]A compressed file? Not an ISO? Wierd.....[/quote]

I downloaded it from this site (ubuntu.org), and it appeared as a WinRar file.  I unpacked it from there.

---

### Post by erikpiper on 2005-10-09
Weird.....

Ok, do you have Nero burner? What program do you normally use to burn CD's in windows? On the only PC in the house, there is only XP. (Grr) I open the iso with nero, select the burn speed, and burn. No boot options, exc.

Can you link me to where you downloaded your files?

And welcome to the Ubuntu community!

PS: I would actually reccomend the prerelease Breezy: (5:10) It is much more polished, and actually more reliable for me!

---

### Post by Fortigurn on 2005-10-09
[QUOTE=heimo]As Kyral says, install and Live CDs are usually iso files - one of the reasons is that it's easy to get a bootable CD using disc image. I strongly recommend downloading iso file.[/QUOTE]

I actually took them from [here](http://cdimage.ubuntu.com/daily-live/current/).  I see that they are ISO files, they just appear as WinRAR files once they've been downloaded (but they still have the .iso suffix).

I unpack them before I burn them.  As I say, the Live CD looks fine - the 'start' app runs fine inside Windows - but it won't boot.

When I burn these to CD, do I have to set the CD boot options to anything in particular?

---

### Post by Fortigurn on 2005-10-09
[QUOTE=erikpiper]What program do you normally use to burn CD's in windows? On the only PC in the house, there is only XP. (Grr) I open the iso with nero, select the burn speed, and burn. No boot options, exc.[/quote]

I'm using CDBurner XP Pro 3.

---

### Post by erikpiper on 2005-10-09
No specific settings. However, since install CD's are so sensitive, I like to burn them at least half the speed my burner is capable of, so there are no errors.

If you are in XP- Right click on the ISO. Open it with your burner. Burn. Reboot PC, Have fun!

Installation tips: (By the way, you need no more than 10 Gb for your Ubuntu partition when you intall- mine is 6 gb with plenty  of room. I would reccomend resizing you windows partition with gparted. (On the live cd) As for swap- make it the same size as your physical ram.)

---

### Post by aysiu on 2005-10-09
[QUOTE=Fortigurn]I'm using CDBurner XP Pro 3.[/QUOTE] Follow [these directions](http://www.cdburnerxp.se/help/english/burniso), then. WinRar, for some reason, just wants to unpack ISOs, but they really shouldn't be unpacked--they should be burnt as CD images. Again, see the directions I linked to.

---

### Post by heimo on 2005-10-09
[quote=Fortigurn]

I unpack them before I burn them. [/quote] 
Don't. You must not unpack / uncompress before burning, but you need to burn it as a disc image, not a regular single file.

---

### Post by NZ-Wanderer on 2005-10-09
Agree with the others, not using the ISO itself is what is causing you problems burning...

---

### Post by Fortigurn on 2005-10-09
Thanks a lot guys, I'll give it a go.  :)

---

### Post by Fortigurn on 2005-10-10
Thanks, I now have the 'install' CD burned, and it's 'installing'.  Let's see how this goes.  :)

---

### Post by Fortigurn on 2005-10-10
Dear me, first problem in the install - it seems to be having difficulty locating partitions or something.  I had prepared a Linux partition on the hard drive, but it can't seem to find it.  It hung when trying to do something with the partitions (I'm not sure what).

Now it tells me 'Kernel panic - not syncing: Attempted to kill init!' when I reboot from the CD.

---

### Post by heimo on 2005-10-10
How did you partition the disk beforehand? Which program? Do I understand correctly that the install CD no longer boots, but goes directly to kernel panic?

One thing you can do is verify the iso file:
[http://www.linuxiso.org/viewdoc.php/verifyiso.html](http://www.linuxiso.org/viewdoc.php/verifyiso.html)

And what I've heard is that there's also option to check the media at the beginning of install, but if you don't even get that far, either the CD or some piece of hardware / BIOS setting is now causing problems. Burn again... be sure to use slow speed - 4x or 8x at most.

---

### Post by Fortigurn on 2005-10-10
[QUOTE=heimo]How did you partition the disk beforehand? Which program?[/quote]

I used Partition Magic to create a 9GB Linux Ext2 partition on the drive.  It's a primary partition, and it's active.

> Do I understand correctly that the install CD no longer boots, but goes directly to kernel panic?

It boots, but doesn't continue the installation, it just goes to kernel panic.

> One thing you can do is verify the iso file:
[http://www.linuxiso.org/viewdoc.php/verifyiso.html](http://www.linuxiso.org/viewdoc.php/verifyiso.html)

And what I've heard is that there's also option to check the media at the beginning of install, but if you don't even get that far, either the CD or some piece of hardware / BIOS setting is now causing problems. Burn again... be sure to use slow speed - 4x or 8x at most.

Ok, thanks.  I burned it at 8x.

Am I supposed to partition the drive before installing, or during?

---

### Post by Fortigurn on 2005-10-10
Ok, I pulled the HDD out, threw it in my main rig, reformatted it with Linux Ext2, and put it back in the secondary rig.

Ubuntu install went fine, and I gave the rig a hostname.  Now it's sitting on 'Starting up the partitioner'.  It's at 52%, and it has been there for a few minutes now.

---

### Post by Fortigurn on 2005-10-10
Ok, restarted, CD booted up, and now we have 'Uncompressing Linux...  invalid compressed format (err=1)  -- System halted'.

---

### Post by Fortigurn on 2005-10-10
I cannot believe I have been at this for four hours now.  I'm back to the 'kernel panic' error.

---

### Post by heimo on 2005-10-10
Hmm... Those errors are not too promising. You can partition with Ubuntus installer, and that's probably the best way to do it. You could try to remove the partition you created - if the CD still doesn't boot, I'd probably try another cd drive (if you have one nearby). Or you could try with Live CD first.

---

### Post by Fortigurn on 2005-10-10
I have tried:

[list][*]  Reformating the Linux Ext2 partition using Partition Magic 7 (twice)

[*]  Deleting the Linux Ext2 partition and creating it using Partition Magic 7 (twice)

[*]  Deleting the Linux Ext2 partition and booting the Ubuntu install CD to see if it would partition the drive itself - the first time I did this it went fine until it reached 'Starting up the partitioner', managed to get to 52%, and then stuck, the second time I tried this I simply received the Uncompressing Linux... invalid compressed format (err=1) -- System halted' error

[*]  I have tried the Live CD, and will now try it again[/list]

I have one CD burner between 2 rigs, and it is a world of hurt swapping it out left right and center and rebooting, I can tell you.

---

### Post by Fortigurn on 2005-10-10
Ok, I've just deleted all partitions on my target hard drive.  Before I go any further, which is the best idea:

[list][*]  Use some program to partition the HD before putting it into the target rig and installing Ubuntu


[*]  Throw the HDD in as is, no partitions, and let Ubuntu's Partitioner sort it out


[*]  Something else[/list]

Thanks.

---

### Post by heimo on 2005-10-10
Those problems seem a bit random, but most likely subjects are bad media and bad drive. I've never suggested this before (on these forums), but ... take a break. :) Seriously, don't burn yourself, don't bang your head too hard. Go step by step and eliminate the possible causes, isolate the problem by making sure that it's not
[LIST]
[*]bad drive (is Live CD running flawlessly?)   
[*]bad media (check md5sum of iso file and burn again with 4x speed) [/LIST] I know it's pain to swap drives and disks all the time, but I'm pretty sure you have good chance of finding out what's causing it (two computers is a great help!) I'm pretty sure it's not about Ubuntu<->hardware compatibility.

Good luck! Keep us updated!

---

### Post by heimo on 2005-10-10
[quote=Fortigurn]Ok, I've just deleted all partitions on my target hard drive.  Before I go any further, which is the best idea:
[LIST]
[*]  Use some program to partition the HD before putting it into the target rig and installing Ubuntu
[*]  Throw the HDD in as is, no partitions, and let Ubuntu's Partitioner sort it out
[*]  Something else[/LIST]
Thanks.[/quote]

[LIST]
[*]  Throw the HDD in as is, no partitions, and let Ubuntu's Partitioner sort it out [/LIST]

---

### Post by Fortigurn on 2005-10-10
[QUOTE=heimo][LIST]
[*]  Throw the HDD in as is, no partitions, and let Ubuntu's Partitioner sort it out [/LIST][/QUOTE]

Beaut, I'll try that, thanks.  I really appreciate all the help here.

I may have found the problem.  Working through it all, I decided that it must be a hardware issue, because the software isn't even on the drive yet.

It seems that with all the plugging and unplugging of the HDD, the IDE ribbon head has become damaged (part of it is pulling away, and some of the internal pins are visible).  I tested the theory by putting the CDROM drive on this ribbon, and low and behold it wouldn't work.  I'm going to try another ribbon.

---

### Post by Fortigurn on 2005-10-10
Well, that was an interesting day.  Net result:

[list][*]  Two IDE cable heads destroyed as a result of constant unplugging/replugging of the HDD and the Pioneer 108


[*]  Two pins on my Pioneer 108 bent (as a result of the same experience), so that the drive will no longer function reliably[/list]

One time I made it as far as the Partitioner, but it couldn't find the HDD.  I rebooted after reseating the HDD, and it made it to the Partitioner again and then went to 'segmentation error!', which it repeated ad infinitum.  

By this stage it was clear to me that the bent pins on the Pioneer were causing the problem (sometimes I would get to the 'name the computer' section, sometimes I wouldn't even make it that far, the drive was completely unreliable).

Looks like I've written off a Pioneer 108 and two cables.  Not a bad result for 6 hours of tinkering.

Tomorrow I will purchase a dirt cheap CDROM drive, a couple more cables, and see what else I can destroy.

---

### Post by NZ-Wanderer on 2005-10-10
Hope things work better for you with the new hardware... :)

I'm gonna get myself a new HDD in the next couple of days ready for the official release on the 13th, I've played enuff with 5.10 now to know I gonna keep it..

---

### Post by Fortigurn on 2005-10-10
Thanks.  Yesterday was a shocker of a day, but hey these things happen.  Let's hope today pans out better.

If it turns out it wasn't simply the optical drive, I'm just going to bite the bullet and buy another copy of Windows.  :p

---

### Post by darius_underhill on 2005-10-11
[QUOTE=Fortigurn]I actually took them from [here](http://cdimage.ubuntu.com/daily-live/current/).  I see that they are ISO files, they just appear as WinRAR files once they've been downloaded (but they still have the .iso suffix).

I unpack them before I burn them.  As I say, the Live CD looks fine - the 'start' app runs fine inside Windows - but it won't boot.

When I burn these to CD, do I have to set the CD boot options to anything in particular?[/QUOTE]

Winrar has a weird feature that allows you to open ISO images as if they were archives.  As said in the previous posts, try getting hold of an ISO burning software such as Nero, I think they have a demo version.  And burn the ISO directly to the CD.

Never unpack it using Winrar. Part of the ISO is the actually code that will make the CD boot.

---

### Post by Fortigurn on 2005-10-12
Yesterday was even more interesting.  Here's the summary:

[list][*]  The install CD behaved just as badly on the brand new drive as they had in the old optical drive


[*]  I managed to rebend the pins on my old optical drive, and it now functions pefectly (one good result from yesterday)


[*]  After burning several CDs which all failed, I decided the media was probably at fault (Ritek -R), and bought some new media (Samsung +R)


[*]  I have burned install CDs on the Samsung +R media, at 6x, 4x, 2x, and even 1X, but I still have the same problem - I was able to partition my drive, and everything installs fine until I get to about 6% of the install process, when it hangs[/list]

The point at which it consistently hangs is during the installation of the main system components, during the mysterious 'validating zlibig' process.

I have downloaded the .iso twice now, in case it was a corrupted or damaged file.  I don't know what else there is to do.

---

### Post by Fortigurn on 2005-10-15
Several coasters later, the above problem remains.  I've tried two different optical drives (one brand new), and two different computers.

At this point it has been almost a week since I first attempted to install Ubuntu on this rig.  My wife is asking why her rig isn't up yet, since I told her it would be a day and a half.  She is asking why I don't just buy a copy of Windows, which we know will work.

I am starting to ask myself this question.  :(

---

### Post by NZ-Wanderer on 2005-10-16
Silly question, but when you downloaded the ISO's did you use normal download, or did you use a download manager?

---

### Post by Fortigurn on 2005-10-16
Normal download.  I haven't given up yet.  I'm trying Kubuntu (still downloading the DVD .iso).  If I can't get that working, I will look at Mepis.

---

### Post by erikpiper on 2005-10-16
Try shipit- snailmail, but the cd's will be good.

Good luck! This is not normal....

Try an Md5 sum checker to verify that the downloads are good. (I don't know how to in windows, mabe someone here can tell you)

---

### Post by NZ-Wanderer on 2005-10-16
If you are downloading via windows, use something like "flashget" - the normal windows downloader is notorious for not downloading files correctly, and all it needs is for one tiny glitch in the download for your whole download to become useless...
I personally used flashget for years, and I don't think I ever had a download fail while using it..
I has an ad banner if you don't pay for it, but hey you only gonna use it for a couple of downloads...
Just google it...

[QUOTE=Fortigurn]Normal download.  I haven't given up yet.  I'm trying Kubuntu (still downloading the DVD .iso).  If I can't get that working, I will look at Mepis.[/QUOTE]

---

### Post by Fortigurn on 2005-10-17
Today's efforts:

[list][*]  No luck at installing Ubuntu (it stalls at the mysterious 'validating zlibig' process)


[*]  Downloaded Mepis and after about half a dozen tries I managed to get it to install, apparently - but given that the HDD won't boot, it obviously didn't install correctly


[*]  Downloaded Kubuntu - the installer won't even get as far as the GUI, it erupts into a 'kernel panic' seconds after I ask the CD to install the 'default' configuration[/list]

I'm now trying Foresight.  When I have a few more idle hours to spare, I'll repeat my efforts with Ubuntu, Kubuntu, and Mepis.  I have to say this, Linux is certainly a hobby which requires lots of time.

---

### Post by Fortigurn on 2005-10-17
Well, Foresight just gave me the 'kernel panic' error also.  It seems to be a favourite habit of Linux distros.

---

### Post by Fortigurn on 2005-10-17
I cannot believe that this is a problem with the software - I've tried too many distros and install packages now.

I know it's not the optical drive or the media, so now I am checking my RAM.  It's about the only thing left I can think of.

---

### Post by Fortigurn on 2005-10-17
Well, I tried both sticks one at a time.  With one stick in, the computer won't even POST.  Ah, we have a culprit!

Not quite.  The other stick looks fine.  But when I ran the memory test which comes with Mepis, it failed on test 4.

Unfortunately this tells me nothing, because when I took a perfectly good stick from my other rig and placed it in this computer, it also failed the Mepis memory test (though I have no problems at all with that memory in the other computer).

In addition, with the stick from the other computer in it I'm still getting the same strange errors.  Something is very wrong, but I cannot pin it down.

---

### Post by NZ-Wanderer on 2005-10-17
one thing you could try...
Take one of he CD's you have burnt over to a friend and persuade him to let you install it on free space on his computer.. :)
this way you will see if it the CD or not..

---

### Post by Fortigurn on 2005-10-17
I have another rig which I can put together.  I'll try that.

---

### Post by bluck on 2005-10-17
[QUOTE=Fortigurn]I actually took them from [here](http://cdimage.ubuntu.com/daily-live/current/).  I see that they are ISO files, they just appear as WinRAR files once they've been downloaded (but they still have the .iso suffix).

I unpack them before I burn them.  As I say, the Live CD looks fine - the 'start' app runs fine inside Windows - but it won't boot.

When I burn these to CD, do I have to set the CD boot options to anything in particular?[/QUOTE]

dont unpack the ISO with winrar.
use your cd burning software to 'burn cd image'  or something similar.

the ISO file is basically a "snapshot" of the cd, so if you burn that directly, rather than unpacking with winrar, you will have a bootable disc.

also, you dont really need both the 'live' and 'install' discs.   the live disc will run the os directly from CD (and RAM) and the install disc will install the OS on your hard drive.

hope this clears things up for you.

---

### Post by Fortigurn on 2005-10-17
[QUOTE=bluck]dont unpack the ISO with winrar.
use your cd burning software to 'burn cd image'  or something similar.

the ISO file is basically a "snapshot" of the cd, so if you burn that directly, rather than unpacking with winrar, you will have a bootable disc.

also, you dont really need both the 'live' and 'install' discs.   the live disc will run the os directly from CD (and RAM) and the install disc will install the OS on your hard drive.

hope this clears things up for you.[/QUOTE]

Thanks, some of the other guys cleared that up a little way back.  I have now burned over 20 CDs, with four different distros.  None of them install properly.  Most of them hang at some point in the installation process.

Mepis managed to get through the full installation process (allegedly), after about a dozen tries (and many hangs), but unfortunately refuses to boot.

I have tried two different machines.  Later today I will see if I can try a third.  But after just over a week, 4 distros, 20 CDs, and many downloads, I do not have a great deal of confidence that Linux is for me.

---

### Post by NZ-Wanderer on 2005-10-17
Well I am pretty new to it myself, but after scrolling around quite a few forums, I have never heard of this problem before....

---

### Post by Fortigurn on 2005-11-06
Well guys, you can be proud of me.  I persisted until it all worked out.

I actually went to the extent of purchasing a new Shuttle barebones system, and throwing all the old components into it (suspecting the motherboard of the old system was faulty).

Whatever the status of the old Shuttle board, the new system (with the old components), is working perfectly.

And I installed Ubuntu in no time, with complete success.  :smile:

---

### Post by NZ-Wanderer on 2005-11-06
Congratulations, real glad you got it figured out.. - Pity about the old board tho.. - But it good you found out now rather than later.. :)

---

