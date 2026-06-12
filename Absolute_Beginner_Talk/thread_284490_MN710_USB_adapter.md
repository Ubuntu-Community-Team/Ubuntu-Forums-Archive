---
title: "MN710 USB adapter"
date: 2006-10-25
forum: Absolute Beginner Talk
---

### Post by IsaacJ on 2006-10-25
Hello everyone.  I just started Ubuntu Dapper about 3 days ago and have been trying to get wireless going.  I am a Linux newb, but I have been checking on quite a few tutorials regarding this and other things.  Maybe someone who has the adapter can tell me if they did something different from myself?

The short version is that I have found a few other references (some in here, I think) to people who have found a way to get the adapter to work via ndiswrapper.  Yet when I try, using both the drivers on the CD and the latest updates, I get an error.  Then I tried updating ndiswrapper (downloaded the deb file in WinXP) and get:

==================
couldn't copy /home/isaacj/isaacj/Desktop/mn710.inf at /usr/sbin/ndiswrapper line 135.
==================

But as I said, a few others have pulled it off online.  Some seem to have problems getting it to stay active, but I haven't even got that far yet.  :-)  Note that before I updated ndiswrapper it did not give an error message, but when I checked via "ndiswrapper ~l" it would then say the driver is invalid.  So it still didn't work regardless of ndiswrapper version.  I doubt it matters, but it was only after the update that it gave me anything specific.  There was nothing but an empty folder where the driver should have been copied, so I have deleted it for now.

BTW, I see plenty of people have tried the Linksys WUSB54G adapter and got it to work.  Has anyone tried this that might share some experiences?  Just wondering in case this is a no go.  Thanks a lot for your time.

IsaacJ

---

### Post by IsaacJ on 2006-10-26
The version of ndiswrapper I'm currently using is 1.8 (ndiswrapper-utils_1.8-0ubuntu2_i386.deb).  I see there is another version marked 1.27, dated just a few days ago despite being a lower version number.  I'm wondering if I should be using it instead?  Maybe that's my problem.  The only person I have been able to contact directly who has the adapter working uses Suse Linux, and that's what he is using.

I understand that there are differences between Ubuntu and other Debian builds.  I don't much about Suse or if this other package is acceptable? 

If anyone is curious about what I mean, it's here at [http://sourceforge.net/project/showfiles.php?group_id=93482](http://sourceforge.net/project/showfiles.php?group_id=93482)

Thanks for any help.


IsaacJ

---

### Post by wrongopinions on 2007-05-29
I got my driver to recognize mine....
I installed ndiswrapper from the live cd and then installed the driver.

My issue is, I can see other wireless networks and I entered all my information for WEP and ID... but still it isnt connected....

help?

---

