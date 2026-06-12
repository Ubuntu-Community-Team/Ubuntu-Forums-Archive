---
title: "GRUB error 21 on new install"
date: 2007-05-16
forum: Absolute Beginner Talk
---

### Post by Mode_Locrian on 2007-05-16
Hi all,

I apologize for what probably looks like a relatively common question, but I've spent the last few hours trying to figure it out myself scouring forums and stuff with no luck, so maybe someone here can help.

Here's my situation:  I want to dual boot between Ubuntu 7.04 and Windows XP on my desktop (XP is currently installed).  My hard drive situation is this:  I have two drives in RAID0 (promise 378 raid controller), and this is where XP is installed.  I also have an additional SATA hard drive that I'm currently using for storage.  My though was that it would be easiest to simply shrink the partition on this latter drive and install Ubuntu there (so Ubuntu and windows are installed on seperate drives).

So far, so good.  Installation goes great.  However, when I restart, I get GRUB error 21, with no options or anything (or than restarting) to get out of it.  I understand that this error means that Ubuntu is not finding the hard drive that it's looking for.  Ok, so my first thought was, well, my RAID0 (on which Ubuntu is *not* installed) is set as the primary boot disk, so I'd better change that, so that my other SATA disk is primary.  If I make that change, though, I get an "Operating System not found" error.

Any suggestions as to what to do here?

---

### Post by PMatt on 2007-05-16
I have the same problem and started a thread just a little bit ago. I did a quick search, but couldn't find anything helpful. I'll try again.

---

### Post by gn2 on 2007-05-16
If you can get a "Boot device selection menu" by pressing F8 or whatever at boot time, this is one method that may be useful: [http://ubuntuforums.org/showthread.php?t=275728](http://ubuntuforums.org/showthread.php?t=275728)

---

### Post by Mode_Locrian on 2007-05-17
> **gn2 said:**
> If you can get a "Boot device selection menu" by pressing F8 or whatever at boot time, this is one method that may be useful: [http://ubuntuforums.org/showthread.php?t=275728](http://ubuntuforums.org/showthread.php?t=275728)

Thanks, gn2!  That thread you linked me to was extremely helpful.  In case anyone is wondering, here's what I ended up doing (and now it works perfectly):

First, I went into BIOS and made sure that my SATA drive (*not* my RAID) was set as the primary boot hard disk.
Then, I booted Ubuntu off of the live CD and reinstalled it.  I installed it to my SATA drive, and at the very end (step 7, I think) I clicked the "advanced" button and made sure that GRUB was installed to hd0.  I think what happened before was that GRUB got installed to my RAID while Ubuntu was on my other drive, so when it tried to boot, I'd get problems regardless of which drive I tried to boot from.

Now, my machine boots to Ubuntu by default.  If I want to boot into Windows, I can just hit F8 while booting and tell my machine to boot from my array instead.  It works like a charm.  Yes, it's not a slick little bootloader UI, but it works just fine for me.

Thanks for the help.

---

