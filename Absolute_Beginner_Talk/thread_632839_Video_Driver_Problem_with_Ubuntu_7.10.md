---
title: "Video Driver Problem with Ubuntu 7.10"
date: 2007-12-05
forum: Absolute Beginner Talk
---

### Post by Curbuntu on 2007-12-05
I have a three-year-old Compaq laptop with an nVidia GeForce4 440 64M graphics chip.  The Ubuntu 7.04 Live CD was able to load just fine on this machine, an install of 7.04 was a success (except for the built-in wireless network adapater).

But, having removed 7.04, I can't get the 7.10 Live CD to run.  The MD5 hash of the desktop-i386.ISO file checked out fine.  The CD's self-check was positive as well.  Everything seems to load fine -- even the Ubuntu theme music.  But after what appears to be normal screen output right up to almost the very end of the boot process, what I finally get is a horizontal band (with a sort of "houndstooth" pattern) through the center third of the screen.  It's completely unreadable.

Any thoughts about how to proceed?  Do I have to use the "alternate" CD?  If so, why would the 7.04 Live CD work and not 7.10?

Thanks in advance.

---

### Post by Hospadar on 2007-12-05
The reason it might not be working is the livecd might be trying to enable some extra effects not present in 7.4 that could be causing problems.  I believe in the initial ubuntu boot screen from the livecd (where you select "Start and install... blah, blah, etc) you can get at some different options for video, you might take a look there, see if there are some settings that can be turned down.  also it's a while since I've gotten cookin with a livecd, but is there a "safe graphics" option? if so, try that.

Worst case scenario, just use the alternate cd, it's not particularly difficult to use, it's just uglier.

---

### Post by Curbuntu on 2007-12-06
I tried your suggestion.  The LiveCD boot screen gives a video option (F4 as I recall).  I chose to boot in 1024x768x16M colors and all went well (although the optimum resolution -- 1280x800 -- wasn't available from that screen).  Thanks for the suggestion.

Now the question is, when I decide to load 7.10 (from within the LiveCD session), will there be options available to choose the graphics adapter or resolution, etc.  I know you said that it's been a while since you used a LiveCD, but perhaps someone else is reading and can answer.

Once again, thanks for your solution.

---

