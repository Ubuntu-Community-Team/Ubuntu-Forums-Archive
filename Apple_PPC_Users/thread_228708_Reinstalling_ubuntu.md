---
title: "Reinstalling ubuntu"
date: 2006-08-03
forum: Apple PPC Users
---

### Post by Lurcher on 2006-08-03
How can I go about reinstalling ubuntu 6.0.6 on an iMac G3? Ubunutu worked fine for me till I attempted to uninstall Evolution (the email client) with the Synapse Package Manager.  I suspect (primarily because after I log in I get a–while esthetically pleasing–a somewhat intimidating chocolately screen of blankness) that I removed something that I should not have, and want to start from scratch.

The thing is, I am able to log in just fine.  It is after the log-in that the chocolate nothing happens.  

As a result I want to attempt a wipe and reinstall of ubuntu (this seems logical to me, though based upon a knowledge base that is at the moment somewhat lacking).

Any suggestions as to how I can do this would be most appreciated (and believe it or not, this is actually a way that I learn about such things, so at this rate I should be approaching ubunutu mastery very soon;)

---

### Post by stmiller on 2006-08-03
Hm. Removing Evolution may have zapped some needed gnome packages to make gnome work.

If you can get to a command line after it boots, (try hitting cntrl+option F1, or cntrl+option F2). Log in, the try sudo apt-get install evolution.

That may repair everything. Or to do a clean install (if you don't need anything on your hard drive) you can always boot from the CD and do a fresh install, which will erase all of you data.

---

### Post by Lurcher on 2006-08-03
I can reach the command line just fine.  I'll give your suggestions a try.  I thought that I should mention that this board reminds me a lot of the Apple boards: Namely there are quite a few knowledgeable people about, most of whom are very helpful.

By the way, is there any way I can run routine maintenance on ubunutu 6.0.6 (via the command line, I assume).  I run maintenance on my G5 on a regular basis and don't want to neglect my ubuntu G3.

As always, thanks for the assist (as well as any assists to come;)

---

### Post by Lurcher on 2006-08-03
Reinstalling Evolution didn't reverse the problem, so how would I do a fresh install?

---

### Post by zachws on 2006-08-03
Run the installer off of the livecd, like you did the first time. However, go through until the partitioner starts... delete these three partitions:
bootstrap
swap
main linux partition

Then go BACK in the installer until you can select to "install to largest free space"

---

### Post by Lurcher on 2006-08-03
I am starting up from the ubuntu CD, but I cannot seem to get to an 'install' option.

Is there a command that I can use to access it?

---

### Post by zachws on 2006-08-03
If you can't load Ubuntu... type 'install' at the boot prompt instead of the default 'live' (which is the same as just pressing enter).

You are on an old-school imac g3... so at the prompt press tab to see your options for booting into ubuntu. Have you ever been able to get to the desktop via the livecd?

---

### Post by Lurcher on 2006-08-03
Yeah, everything was fine before I started playing with Evolution.

---

### Post by linear on 2006-08-03
Before you re-install, it wouldn't hurt to check for the [Date Bug]("https://help.ubuntu.com/community/UbuntuDateBug"). (Might be a coincidence that the problem started when you removed Evolution.)

You could also check for broken dependencies from the command line:

**sudo apt-get check**

Might be able to save the trouble of a re-install.

---

### Post by Lurcher on 2006-08-05
Nope, the date checks out just fine.  When I ran sudo apt-get check the message I got back was:  Reading package list...done; Building dependency tree...Done.

---

### Post by Lurcher on 2006-08-05
I am actually having difficulty with the install/reinstall.  Using 'install' gets me the message: missing file operand.

At this point a reinstall (since I haven't actually installed anything other than ubuntu 6.0.6 at this point, so there's nothing for me to lose) would be the best thing if anyone can, step by step, provide me a means to do so.

Keeping in mind that 'install' from the command line doesn't work.


Thanks

---

### Post by Lurcher on 2006-08-05
'Stopping RAID monitoring services...' also reported a Fail, when my system underwent a reboot, if that helps.

---

