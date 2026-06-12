---
title: "Install problems on Rev 1 B+W G3"
date: 2004-12-07
forum: Apple PPC Users
---

### Post by features on 2004-12-07
Hi All,

I'm having some problems installing Ubuntu onto my B+W G3.  The CD I am using is the Warty CD release from Shipit.

THe first section of the install works fine: all data is copied across to my HD (the stock 6GB B+W HD), but when I reboot to go on to the second stage of the install I get the following message:

[TUX LOGO]
pivot_root no such file or directory
/sbin/init/: 429: cannot open dev/console: no such file
Kernel Panic: Attempted to kill init!

I have attempted the install several times, even on a freshly initialised HD with new (Apple) drivers, still no joy.  

It is a Revision 1 B+W G3 which has some known issues with the IDE controller, so this may be the culprit, though the controller works fine with the stock HD with no issues.

I did notice, however, that the message says "dev/console",  not => "/dev/console".  Could this be the source of the problem? Or is the CWD already "/" at this point?

I have seen the other posts in these forums about this error message, but they don't seem to have an answer.  Most answers immediately suspected the media, since they were downloaded ISO's.  This is not the downloaded version, however, it is the FreeCD version.

Any thoughts?

---

### Post by Ptero-4 on 2004-12-07
[QUOTE=features]Hi All,

I'm having some problems installing Ubuntu onto my B+W G3.  The CD I am using is the Warty CD release from Shipit.

THe first section of the install works fine: all data is copied across to my HD (the stock 6GB B+W HD), but when I reboot to go on to the second stage of the install I get the following message:

[TUX LOGO]
pivot_root no such file or directory
/sbin/init/: 429: cannot open dev/console: no such file
Kernel Panic: Attempted to kill init!

I have attempted the install several times, even on a freshly initialised HD with new (Apple) drivers, still no joy.  

It is a Revision 1 B+W G3 which has some known issues with the IDE controller, so this may be the culprit, though the controller works fine with the stock HD with no issues.

I did notice, however, that the message says "dev/console",  not => "/dev/console".  Could this be the source of the problem? Or is the CWD already "/" at this point?

I have seen the other posts in these forums about this error message, but they don't seem to have an answer.  Most answers immediately suspected the media, since they were downloaded ISO's.  This is not the downloaded version, however, it is the FreeCD version.

Any thoughts?[/QUOTE]
 The problem seems to be a misconfiguration in the line 429 of your /sbin/init file, which as you noticed points to dev/console from /sbin instead of /dev/console. To fix it you need a way to access your B+W HD and edit the /sbin/init file (the gentoo live cd is a good way of doing that)

---

### Post by features on 2004-12-08
Good idea!  And that's what my next step would be, except my employer just furnished me with a "pre-loved" laptop to play with, so I think I'll take out my Ubuntu / general Linux fiddling obsession out on that, and leave the G3 as a MacOS machine, for now.  The gentoo CD would'vew taken an age at 56k too  :mrgreen: 

So, is this a PPC installer misconfig, or something specific to the G3?  Should I put a bugnote or something in?

Thanks heaps for the prompt and practical help.

Mark

---

### Post by ethn on 2004-12-09
hello!

i have a group of B & W G3s (rev 1 and rev 2) and haven't been able to get past this error on a single machine.  i am very new to linux.  i had originally heard it was a problem with the ide controller detecting the drives in a different order than the installer did.  one person suggested compiling CMD64 support into the kernel to fix it.  for a while i thought it was just a rev 2 problem, but now the rev 1s are producing the same results.  i like the simplicity of your solution, but would love a list of commands to fix this problem.  i haven't seen a working resolve explained step by step yet.  the person who took the time to do it would help a few people it appears.  (this problem is posted again and again in this and other forums.)  i have the gentoo live cd and i am not afraid to use it!  =)  i know this is a breeze for somebody out there.  help me get unstuck.  i just want to stop drooling over screenshots and actually run the thing.

Thank you for your time sirs.

---

### Post by features on 2004-12-09
[QUOTE=ethn]

 i am very new to linux.... i like the simplicity of your solution, but would love a list of commands to fix this problem. 

[/QUOTE]

I am only slightly less new to linux, but I think the basic idea is this:

Fire up Gentoo Live CD
Open up a terminal
mount the HD of the B+W (unless Gentoo automounts it already)
cd into that
edit line 429 of /sbin/init in your favourite editor to read "/dev/console" instead of "dev/console"
save changes
unmount HD
reboot machine (take out the Gentoo CD)

The hairy bit is the "mount the HD" bit, you have to get the right device number.  I 
*think* it's hdc.  Check out "man mount" from the terminal for some help.  There's quite a bit of info there,and it's a bit scary but if you take it slow, you can sort it out.  Perhaps one of the Linux deities lurking around here may be able to provide a command for us mere mortals to use? :mrgreen: 

At least at this point in the procedure it's easy enough to go through the install process again, and get back to the state you were in before.

Let us know how it goes!


Mark

---

### Post by ethn on 2004-12-10
Hello Mark!

Thank you very much for your help sir!  I am able to boot the gentoo live cd, mount the hardrive, locate the file.... and here, I fear, is where the newbie is glaring off my forehead.

I thought I would be able to throw a "nano /sbin/init" from the mount point?  I get a very garbled looking file in all of the "editors" I have tried.  I suspect I am confused about the type of file I am editing and the tools to do it.  When I "less /sbin/init", it spits out a better looking list.  I would go on with my sob story but something tells me what I just described might be just plain silly.  =)

Thank you again for your help.  I appreciate it very much.

ethn.

---

### Post by features on 2004-12-14
Righto,

Apologies for taking an eternity to reply :D ....I think you may have to "sudo" to edit that file.  I'm working from a windows box at the mo, so can't verify.  But try that.

HTH

Mark

---

