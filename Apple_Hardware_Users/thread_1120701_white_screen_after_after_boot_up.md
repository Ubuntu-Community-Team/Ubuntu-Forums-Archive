---
title: "white screen after after boot up"
date: 2009-04-09
forum: Apple Hardware Users
---

### Post by TrevM on 2009-04-09
I am trying to install Ubuntu 8.10 on my 2003 Mac Ti powerbook.  However once installation is complete and the machine reboots the screen slowly turns white.  Please, will someone explain:
1. how i can access (and see) the command line so i can make a fix

2. what fix do i have make?

please give instruction as if you are talking to a complete beginner, beacuase win it come to Linux and Ubuntu i am.  So please walk me through it.

I am disparte to give Linux a fair crack, i just can not get to the start line and i do not want to use Fedora (can't get my airport to work in fedora and i have tried everything)

thanks for your help

---

### Post by cyberdork33 on 2009-04-09
This is a PowerPC machine, right?

---

### Post by stream303 on 2009-04-12
When the second-stage yaboot boot: prompt comes up, hit TAB to stop the countdown.  Then enter

```
Linux video=ofonly
```

after this you may have to custom-modify your /etc/X11/xorg.conf to get X working properly.  See the threads and wikis for more details specific to your machine.

I also suggest using the "alternate" release since being text-based for installation, it helps to bypass some of these issues early on - at least enough to get the system written to disk properly - you'll sometimes still have ppc quirks to deal with manually.

And, I'd avoid 8.10 with it's known cdrom detection and application issues.  Stick to 8.04.1 or perhaps try Jaunty 9.04 beta or release..

---

