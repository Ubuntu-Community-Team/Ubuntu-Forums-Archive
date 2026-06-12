---
title: "iMac Blueberry: Ubuntu/Xubuntu turns off the CRT power supply at wrong time"
date: 2007-05-06
forum: Apple PPC Users
---

### Post by rondackcpu on 2007-05-06
I have an old iMac Blueberry which I have tried to rehab with Ubuntu or Xubuntu.  I have the 3 legitimate Apple CD's which will install Apple OS 8.5, or OS 9.1, or OS 10.0 on the machine.  None of these operating systems are acceptable to me because of the one button hockey puck mouse.

So I tried to rehab the machine by installing 512 MB memory (which works correctly, and the Apple OS's love) and some other operating system such as Ubuntu or Xubuntu.  One of the annoyances I have had is that the Ubuntu or Xubuntu Live CD's and the Ubuntu or Xubuntu startup routines turn off the iMac's CRT power supply (that is, put the machine into the Apple's equivalent of "sleep") at inappropriate times.  The Live CD's boot OK, but they turn off the CRT power supply at the critical time that "X" is about to display a window, making the install from the Live CD impossible.  The Alternate CD's install an annoying system which turns off the CRT's power supply during part of the boot sequence.

Both do a disservice to the potential Ubuntu/Xubuntu user.  Is there any solution to this annoyance?

---

### Post by 3rdalbum on 2007-05-07
There are two solutions:

1. Pay me $300 and I'll find the time on Wednesday to finish and release Copland PPC; a distribution which has fixed this problem. :-)

2. Cheaper solution: [https://wiki.ubuntu.com/PowerPCFAQ](https://wiki.ubuntu.com/PowerPCFAQ)

Under the heading "How do I get Ubuntu working on an iMac G3"

---

### Post by rondackcpu on 2007-05-09
Thanks, 3rdalbum, for your response.  All I found there was an edit to the xorg.conf file.  I made the changes (# load DRI, and change horizontal range, vertical range agreed with the suggestion).  On reboot, those changes made no difference at all.  "Your $300 check is in the mail."

CRS

---

### Post by rondackcpu on 2007-05-09
If anybody is still watching:  There may be a bigger clue in 3rdalbum's post than I caught on the first try.  In the "xorg.conf" file, the screen resolutions given for all  the depths are "800x600" and "640x480".  In the Ubuntu preferences screen resolution panel, only "1024x768"is offered as a screen setting.  Where is that coming from?  Why is it not offering the "800x600" and "640x480" instead?  Is some other configuration file taking control instead of xorg.conf?  What, where?  I have no idea how to measure what resolution is actually being displayed.  What screen resolution are other iMac users seeing?

During the Yaboot startup, the lettering on the screen is very, very tiny.  Is that display adapter (ATI) capable of higher resolution than what seems to be offered?  Apple does not offer any advice on higher resolution, but Apple did not offer much advice on a whole bunch of other issues about the iMac Blueberry.  For example, upgrading memory.

One last point, when I first installed OS 9.1 and/or OS 10.0 on this machine many years ago, there was a required change to the iMac equivalent of BIOS.  I had to hold the "programmers paper clip switch" while the computer booted;  then a change was written to the BIOS, but I have no idea what was changed.

Thanks for reading through this.

CRS

---

### Post by 3rdalbum on 2007-05-10
The Yaboot text is indeed tiny.

I think the PowerPCFAQ I linked to has incorrect information; give these settings a whirl (they definately work on my iMac Grape):

	HorizSync	60-60
	VertRefresh	75-117

---

