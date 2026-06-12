---
title: "[SOLVED] Power issues - off and possibly on"
date: 2007-11-05
forum: Absolute Beginner Talk
---

### Post by expatCM on 2007-11-05
The computer was working fine with Feisty.  A clean install was performed to put Gutsy in place.

The main problem is that the computer will not power off on shutdown.  The computer closes Ubuntu cleanly but leaves a black screen with a blinking white underscore in the top left corner of the screen.  This is as far as it gets .... the fans all stay running.

How do I diagnose / fix this problem?

Also when the computer is powered on, the Ubuntu logo appears on screen.  Then a white rectangle appears with the words "Input Signal Out of Range".  This rectangle disappears as Ubuntu moves on with the loading.  How can I get rid of this event?

---

### Post by kyphi on 2007-11-05
The first item I would have a look at would be power management under preferences.

Next I would check that all peripherals are firmly connected.

Next I would check, by removing and reseating, internal modules such as RAM, graphics card, etc.

Next I would check the BIOS, perhaps loading failsafe configuration.

One of the above must surely fix the problem.

---

### Post by expatCM on 2007-11-07
Well I have been through your list and nothing helped :(

I then powered down and AutoFSCK cut in and proceeded to check the file system.  This is a dual boot machine and AutoFSCK gave a message that one file on the Windows FAT32 partition was a problem and needed either renaming or deleting.  So I let the program rename and then AutoFSCK ran normally and this time powered the computer completely off.

So I went into Windows land where I have not been for a long long time and deleted the temp files, defragmented the drive and generally tidied up.

Next boot back to Ubuntu and then test powering down normally.  This time it went straight down.

So my conclusion is that either the file which AutoFSCK identified or the general clean up has had an impact.  It does seem that the Windows partition was something to do with this problem though...

---

### Post by kyphi on 2007-11-07
Thanks for posting that summary, expatCM.

I have never come across that.  I have always thought that the integrity check was for the linux system only.  By AutoFSCK, I assume that you meant fsck -a.

I keep a bare-bones version of XP on a separate drive without internet access.

Anyway, good that you are able to shut down properly again.

---

### Post by expatCM on 2007-11-07
no ... I mean this
[https://wiki.ubuntu.com/AutoFsck](https://wiki.ubuntu.com/AutoFsck)

basically you change fsck running to the end of a session where it will check and then unattended power off.  Saves time rather than waiting for ever for fsck to run when you power on.

---

### Post by kyphi on 2007-11-07
Thank you for that information and the link.  Seems like a good idea.

---

