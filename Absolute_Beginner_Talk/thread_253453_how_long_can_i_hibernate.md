---
title: "how long can i hibernate?"
date: 2006-09-08
forum: Absolute Beginner Talk
---

### Post by jaden403 on 2006-09-08
This is probably a silly question, but is there any harm in leaving my laptop in hibernate mode instead of turning it off all the time?  Will this have any negative affects on Ubuntu or my laptop?

---

### Post by xyz on 2006-09-08
Probably as long as a bear does! :-D 

What do you mean by how long? Days? A couple of hours?

---

### Post by davmac on 2006-09-08
As far as I know, when your machine is hibernated, it is technically off. The only difference is that when you boot it up, rather than doing a normal restart, it reloads the image that it saved when you hibernated. Of course I could be talking out of the wrong end, but I've not had any problems with leaving my laptop hibernated for 4-5 days.

Hope this helps,

Dave Mac

---

### Post by az on 2006-09-08
> **jaden403 said:**
> This is probably a silly question, but is there any harm in leaving my laptop in hibernate mode instead of turning it off all the time?  Will this have any negative affects on Ubuntu or my laptop?

Hibernation means writing the contents of memory to disk and then shutting off.  The next time you power up, (actually, every time you power up) the swap space will be probed to see if there is a hibernated session there and if so, it will be loaded into ram and your boot time will be reduced.

To suspend your computer, means to enter a low-power state which keeps some current goingto the ram to keep everything there for when you resume.

When you hibernate, your computer is off.  If your swap space is shared with another OS (like if you boot another linux OS on the same machine and use the same swap space as Ubuntu) and you boot your other OS while there is a hibernated session there, it will be erased and you will lose all your data from that session.  Otherwise, you can keep it off for years - it is completely off.

When you suspend, that is a different story.

Resuming from hibernation takes a lot longer than resuming from suspend, since your computer was never really off, just in a low-power state.

---

### Post by jaden403 on 2006-09-08
Thanks a lot for your responses!  This answers my question...

---

