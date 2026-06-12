---
title: "[SOLVED] No s2ram in uswsusp??"
date: 2007-11-18
forum: Absolute Beginner Talk
---

### Post by ResumeMan on 2007-11-18
I was using uswsusp in my Feisty install per this thread. It worked better than the native install but somewhat imperfectly.

I recently did a Gutsy install to replace Feisty. The Gutsy suspend wasn't working so hot, so I installed uswsusp. But the command s2ram returns "command not found." Looking in my /sbin folder I see that the files s2disk and s2both are there, but there's no s2ram.

Has something changed with the uswsusp program? I tried installing it again but it just said already installed.

What am I missing???

Thanks!

---

### Post by ddrichardson on 2007-11-18
You're quite right, it's not [there]("http://packages.ubuntu.com/cgi-bin/search_contents.pl?searchmode=filelist&word=uswsusp&version=gutsy&arch=i386"), but it was in [Fiesty]("http://packages.ubuntu.com/cgi-bin/search_contents.pl?searchmode=filelist&word=uswsusp&version=feisty&arch=i386"). All I could find in the changelog was this:> 
uswsusp (0.6~cvs20070618-1ubuntu2) gutsy; urgency=low

  * Don't build s2ram. It's not sensible on Ubuntu.
-- Matthew Garrett <mjg59@srcf.ucam.org>  Mon, 20 Aug 2007 15:47:18 +0100

---

### Post by ResumeMan on 2007-11-18
Well. THAT isn't very helpful! Do you know if there's any way to go back to the Feisty package?

Thanks for your research!

---

### Post by ResumeMan on 2007-11-22
So this [bug report]("https://bugs.launchpad.net/ubuntu/+source/uswsusp/+bug/134238")  has some more information on this.

I went to the debian page linked near the bottom of the thread, activated one of the Debian repos, and installed uswsusp v.7.1(I think that's the one?). Note that I followed the advice at the bottom and upgrated my existing v6.

As far as I can tell, s2ram is working just fine. I've only run thru the cycle a handful of times, and I haven't integrated it into HAL yet, so I'm not sure if it's a permanent fix. But so far I'm happy.

Note that [this page]("http://en.opensuse.org/S2ram") has lots more info on s2ram, including some work-arounds.  So far it doesn't seem that I need them, but it's good to know that there's a resource if I get into trouble.

---

