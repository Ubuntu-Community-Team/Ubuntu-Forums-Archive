---
title: "I'm back and this time it's personal ..."
date: 2007-10-18
forum: Absolute Beginner Talk
---

### Post by castalla on 2007-10-18
okay guys ... I waited for the production release which I installed.

Fired it up (online via the wires) - went into the Restricted Drivers Manager, enabled the broadcom firmware, And ... got the message that the software source for bcm43xx-fwcutter  is not enabled.  That's it, no further for you, my friend!  No clues about what to do next.

So has anybody got any easy to follow instructions on what I do next?

Or does anybody know how I could get a persistent Ubuntu running in VMware Player?
That's what I'm using now (VMware Ubuntu) which gives me wifi via (oops) Vista.

---

### Post by lbelloq on 2007-10-18
Check if the universe and multiverse repositories are enabled (Sytem-Administration-Software Sources I think).

---

### Post by lazyart on 2007-10-18
> **castalla said:**
> okay guys ... I waited for the production release which I installed.

Fired it up (online via the wires) - went into the Restricted Drivers Manager, enabled the broadcom firmware, And ... got the message that the software source for bcm43xx-fwcutter  is not enabled.  That's it, no further for you, my friend!  No clues about what to do next.

So has anybody got any easy to follow instructions on what I do next?


Just like it says... the source is not enabled, so you need to enable it.

Open Synaptic Package Manager (System>Administration>Synaptic), go to Settings>Repositories and put a check mark in the first four boxes.  Then close that window and hit Reload in the main window.  That will activate the software source.  Close Synaptic, then go to Restricted Package Manager and install away.

---

### Post by castalla on 2007-10-18
Well ... here we go again.

I did what you said AND it worked!  The cutter was installed, etc.  I shut down and did a restart.

Big problems ... at login I get the following warning panels:

1.
Gnome session manager unable to lock the file /home/ubuntu/ICEauthority. Please report this as a Gnome bug.

2.
Session only lasted less than 10 seconds. (more)

I managed to login to the failsafe terminal BUT haven't a clue what to do there!

Oh dear ... not looking good at all.

Big help needed.

---

### Post by castalla on 2007-10-18
Please check my original Personal post!  I need help!

---

### Post by Technoviking on 2007-10-18
Where is your original post?

---

### Post by ubunoobie on 2007-10-18
could you link to it please?

---

### Post by earobinson on 2007-10-18
a link would also be nice, also there is no reason to repost people will get to it, and if you have to *bump* it

---

### Post by gigaferz on 2007-10-18
you could try typing "xstart" or "xinit", and if it works (ill be a nother terminal-like window) type "gdm "
right now im testing 7.10 also there is not enough debs from getdeb  and i had a few bumps while trying the live cd.....
maybe you need to do everything with "sudo" before any command you enter...

lso it'll be
   you@home:$sudo xinit

---

### Post by Technoviking on 2007-10-18
Threads merged

---

### Post by dhruva023 on 2007-10-18
if you are running from live cd, then this might happen,

i had to install ubuntu to make my wireless work

---

### Post by castalla on 2007-10-18
I'm trying to use the pendrivelinux method.  Ubuntu is on the usb with a casper-rw partition.  I'm not sure it's actually saving anything.  I will persevere and report back.  I got a warning about reposting but my experience is that posts sink with a very short stream of bubbles to follow!

---

### Post by lazyart on 2007-10-18
looks like your username is ubuntu, so try```
sudo chown -R ubuntu:ubuntu /home/ubuntu
```

What I've heard about automatix is that it is well-intentioned but problems do arise.  For the moment, remove automatix:```
sudo dpkg -r automatix2
``` and get yourself back into the GUI.  From there we can get the media packages easily from Add/Remove.

---

### Post by castalla on 2007-10-18
errr ... didn't mention anything about automatix

I'm still struggling to get a usb stick install to work at the basic level!

---

### Post by castalla on 2007-10-19
Okay - Update Time on Broadcom ...

Following Lazyart, it worked!  I logged off, shutdown.  Restarted, and discovered exactly the same problem.  No Broadcom drivers installed.   So what can I do now?   Go back on hard-wired line, install the drivers, logoff ... repeat ad infinitum?

Any suggestions?  Should I login as root or another user.  Assume I need Admin privs to do anything?

---

### Post by scrooge_74 on 2007-10-19
> **castalla said:**
> okay guys ... I waited for the production release which I installed.

Fired it up (online via the wires) - went into the Restricted Drivers Manager, enabled the broadcom firmware, And ... got the message that the software source for bcm43xx-fwcutter  is not enabled.  That's it, no further for you, my friend!  No clues about what to do next.

So has anybody got any easy to follow instructions on what I do next?

Or does anybody know how I could get a persistent Ubuntu running in VMware Player?
That's what I'm using now (VMware Ubuntu) which gives me wifi via (oops) Vista.

A couple more ideas for you

[http://forums.debian.net/viewtopic.php?t=7949&highlight=broadcom](http://forums.debian.net/viewtopic.php?t=7949&highlight=broadcom)
[http://forums.debian.net/viewtopic.php?t=20363&highlight=broadcom](http://forums.debian.net/viewtopic.php?t=20363&highlight=broadcom)

---

### Post by anewguy on 2007-10-21
I haven't had the time to try tracing down all of your posts, but if you have been trying the firmware cutter, I would suggest instead to use ndiswrapper.  Complete instructions for doing this VERY easily can be found in the top section of this how-to:

[http://ubuntuforums.org/showthread.php?t=507505&highlight=mx3215](http://ubuntuforums.org/showthread.php?t=507505&highlight=mx3215)

If you can't find ndiswrapper and the utils on the installation CD, just go through synaptic package manager (system/administration/synaptic package manager) to find, select and apply them to your OS.

---

### Post by scrooge_74 on 2007-10-21
Las I read about Ndiswrapper the packages are not in the CD

---

### Post by anewguy on 2007-10-21
> **scrooge_74 said:**
> Las I read about Ndiswrapper the packages are not in the CD

I think that started with the 7.04 LiveCD.  With a wired connection run synaptic package manager and select both ndiswrapper and the utilities and then apply.:)

---

