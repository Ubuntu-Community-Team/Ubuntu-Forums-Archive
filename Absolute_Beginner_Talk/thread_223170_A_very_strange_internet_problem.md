---
title: "A very strange internet problem"
date: 2006-07-26
forum: Absolute Beginner Talk
---

### Post by limberlegs on 2006-07-26
Hello,

I've been using Dapper Drake 6.06 for about three weeks now, and for the most part, the transition from Windows has been relatively smooth.  

Since the first install, my LAN connection has been fine.  I'm connecting via ethernet to my Linksys Wireless-B router, which has worked flawlessly under Windows for over two years.  My internet is provided through a residence hall connection at my university.

Lately, I've encountered a rather strange problem.  I log on to Ubuntu,  start Firefox, and everything will be just fine for about 5 minutes.  Suddenly, my internet connection is lost.  Firefox gets stuck "looking for www.google.com" or whatever.  Even more strange is the instance of this that happened earlier today when it appeared that my IM client was still online while the browser wasn't able to connect to anything.  

Usually, I can restart my computer and this will fix things.  Sometimes, I will restart and I'll have the same problem (online for 5 minutes, then nothing).  I encountered the same problem with a 3Com router about a week ago, and so I switched to my Linksys router.  It was fine for a few days, but recently the problems have started again.  

Has anyone else encountered such a problem?  Are there any documented solutions?

Thanks for your help!

---

### Post by Sef on 2006-07-26
1) Have you had the same problem if you used Windows?

2) Was any software installed or settings changed just before this problem occurred?

---

### Post by limberlegs on 2006-07-26
Hey, thanks for your reply.

1) I've never encountered such a problem in Windows with the same frequency.  I've certainly had internet interruptions, and usually a quick reset of the router fixes it.  This problem seems to occur more consistently.  It was so consistent that I switched routers, and that seems to provide a temporary solution, however the same problem began occurring today.  

2) I have been messing around with codecs trying to get flash to work with sound in Firefox.  The last thing I did was this add this to my startup:

ln -s /tmp/.esd-bryn/tmp/.esd 

I have installed all of the codecs I can think of (via Automatix, and manually) to get all of my multimedia working, but I can't imagine this would have affected my internet connection (right?).

The problem seems to be hard to diagnose, because it isn't consistent ENOUGH to isolate the cause.  Perhaps Ubuntu only weakly supports my Linksys router? I'm curious to know if there is any information out there dealing with these problems.  Right now, I'm able to connect to the internet without any difficulty, but I'm not sure how long that will last.

Thanks again for your response.

---

### Post by professor_chaos on 2006-07-26
You can try searching the forum for the term "chattr". Many of the hits you get will involve people with intermittent network problems like yours. Basically you set /etc/resolv.conf with fixed DNS addresses and then you prevent the config file from being changed by the OS, by using the command "chattr". Note: chattr "locks" the file, so if you ever need to edit the file you need to manually unlock it. Hope it helps.

---

### Post by limberlegs on 2006-07-26
Hey, thanks for your reply!

I have perused the links that resulted from the search, and it seems that this is indeed my problem.  I will check it out and post my results.

---

