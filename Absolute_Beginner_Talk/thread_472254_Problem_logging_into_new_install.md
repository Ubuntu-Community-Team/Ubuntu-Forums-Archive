---
title: "Problem logging into new install"
date: 2007-06-12
forum: Absolute Beginner Talk
---

### Post by MacDuff on 2007-06-12
Just installed Ubuntu on a Windows XP machine and did not receive any errors but when trying to log into Ubuntu I get a message "GDM could not write to your authorization file.  This could mean that you are out of disk space or that your home directory could not be opened for writing.  In any case it is not possible to log in.  Please contact your system administrator."

Does anyone have any idea what I can do to address this problem?

Thanks

---

### Post by abn91c on 2007-06-12
try defragging windows

---

### Post by MacDuff on 2007-06-12
Thank you.  When I started windows it asked me to to do run scandisk.  After completion I tried again to start ubuntu but same problem appeared. I did not think to try defrag, so you may be on to something here.  
I will give it a try.

---

### Post by Hendrixski on 2007-06-12
hey I just saw that you're new here and I thought I'd just welcome you.
so here it goes

WELCOME TO THE COMMUNITY!
You can come to the UbuntuForums to ask questions or just chat.  We're all here because we love ubuntu, and we want to share our joy with others. Soon you will be too.

If you would prefer to ask questions via a chatroom full of community members who can help you then you can check out the channel #ubuntu on IRC.  Installing IRC is easy and fun.  Just go to applications-->Add/Remove and pick XChat from the list, click OK and it installs.

If you'd like to meet other Ubuntu users in your area check out the Ubuntu LoCo teams for your city or state. 

There is plenty of GREAT documentation written about Ubuntu, just ask google and you'll find it.  A lot of it is written by the same people who answer questions on the forums so you'll get the information faster.  if dry manuals aren't your thing then relax and watch some videos.  [http://screencasts.ubuntu.com/](http://screencasts.ubuntu.com/) is a great website to get started, how to install, how to customize, how to set up your mail. etc.  Also check out [www.ubuntuvideo.com](www.ubuntuvideo.com) and [www.ubuntuclips.org](www.ubuntuclips.org).

I hope I'll see you around some more.  :-)

---

### Post by MacDuff on 2007-06-12
Thanks for the welcome Hendrixski.  I am not crazy about chat rooms because of all the security problems reported but I may be force to do that.

I tried running defrag as suggested by abn91 but it did not fix my problem.  I have been reading documentation about Linux in general and ubuntu in particular for about 5 days now and have struggled to get ubuntu installed on the box I on which I wanted to try it.  (The install disk was a DVD and the box I was using only had a CD reader.)  Now I run into this problem.  It is getting frustrating.

As much as I would like to abandon MS, it seems that I have had less problem with umpteen Windows installations of various flavours than I have had with this install of Ubuntu.
Oh well, I guess DOS and Windows and Cobol were all frustrating at first.  I will soldier on.

---

### Post by H.E. Pennypacker on 2007-06-18
MacDuff, please see this thread:

[http://ubuntuforums.org/showthread.php?p=2862368#post2862368](http://ubuntuforums.org/showthread.php?p=2862368#post2862368)

---

### Post by MacDuff on 2007-06-18
That particular problem is solved.  It turns out that I was attempting to install Ubuntu into a partition that, indeed, probably did not contain enough space but why did the installer not check for available space instead of doing the install and then not let me log in?

I have since installed Ubuntu on a test system with its own drive and I was quite impressed with the install until I add VMWare Server then installed Virtual Windows XP and found a couple of problems:
1. When switching back and forth from Win XP to Ubuntu the screen resolution changes and the Ubuntu display screen is too large to fit on the monitor. 

OK so maybe that is caused by an old ATI driver and may not appear on a newer system so I could live with having to re-start Ubuntu ever time I leave Windows XP on the test system BUT

2. The sound card also quit working and I could not find a fix for that. After testing the hardware on another system,  I tried a disk re-format and clean re-install of Ubuntu and still no joy.  I have just reformatted the test drive and will try a clean install of Win XP to see if Windows can find and install the audio drivers again.  If it does, I will have to consider the experiment with Ubuntu a failure.

I was hoping that Ubuntu would be the solution to some of my client needs.  I still hope that it may be (If I live long enough to learn enough about it to be able to support it);)

Can anyone recommend a good book or books that will show me the administrative tricks to trouble-shoot Ubuntu?

Thanks

---

