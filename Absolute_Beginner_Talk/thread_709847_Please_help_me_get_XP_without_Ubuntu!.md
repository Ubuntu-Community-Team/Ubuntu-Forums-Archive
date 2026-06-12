---
title: "Please help me get XP without Ubuntu!"
date: 2008-02-27
forum: Absolute Beginner Talk
---

### Post by electrosaab on 2008-02-27
I thought I was doing things right when I installed Ubuntu 7.x on a completely new hard drive with the intention of only using it by changing boot sequence in the Bios.

Little did I know that it would modify the boot sector on my main XP drive!

I like the OS (have it on another machine by itself) and don't mind having it on the computer, except that it has now made me a slave of having all my drives installed or XP will not load up.  Today I tried installing a new SATA DVD burner on my second SATA drive plug and as long as it is connected XP just goes to a blue screen for a second and reboots.  Take out the drive it starts.  I tried switching the sata channels but that did not help.   My main XP drive is an IDE master and I would have never given permission for it to be modified had I known it would mess with the boot sector.  I would have just disconnected it, but nobody warned me of the potential disaster in waiting.

The problem in all of this is I need to be able to put different drives on my computer from time to time since I use it for data recovery, music and other things.  If I take the SATA Ubuntu drive off it won't go to XP at all, just the boot menu choices.  

Please somebody tell me an EASY way to get rid of this problem without a long spastic bunch of code that is meaningless to me from the command line.  I simply don't have time to fool around learning the intricate details of Linux at this time.

And, I don't care if Ubuntu still runs after this is over.  I can reinstall it another time, but need the drive back and my XP functioning able to boot itself again!  If something happens to any of my hardware my access to very important stuff is going to get lost!

HELP!

---

### Post by neurostu on 2008-02-27
Ok the first thing you should do is look to see if you can access the XP partition from ubuntu. If you can, you should backup ALL the data that you need. Then you should proceed with the process to make XP bootable again.

But I don't know enough to help you with that :-(

---

### Post by anewguy on 2008-02-27
Please see the following how-to:

[http://ubuntuforums.org/showthread.php?t=508927](http://ubuntuforums.org/showthread.php?t=508927)

---

### Post by dstew on 2008-02-27
If you have a Windows disk, boot it, enter the recovery console and issue the fixmbr command. See the [Microsoft support page]("http://support.microsoft.com/kb/307654").

---

### Post by electrosaab on 2008-02-27
Thanks everyone!  I am going to do the fix mbr and see what happens.  I want everyone to know that I do love Ubuntu, just not on my XP machine!  The machine I just sent this reply on has been running 6.06 for close to a year now.

I have it on a notebook pc  too and have no intention of getting rid of it.  The fact I can get a response so quickly in this forum speaks to the great support it is receiving.

I am not a fan of Windows. In fact I hate VISTA the new piece of junk OS Microsoft just came out with. We are still forced to use windows for some things...for now at least.

I just want to keep the two apart and not have them interact.

Electrosaab

---

### Post by asmoore82 on 2008-02-27
Too late now, but ...

there is an "Advanced" Options tab somewhere during the install process that asks
where you would like GRUB's stage 1 to be embedded. But my advice would be to do it
the cheezy but breezy way and just unplug the XP drive during Ubuntu installation :D.

---

### Post by electrosaab on 2008-02-27
> **asmoore82 said:**
> Too late now, but ...

there is an "Advanced" Options tab somewhere during the install process that asks
where you would like GRUB's stage 1 to be embedded. But my advice would be to do it
the cheezy but breezy way and just unplug the XP drive during Ubuntu installation :D.

Well I know that now of course!  Next time I want a dual boot system I will do that.  I figured it was like Windows and would setup on the drive I told it to.  Of course I didn't know about Grub's modifications at the time.

---

### Post by asmoore82 on 2008-02-27
> **electrosaab said:**
> Well I know that now of course!  Next time I want a dual boot system I will do that.  I figured it was like Windows and would setup on the drive I told it to.  Of course I didn't know about Grub's modifications at the time.

I was surprised by your findings on the installer's behavior at first;
but then I realized that it must always default to the drive it believes is booted first by the BIOS or else
it would lead to a lot of "I just tried to do a dual boot install; where the heck did Ubuntu go?" situations.

---

### Post by electrosaab on 2008-02-28
> **anewguy said:**
> Please see the following how-to:

[http://ubuntuforums.org/showthread.php?t=508927](http://ubuntuforums.org/showthread.php?t=508927)


Worked like a Champ!  Fast and easy to do!:)

---

