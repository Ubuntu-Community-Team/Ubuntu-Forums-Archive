---
title: "LiveCD didn't do its thing..."
date: 2005-12-16
forum: Absolute Beginner Talk
---

### Post by Bartender on 2005-12-16
I'm not freakin' about this cause I've got a spare Pentium III computer that'll get the Ubuntu install in the next week or two.  But the mailed (not downloaded)  CD's are just sittin' here next to me and I thought, "What the hey".  Tried the LiveCD in my M$ machine after changing boot sequence to DVD drive.  Nothing.  I heard the drive animate a few times, then the computer waited about a half minute (funny how those half minutes can seem like an eternity) then it started up W2K.
Went back into BIOS and disabled the HDD from the boot sequence.  Restarted.  Same thing; some false starts from the DVD drive, then the wait, but this time of course I got a message about choosing a boot device and pressing a key.
This is not the introduction to the Ubuntu learning curve that I'd imagined.  Any thoughts?  Did I do something obviously wrong, did Ubuntu detect some basic incompatibility and give up, or what?

EDIT:  Er, um, five minutes of pokin' around on the Beginner's Forum brought up a thread from today where Aysiu mentioned that the LiveCD won't work with NTFS.  Sheesh, why didn't I figure that out before?  I double-checked, sure enuf, my W2K files are NTFS.  Everyone's W2K & XP machines are NTFS, aren't they?  It just never occurred to me that the LiveCD wasn't gonna work on most modern computers...

---

### Post by Mustard on 2005-12-16
I think the comment you read is referring to the liveCD not being able to do certain functions with regards to the ntfs filesystem.  LiveCd's are quite capable  of running on XP and W2K machines that have ntfs filesystems.

This would mean that the error is something else.  When you say you disabled the boot from hard drive option in BIOS, what was the next option that was available for the system to use?

Normally there would be a 'boot order' configuration of somekind in BIOS in which you could decide in which order the BIOS will look for a bootable device.  Changing the order so that it checks the CD before it checks the hard drive is normally how you would go about it.

Not being able to see your screen, I'm guessing a bit as to what you might have done, but I would re-enable the boot from hard drive option, and look for another option somewhere that deals with what order the devices are booted in.  Ideally it would be floppy first, CD second and hard drive third.

---

### Post by Bartender on 2005-12-17
Hi, Mustard -
Sorry, I didn't explain myself very well.  I'm fairly competent with BIOS settings, if only because I've made all the wrong entries at one time or another...  I set the DVD drive as 1st in boot order, put the HDD 2nd.  Floppy last.  Although I heard the DVD drive making some noises, the CD was ignored and the computer moved on to the HDD.
So I went back into BIOS and actually took the HDD out of the boot order by disabling it.  Didn't change the order - DVD drive still 1st.
Saved changes, restarted, same noises from the DVD drive, then a pause, then I got the "No boot device" or something similar message.  Not surprising since there was nowhere else for the computer to go.  Went back into BIOS, reset the boot order to the way I like it (HDD 1st) and went to the forums.  That's when I thought I understood Aysiu's message as indicating that the LiveCD wouldn't work under NTFS.  I thought that was awfully weird.  Thanks for clearing it up.  If you've got some other suggestions I'd be happy to try 'em.
EDIT:  Since I've got 5 CD's I tried another one.  Made absolutely sure that the DVD drive was 1st by going back into BIOS a second time after entering the change and restarting.  Restarted again, same thing as before.  I watched the light on the DVD; it flashed several times before the computer moved on to the HDD

---

### Post by aysiu on 2005-12-17
[QUOTE=Bartender]
EDIT:  Er, um, five minutes of pokin' around on the Beginner's Forum brought up a thread from today where Aysiu mentioned that the LiveCD won't work with NTFS.[/QUOTE] Huh? When did I say that?

First of all, booting the live CD should always work, no matter what filesystem you have installed--NTFS, FAT32, Ext3, Reiserfs, HFSplus, HFS...

I've booted the live CD on an old FAT32 Windows 98 computer, a newer NTFS Windows 2000 computer, a semi-brand new NTFS Windows XP computer, an HFSplus Mac Powerbook, and an HFS Mac Powerbook.

The filesystem has nothing to do with booting the live CD. It's all about the BIOS settings, the drive functionality, and the CD's integrity.

The only limitation I know of is being able to *write* to NTFS from Linux, but that's not unique to the live CD.

P.S. Can you point me to the post where I said the live CD wouldn't work with NTFS? If I actually said that, I'll revise the post to be correct. If what I said was misleading, I'll try to rephrase it to be clearer. Thanks.

---

### Post by Bartender on 2005-12-18
Hi, Aysiu -
I'm sorry but I can't find the thread.  I shoulda wrote it down.  Before getting involved on this forum I'd only posted a dozen times total in any forums, so I haven't gotten in the habit of backing myself up by jotting thread numbers in a notebook or something similar.  
I think we can assume that I misread your message.  It doesn't seem likely that you would have miscommunicated a basic fact like the LiveCD's ability to run across all platforms.  I apologize for that.
So how come my computer looks at the LiveCD, thinks about it for ten seconds, then moves on?  I built the computer, so it'd be easy to say that I screwed something up, but it runs like a champ.  The Sony DWD26A/B DVD drive has never balked at reading any kind of CD - stamped, home-made, multi-session, whatever.  I've dinked around with BIOS settings enuf to know how to set the HDD behind the DVD.

---

### Post by Gustav on 2005-12-18
Maybe your LiveCD is broken in some way. 
It happens even with the shipped ones. :(

---

### Post by aysiu on 2005-12-18
[QUOTE=Gustav]Maybe your LiveCD is broken in some way. 
It happens even with the shipped ones. :([/QUOTE] I can verify that. The official burnt ones are not always the best (sad to say... but they are free... and probably mass-produced and burnt at high speeds).

---

### Post by Bartender on 2005-12-18
O.K., then, we'll run every LiveCD and see what happens.  Quadruple-checked the boot order, then started plunking LiveCD's in the tray.  Every single one of them the same - the drive starts to spin up, then stops, spins/stops, the green LED blinks several times, spins/stops, machine gives up.
The ASUS P5GDC-V mb has one PATA bus and a buncha SATA plugs.  The HDD is SATA so the DVD drive has PATA all to itself.  So no weird slave/master complications.  
It seems to me that the problem is with my hardware, not the CD's.  I'll test the CD's on a couple of other computers in the next few days.
If this was a problem that cropped up a lot I'd just write it off but I get the impression that the LiveCD's are pretty reliable.

---

