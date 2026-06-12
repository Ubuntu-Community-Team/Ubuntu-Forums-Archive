---
title: "It wont even get to the desktop"
date: 2008-03-28
forum: Absolute Beginner Talk
---

### Post by PollitowuzHere on 2008-03-28
Ok, after using the Live CD yesterday, today the Live CD won't reach the desktop/GNOME environment. Its running on a HP dv6000 laptop with AMD Turion 1.9GHz and 1GB of RAM, video card is a nvidia 6125go. Any help on how to reach the desktop?

---

### Post by Inxsible on 2008-03-28
what is it telling you?
any errors ?

---

### Post by PollitowuzHere on 2008-03-28
It doesn't show any error text, it happens after the Ubuntu loading bar and the list of all the hardware (?) drivers and such. It just switches to an empty black screen.

---

### Post by Inxsible on 2008-03-28
not even the prompt ?

---

### Post by waspbr on 2008-03-28
since you are in the beginners forum i am gonna assume you are using gutsy.

I reckon u should at least be able to get to the menu screen, I have an HP tx1320us, so this might work.

when  u get to the menu screen, press F6, you should see a command line, add the following term:

```
noacpi
``` 

see if that works, if it does open yourself a nice cold beer to celebrate, if that still doesn't work, get yourself a beer and drown your sorrows, then come talk to us

---

### Post by PollitowuzHere on 2008-03-28
Yes, the problem occurs after the prompt, both safe-graphics or normal install lead to the same place, which is my dreaded black screen.

---

### Post by PollitowuzHere on 2008-03-28
added the command line, still get to the black screen.

---

### Post by PollitowuzHere on 2008-03-28
On the hardware text (?), one line appears after "loading GNOME Display Manager", the line being "Starting Deferred execution scheduler"...Any help with that?

---

### Post by waspbr on 2008-03-28
hmmm,  I googled for your computer series and I found this link about it

[http://aldeby.org/blog/?page_id=87]("http://aldeby.org/blog/?page_id=87")

according to it gutsy should work...

there was also a thread about this: [http://ubuntuforums.org/showthread.php?t=597638]("http://ubuntuforums.org/showthread.php?t=597638")

If you are still stuck it may help to message some of those people from that thread.

All in all, gutsy is not the most HP laptop friendly distribution, the new version 8.04 (hardy heron) is a lot more friendly. So you might want to consider giving the hardy beta live CD a shot.

---

