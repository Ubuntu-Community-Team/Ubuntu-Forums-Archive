---
title: "Foldng w/ Ubuntu Server 7.10"
date: 2008-03-01
forum: Absolute Beginner Talk
---

### Post by dustin_wielenga32 on 2008-03-01
I'm trying to setup Folding@Home on my Ubuntu Server at home.  I'm using FAH504-Linux.exe from Stanford, and Ubuntu 7.10 Server.

What I am trying to do is to get Folding run silently in the background.  If I run "./FAH504-Linux.exe" folding works fine, but I can't use the console for anything else.  If I run "./FAH504-Linux.exe &" then I can Ctrl-C out of FAH, and FAH keeps calculating.  However, whenever FAH posts something to the log, that goes on my screen.

I've come across a couple of commands which are supposed to direct the output to /dev/null, but neither have worked, the Folding process doesn't run using them (if I check "ps aux", FAH is not listed).  The commands I tried are: >  ./FAH504-Linux.exe -forceasm -advmethods -verbosity 9 >/dev/null 2>&1 & and >  exec FAH504-Linux.exe >& /dev/null &.

After running the second of those commands, and immediatly going "ps aux" at the bottom it says: > [1]+ Exit 127 exec FAH504-Linux.exe >&/dev/null.  And next time I run "ps aux" no folding process at all.

So, to simply and restate my question, is there a way to run Folding silently in the background, and also, what's the best way to set it up to run on startup.  Cron?  Or messing w/ rc3.d?

Thanks in advance.

---

### Post by dustin_wielenga32 on 2008-03-01
Ok, found a working command: "./FAH504-Linux.exe > /dev/null 2>&1 &"

It's all working now.

---

