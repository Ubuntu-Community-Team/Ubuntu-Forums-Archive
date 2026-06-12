---
title: "Can't Boot!!"
date: 2007-10-20
forum: Absolute Beginner Talk
---

### Post by froggger on 2007-10-20
I can't boot into gutsy.
i was fiddling with ndiswrapper(more deatils in this thread=http://ubuntuforums.org/showthread.php?t=581753)
and now i can't boot.
i can't get into recovery menu either.
the boot hangs at something to do with ndiswrapper.
i can get into windows if that helps.
more info in that thread i linked to.

if you guys want the numbers and letters of the error, i can post them up.

Please help me!

---

### Post by catfacts on 2007-10-21
If you have just installed and can afford to do this reinstalling can save you a lot of troubble.

---

### Post by froggger on 2007-10-21
i dunno, i had to manually switch dvrives becasue one of mine had errors and i can do it, but its not that easy.
are you sure there are no alteranatives?

---

### Post by froggger on 2007-10-21
bump?

---

### Post by shad0w_walker on 2007-10-21
If you could post the details of any messages/errors you see that would probably help alot. The odds are good that whatever has been done you can fix by booting off a Live cd and editing a file or two but first we need to figure out what the problem actually is.

---

### Post by froggger on 2007-10-21
thank you so much, i was just about to give up on it too.
i'll edit this post in a min with the errors, one of them changes every time, but i'll post it anyway.

UPDATE:
heres the error code the first set of numbers in brackets changes though.
"[71.187829] ndiswrapper (ZwQueryValueKey:2376) not fully implemented (yet)"
thats the last thing it says before it freezes.


Thank you sooooo much if you can help me figure this out!!!!

---

### Post by shad0w_walker on 2007-10-21
So far i haven't found any good information about this. The only things that appear from a google search talk about this sort of problem, there is even a filled bug report about this particular problem however no work around or solutions i have encountered.

[https://bugs.launchpad.net/ubuntu/+source/ndiswrapper/+bug/93152](https://bugs.launchpad.net/ubuntu/+source/ndiswrapper/+bug/93152)  <- Bug report

If you have an alternative Wifi card around then that would be the easiest option for getting this sorted and still having Wifi available. As for getting your system booting again, do you have a LiveCD? Like the LiveCD/installer disc for Ubuntu? If you do, you can boot that up and should be able to stop ndiswrapper from loading up (Which should sort out the crash issue for now)

If you have the livecd let me know and I'l write up some instructions if you need them.

---

### Post by froggger on 2007-10-22
yes i have the livecd, and yes i need instructions.
i'll figure out wifi later, i need to boot right now!

---

### Post by froggger on 2007-10-22
ok, i was being retarted and didn't try and to boot w/out wifi plugged in.
now i can boot and am about to remove ndiswrapper.
so now i'm back to my wifi problem.
theres a thread on these forums about some guy getting dwl-g132 to work w.out ndiswrapper.
can anybody shed some light on how he would have done that?
heres the thread:
[http://ubuntuforums.org/showthread.php?t=516438&highlight=dwl-g132](http://ubuntuforums.org/showthread.php?t=516438&highlight=dwl-g132)

Thanks!!

---

