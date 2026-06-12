---
title: "Live CD Shutdown"
date: 2005-10-18
forum: Absolute Beginner Talk
---

### Post by Honayo on 2005-10-18
I just downloaded and burned a live CD of the lastest version of Ubuntu. Loved what I experienced and want to take this further with Ubuntu.
Everything went smoothly and all applications seemed to work properly when I booted from the cd.
The problem I had is that I was unable to shut down the machine to re boot.
The cd would not eject, ctrl/alt/delete didn't work and I was unable to power down by turning off the machine. Had to unplug it from the power source in order to shut down. Any tips on shutting down from the live cd?

---

### Post by jasmuz on 2005-10-19
Open a terminal, type sudo halt

---

### Post by Honayo on 2005-10-19
Thanks for the tip.
As you can probably gather, I'm completely new to Ubuntu and linux. Is there a link you could recommend that would help me learn some of the intricacies of them?

---

### Post by ChrisTheGeek on 2005-10-19
The correct way to shut-down is to choose "Log Off" from the System menu at the very top of your screen.  A little box will appear with some options including "Shut down".  Just choose that and click ok.

You cannot eject the CD since, when running the LiveCD, everything is being read from that CD (remember, the liveCD doesn't touch your hardrive at all).  In general, you can right click on the CD icon on the desktop and choose "Eject" to eject CDs.

Ubuntu specific help can be found:

- by clicking the help icon at the top of the screen (looks like a red life preserver)
- at [www.ubuntuguide.org](www.ubuntuguide.org)
- at [www.ubuntu.com](www.ubuntu.com)

There are loads of beginners guide to Linux available online.  Lots of information can be found here: [www.tldp.org](www.tldp.org)

Good luck

---

### Post by Honayo on 2005-10-19
[QUOTE=ChrisTheGeek]The correct way to shut-down is to choose "Log Off" from the System menu at the very top of your screen.  A little box will appear with some options including "Shut down".  Just choose that and click ok.

You cannot eject the CD since, when running the LiveCD, everything is being read from that CD (remember, the liveCD doesn't touch your hardrive at all).  In general, you can right click on the CD icon on the desktop and choose "Eject" to eject CDs.

Ubuntu specific help can be found:

- by clicking the help icon at the top of the screen (looks like a red life preserver)
- at [www.ubuntuguide.org](www.ubuntuguide.org)
- at [www.ubuntu.com](www.ubuntu.com)

There are loads of beginners guide to Linux available online.  Lots of information can be found here: [www.tldp.org](www.tldp.org)

Good luck[/QUOTE]

Good advice as well as links for learning more about Ubuntu.

I have an extra machine that I am going to do a full install on in order to learn more about this. So far, I like what I see. I'm ready for windows to take a dive.

---

### Post by ChrisTheGeek on 2005-10-20
Glad to hear you're ready to try the full thing.  Remember that Linux behaves differently to windows in a number of ways.  There is usually a good reason for this but it can be frustrating for linux newbies since the reasons may not always be immediately obvious.

A couple of hints:

- files in linux are case sensitive - "hello.txt" is a different file to "Hello.txt" and they can both be in the same directory.
- files or directories beginning with a '.' are hidden
- all of your personal files and settings should be stored in your home directory

Good luck with it

---

