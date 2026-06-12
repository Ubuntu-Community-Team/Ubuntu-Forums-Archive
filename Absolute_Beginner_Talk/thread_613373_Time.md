---
title: "Time?"
date: 2007-11-14
forum: Absolute Beginner Talk
---

### Post by GeorgiaBoot on 2007-11-14
Okay so I made the decision Sunday to switch half way to Ubuntu Since I work on Windows allot for graphics.  I installed it on my external Hard Drive and so far everything has gone somewhat smooth. 

So now to the question, when I am done with Ubuntu I shut down and then restart and load windows, everything goes fine its just every time I log into Windows the time is incorrect. Ubuntu always has the correct time. Anyone know the problem? I know it has something to do with my booting. 

Thanks

---

### Post by jflaker on 2007-11-14
are you set to UTC or to your own time zone?

If you are set to UTC time in LInux then Windows will be wrong because windows uses UTC Offsets to show the time.

Check your settings on Ubuntu.

---

### Post by GeorgiaBoot on 2007-11-14
When I looked at it the only thing clicked was show date. The "Use UTC" Was not checked. Under clock type it says 12hour. Should I maybe check UTC? I mean changing my clock every time I log into windows is not a huge problem but I guess after a while I will get irritated by it.

Thanks for the help.

---

### Post by arashiko28 on 2007-11-14
It happened to me, it self corrected after a couple of updates. So really don't know, I did nothing.

---

### Post by GeorgiaBoot on 2007-11-14
Okay well I guess I will leave it and see if windows is smart enough to fix it!

Another quick question, Ubuntu has just released 7.1 and I have 7.04, if I upgrade will that change any of my display stuff such as themes? As I have decked out the whole desktop to look a certain way and I would not want to have to re-do anything. It might be a really dumb question but I have not worked with Ubuntu enough yet to know how it works.

Thanks

---

### Post by Tyke91 on 2007-11-14
you *can* do an upgrade, but it will most likely be incompatible with any custom changes you have made. 

It's a lot better just to save your personal data and re install the entire thing. If you feel up to it, go ahead and try. You may be surprised with 7.10, it comes with Compiz-Fusion pre installed, which looks superb when customized.


also, I don't want to be nitpicky, but it is 7.10 , not 7.1.    Ubuntu names its versions after the Year and the Month, so 7.10 is October 2007, 7.04 is April 2007 and so on. :)

---

### Post by bollix47 on 2007-11-14
Open a terminal (Applications > Accessories > Terminal)

Type:

```
gksudo gedit /etc/default/rcS
```

Find:

```
UTC=yes
```

Change it to:

```
UTC=no
```

---

### Post by Hospadar on 2007-11-14
A note on upgrading:
I think that it would be a good idea to go with 7.10, it has some good new features and the compiz integration is really nice.  That said, the upgrade feature is relatively unreliable.  It's just a very difficult task to change that much stuff and still have everything work right.  So as the previous user suggested, if you do try an upgrade from the internet, be sure to back up all your important data first, and be prepared to do a complete install of 7.10 after in case the upgrade doesn't work.

For some people the upgrade will go swimmingly with almost no problems, other people will have serious problems up to an including a totally non-functional installation.

---

### Post by GeorgiaBoot on 2007-11-15
Okay so if I do upgrade via the internet I have probably 50/50 chance on it working? Lets say it works fine does that still mean I lose my custom theme? As I have downloaded some stuff to make it look different, so I would have to go re-download and find the stuff. 

If it did go wrong what do I do? Would I need to re-install the whole system? I don't have to much data on it as I just put Ubuntu on it Sunday but I put it on my external Hard Drive so it was a little more work. Just Let me know the best way to upgrade if you guys think I should.

Also since my desktop effects keep freezing if I upgraded would the compiz effect freeze as well?

Sorry for not putting 7.10 I was just trying to type fast, but I did not know that about the date thing.

Thanks everybody.

---

### Post by derred on 2007-11-15
I upgraded 3 of my 4 Ubuntu machines and everything worked great. (The 4th machine now runs HackOS X86 :)). I didn't have beryl installed on any of them so I don't know if that would affect the upgrade process. I'd say go for it but back up first.

---

