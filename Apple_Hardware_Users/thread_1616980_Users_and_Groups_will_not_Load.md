---
title: "Users and Groups will not Load"
date: 2010-11-08
forum: Apple Hardware Users
---

### Post by entwash on 2010-11-08
I recently installed 10.10 on a Mac Powerbook G4.  Everything seems to be working ok, except I cannot access the Users and Groups.  If I try to launch it from the terminal I get the following error: "Glib-GIO-ERROR **: Settings schema 'org.gnome.system-tools.users' is not installed"

This is a clean install, with no changes made to the system.  I then ran all the waiting updates and am still experiencing this problem.

Any ideas on how I can resolve this?

Thanks.

---

### Post by Cheesehead on 2010-11-08
First, open a terminal and try the command 'users-admin' (don't use sudo). On many Ubuntu systems that will open the Users and Groups control panel without all the desktop environment overhead.

Second, please do open a Launchpad bug for this behavior.

---

### Post by entwash on 2010-11-08
That is what I had tried, when I got the error, sorry for not being more precise.  If I try to launch it from the Menu - it looks like it is starting (shows up at the bottom on the window bar) but then after a few seconds disappears.

Where do I go to submit a Launchpad bug?  sorry I am a newbie to all this...

---

### Post by Cheesehead on 2010-11-09
users-admin is part of the gnome-system-tools package.

First, try reinstalling gnome-system-tools.
```
sudo apt-get install gnome-system-tools --reinstall
```
and post all cryptic error messages here. Then try users-admin again.

If that doesn't work, we'll move on to more invasive and radical solutions.

---

### Post by entwash on 2010-11-09
I have tried what you suggested, and it ran with no errors (downloaded, unpacked, processed triggers, rebuilt /usr/share/applications/desktop.en_CA.utf8.cache, setup the gnome-system-tools (2.32.0-0unbuntu1) and stopped).

When I run users-admin I am stull getting the "Glib-GIO-ERROR **: Settings schema 'org.gnome.system-tools.users' is not installed
Aborting...
Aborted"

Any further help is greatly appreciated - and while I am a newie to Linux I am more than willing to wade into whatever you want to try to help me get this working :)

I have submitted a bug report as well: 
[https://bugs.launchpad.net/ubuntu/+source/gnome-system-tools/+bug/672873](https://bugs.launchpad.net/ubuntu/+source/gnome-system-tools/+bug/672873)

---

### Post by Cheesehead on 2010-11-09
Good job on the bug!

The triager asked the same questions I was going to. And I agree with his ranking of your severity.

Hmmm...Really deep Glib stuff like that is beyond me. I don't even use Gnome, so I'll bow out here.

A quick search showed a few related bugs, there may have been a packaging mistake last summer...or not. But reinstalling (a command convenient fix) did not help them either.

The real kicker about this particular bug is that it's very hard to reproduce - your system fails reliably while others work reliably, and the puzzle is to figure out what is different by playing twenty questions in the dark.

Thanks for you patience, and hang in there. It may take months, but the community will figure it out.

---

### Post by bwpopper on 2010-11-11
I'm having the same issues on five different iBook G4 machines I am setting up for some people who bought them second-hand.  It's been driving me bonkers.

---

### Post by linuxopjemac on 2010-11-12
all these bugs in Ubuntu/PPC would make me crazy ;)

---

### Post by fleeze on 2010-12-10
I had exactly the same problem.  The fix contained in the following bug report resolves it completely for me:

[https://bugs.launchpad.net/ubuntu/+source/glib2.0/+bug/672873](https://bugs.launchpad.net/ubuntu/+source/glib2.0/+bug/672873)

You might want to try it......

---

