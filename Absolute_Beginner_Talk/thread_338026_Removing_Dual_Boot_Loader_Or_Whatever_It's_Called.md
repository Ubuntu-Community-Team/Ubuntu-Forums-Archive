---
title: "Removing Dual Boot Loader Or Whatever It's Called"
date: 2007-01-13
forum: Absolute Beginner Talk
---

### Post by Tryckee on 2007-01-13
Here's the story in a nutshell:

I burned the Ubuntu CD, placed it in my CD, and booted up to the Live CD.  I wanted to install it on my computer and after answering a few questions, when it came to pulling the string thought better of it and cancelled.  Rebooted the system and XP would not re-start no way no how: it would just look like it would be loading but the XP logo screen with the progress bar is as far as it would go.  I pulled what little hair I have left out trying to diagnose just what the heck was wrong. ](*,)  And then it struck me that my lapse of sanity in wanting to install Ubuntu could be the problem. :-k  I put the CD in and rebooted, chose the last option to boot from my HD and *voila* XP booted up.

This is absolutely ridiculous - that install program messed with my system and gave me the illusion that I could cancel and all would be well when in fact it most definitely would not.  I am terribly annoyed at this.  I just want this shyt removed from my system so I don't have to have that CD in all the time to reboot.

I'll save Ubuntu for another machine - not the one where I am productive.

Anyone know how to help me remove the boot loader or whatever it's called from my system?

Thanks

---

### Post by deanlinkous on 2007-01-13
Well.....I am not sure it was a lapse of sanity or a moment of clarity but either way you can look in the mirror at who is to blame.

TO remove the bootloader there are  few methods...
boot from win98 boot floppy, boot cd or similar and use the command
**fdisk /mbr**

Also using the recovery console of winXP you can use the commands
**fixboot**
and
**fixmbr**

all at your own risk and responsibility of course ;) have a nice day....

---

### Post by k|d&lt;FuNkY&gt;FrY on 2007-01-13
If the previous suggestion doesn't do the trick, you could always try and set your XP box to the 'Last Known Good Configuration' --

---

### Post by sean_ on 2007-01-13
Oh, guess it wasn't my english <_<. Dean, I have no ******* CLUE where you got the suggestion of using the windows 98 boot disc from. The only part I know is to go into windows XP recovery mode and do fixmbr or whatever the command Dean said.

---

### Post by deanlinkous on 2007-01-13
My suggestion for the 98 boot disk is from experience and IMO it is often the easiest route as well as the fastest route unless you already have the recovery console installed and ready to go... Assuming you keep a win98 boot floppy or cd laying around. ;)

---

### Post by vortech on 2007-01-13
Yep, a windows 98 boot disk is all you'll need.  As stated, just fdisk /mbr.  If that doesn't work, run FDISK and make sure that your XP partition is set to active.

---

### Post by Tryckee on 2007-01-13
Well thanks fellas.  I knew about the Recovery Console fixmbr but just wanted to know if there was another way to do it.  My sanity is almost restored. :)

---

### Post by Tryckee on 2007-01-13
OK, I did the **fixboot** and **fixmbr** commands from the prompt in the Windows Recovery Console - but no fricking joy!  i still need the Ubuntu Live CD to boot into XP.  Now I'm pissed! There has got to be a way of removing this bootloader/grub whatever it's called from my system so that I can get back to business.  What a nightmare!

Any other suggestions would be welcome at this point.

Thanks. :mad:

---

### Post by kvonb on 2007-01-13
Ring Microsoft, I'm sure they will be happy to help you.

---

### Post by Tryckee on 2007-01-13
> **kvonb said:**
> Ring Microsoft, I'm sure they will be happy to help you.

Don't be a smartass!  If you can't help then shut the f**k up and go away!  This is why Linux will always be on the fringe...twits like you and programs that take over people's computers.  At least with Windows none of this crap ever happened.

Thanks!

---

### Post by confused57 on 2007-01-13
You might try the Super Grub Disk:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

See the section on "Situations Where Super Grub Disk is useful"...

---

### Post by qamelian on 2007-01-13
> **Tryckee said:**
> Don't be a smartass!  If you can't help then shut the f**k up and go away!  This is why Linux will always be on the fringe...twits like you and programs that take over people's computers.  At least with Windows none of this crap ever happened.

Thanks!

Y'know, you could try being a little less confrontational yourself. Less face it, intimating that installing Ubuntu requires a bout of insanity isn't likely to endear to folks on a forum devoted to Ubuntu! As far as complaining about programs that "take over people's computers", pull the other one, it's got bells on. Windows and Windows applications are the king of this sort of behaviour. It's one of the reasons I abandoned Windows for any serious use 8 years ago and now only use it for games.

---

### Post by ucsdrake on 2007-01-13
personally i find it funny that he's making such remarks to the most likely group of people that would help him

and as a side note... programs that take over peoples computers are called Operating Systems and include programs such as Linux, Windows and OSX

---

### Post by Frank Golden on 2007-01-14
> **ucsdrake said:**
> personally i find it funny that he's making such remarks to the most likely group of people that would help him

and as a side note... programs that take over peoples computers are called Operating Systems and include programs such as Linux, Windows and OSX
Thank you gamellian and ucsdrake. I am a devoted "insane" Ubuntu/Linux user. You know I am amazed that the folks here are still trying to be helpful. I gave up on this guy early on in this thread.
It is too bad he is letting his emotions get the better of him. It sounds like he thinks we're the enemy and it obviously pains him to ask us for help.
Oh well, too bad.

---

### Post by Bjoeboo on 2007-01-14
This guys a hoot.  But since Ubuntu people are better than Windows people I'll help him out.  Dude, Go to bootdisk.com and burn the Windows 98 bootable CD image, make a bootable disk (floppy or CD doesn't matter)  after you boot to it type fdisk /mbr  That will overwrite the master boot record back to Windows.  If that doesn't fix it you can use 3rd party tools like Acronis Disk Director, or Powerquest Partition Magic to view (in a pretty Windowsesque GUI) and correct your partitions . Possibly the Windows partition isn't set to Active & Primary needed to be bootable, also possible you've got new linux partitions preceeding the Windows ones so your windows boot.ini now points to wrong partition. These can also be fixed in fdisk utility on the Win98 disk but its harder to work with since you don't get a pretty gui.  Of course you could also use gparted for free but that would be on the Live CD....;)

---

### Post by deanlinkous on 2007-01-14
> **Tryckee said:**
>  At least with Windows none of this crap ever happened.

Thanks!

Really....

Let us reverse the situation and see what happens. I installed Ubuntu then in a true moment of insanity I started installing windows.....

Go ahead and try it and see what you end up with.....

---

### Post by tsav87 on 2007-01-14
> **Tryckee said:**
> Don't be a smartass!  If you can't help then shut the f**k up and go away!  This is why Linux will always be on the fringe...twits like you and programs that take over people's computers.  At least with Windows none of this crap ever happened.

Thanks!

I just switched my entire Windows XP ME over to Ubunto 6.10 Edgy and I'm lovin' it.

Your problem wasn't a programing error, but a user error.  Don't play with something unless you know what it is and how to operate it, you should have done some research before installing it.

If all else fail, dual boot.

---

