---
title: "[SOLVED] &amp;quot;trackerd&amp;quot; wont go away."
date: 2007-10-26
forum: Absolute Beginner Talk
---

### Post by linuxgator on 2007-10-26
I successfully installed Ubuntu 7.10 on an IBM t21 thinkpad.  The installation went smooth except for one problem with X getting the display to work after 1st boot  (FYI - the solution can be found here... [http://www.thinkwiki.org/wiki/Installing_Ubuntu_on_a_ThinkPad_T21](http://www.thinkwiki.org/wiki/Installing_Ubuntu_on_a_ThinkPad_T21) ).  Anyway, i noticed after the install, that the hard disk was being accessed non-stop.  Using "top" i determined that "trackerd" was using a large amount of cpu.  I looked "trackerd" up on the internet and found that it is the daemon used by "tracker" to index the hard disk for desktop searches (this is a new package with 7.10).  I allowed it to run for a couple of days.    The hard disk ran nonstop.  I do not plan to use the desktop search feature so i killed the trackerd task and the hard disk access returned to normal.  I used add/remove to remove the tracker package.  But after rebooting, trackerd still auto starts.  Excessive hard disk access starts a few mins after bootup and top reports that trackerd is running.  Why?  And how do i stop it from auto starting?

---

### Post by n3tfury on 2007-10-26
have you checked System -> Preferences -> Sessions>Startup tab?  not sure why it didn't totally remove itself, but you can see if it's still auto-starting here.

---

### Post by linuxgator on 2007-10-27
That was it.  Thanks for the help :-)

I removed it from the startup list and rebooted... no more trackered!

---

### Post by n3tfury on 2007-10-27
no problem.  can you mark you thread as solved?

---

