---
title: "MacBook (Core Duo) power management"
date: 2007-05-07
forum: Apple Intel Users
---

### Post by thully on 2007-05-07
I just installed Ubuntu 7.04 on my MacBook (Core Duo) using Boot Camp (simple OS X+Ubuntu dual boot - no rEFIt used at all).  While most features seem to work well (I am pretty impressed that the partitioner in Feisty appears to be GPT-aware), one thing has been a big problem - power management.

There are several issues here:

1.  The system seems to be much hotter than under OSX doing equivalent tasks (i.e. browsing).

2.  After having the lid closed for a few hours, the MacBook is EXTREMELY hot and the trackpad is extremely erratic for several minutes.

3. Suspend-to-RAM is completely nonfunctional, as is suspend-to-disk. 

Any clue on resolving these issues?  This is quite annoying, and the suspend-to-RAM issue is in my opinion a showstopper - it is what drove me away from using Linux on my Thinkpad two years ago.  I saw the suggested kernel patch, but was unsuccessful in building a patched kernel using the default Ubuntu settings.  Also, I need linux-restricted-modules for wi-fi, which seems to be incredibly difficult to build.  If I can't get things working well, I may just run Ubuntu in Parallels or VMware on OS X (which would make things very easy as far as hardware support and would allow me to easily test Ubuntu's "unstable" branch without the risk of borking up anything)

---

### Post by mustang on 2007-05-07
> **thully said:**
> I just installed Ubuntu 7.04 on my MacBook (Core Duo) using Boot Camp (simple OS X+Ubuntu dual boot - no rEFIt used at all).  While most features seem to work well (I am pretty impressed that the partitioner in Feisty appears to be GPT-aware), one thing has been a big problem - power management.

There are several issues here:

1.  The system seems to be much hotter than under OSX doing equivalent tasks (i.e. browsing).


This is true. There are a couple of threads about it here but in a nutshell, mactel kernel developers are investigating those issues. Note that you will encounter heat issues in windows as well--apple has admitted that. Also, the linux kernel developers are attacking general power management problems that plague all notebooks. So I would just wait it out or if absolutely necessary, buy a system76 laptop. 

> 
2.  After having the lid closed for a few hours, the MacBook is EXTREMELY hot and the trackpad is extremely erratic for several minutes.


To mitigate the heat issues, I keep my fan's minimum speed at 3000 rpm. See this thread: [http://ubuntuforums.org/showthread.php?t=434639](http://ubuntuforums.org/showthread.php?t=434639)

I get the trackpad behavior every now and then too. Someone probably has a better solution but I solved it by going into gsynaptics, disabling the trackpad, and then reenabling it.

> 

3. Suspend-to-RAM is completely nonfunctional, as is suspend-to-disk. 

Any clue on resolving these issues?  This is quite annoying, and the suspend-to-RAM issue is in my opinion a showstopper - it is what drove me away from using Linux on my Thinkpad two years ago.  I saw the suggested kernel patch, but was unsuccessful in building a patched kernel using the default Ubuntu settings.  Also, I need linux-restricted-modules for wi-fi, which seems to be incredibly difficult to build.  If I can't get things working well, I may just run Ubuntu in Parallels or VMware on OS X (which would make things very easy as far as hardware support and would allow me to easily test Ubuntu's "unstable" branch without the risk of borking up anything)

I responded to your post in my suspend thread. Like I said, I didn't need to mess around with linux-restricted-modules or anything like that. 

I would agree s2ram is a showstopper---I spent days trying to solve it and I'm happy to say that agony is finally over. :) BTW--what do you mean by Ubuntu's "unstable" branch? Feisty is rock solid.

---

### Post by thully on 2007-05-07
By Ubuntu's unstable branch I meant testing Gutsy (7.10) - which is basically Ubuntu's version of Debian sid right now - not using Feisty.  When I had the Thinkpad I actively worked on testing all the development snapshots of Ubuntu - starting with Ubuntu's first public beta version.  I wouldn't want to do this on a separate partition given the fact that I only have a 60GB drive as-is (which is only realistically enough for OSX and one other OS).  

My comment was merely that Parallels/VMware would make this easier (though this would apply on Feisty as well as OS X).  Of course, it would also eliminate all the power management/mouse issues, as OS X would be behind the scenes running the show.  That's why I was saying I may do this until the power management is better (at least until I get s2ram going reliably)...

---

