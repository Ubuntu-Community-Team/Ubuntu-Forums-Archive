---
title: "[SOLVED] Update Manager question about dpkg"
date: 2008-03-31
forum: Absolute Beginner Talk
---

### Post by clintonsears on 2008-03-31
Hi!  I just installed Ubuntu 7.10 not even 40 minutes ago and have already done something stupid!  I just hope it's easily remedied.  While the update manager was running for the first time, I pressed ^f2 and it interrupted the process.  Maybe a dumb thing, but I was skimming around another post and was curious to see what would happen.  This is what happened:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

How do I do these things?  I have no idea, but I'll keep looking around the forums and hope some more proficient users have good news for me.  In case it's not painfully obvious, I just switched from Windows this evening...Thanks,  Clinton

---

### Post by kellemes on 2008-03-31
Just open a terminal and start typing..
```
sudo dpkg --configure -a
```

---

### Post by clintonsears on 2008-03-31
Ok...I've found the terminal under applications the applications menu.  I'm not sure what it's doing...I'm just waiting.  Thanks for your help!

---

### Post by clintonsears on 2008-03-31
Actually, that didn't work...the error message still comes up.  Is there any more specific instructions anyone can give about dpkg?  A previous thread that was useful (I've searced, but so far haven't found/don't understand what I'm reading).  Cheers!

---

### Post by philinux on 2008-03-31
Copy and paste the command into the terminal. It will ask for your password. If it fails again copy and paste the errors back here. That way we can help.

Also highlight the output and put code tags round it to make it easier to read. Thats the # button above in the message pane.

---

### Post by clintonsears on 2008-03-31
Thanks Philinux, but actually, it's working!  I was being impatient and have a steep learning curve to contend with (it seems).  Anyway, it's certainly interesting and I appreciate your help!  I'll try to post error messages in the future using the wrap codes around text function.

---

### Post by philinux on 2008-03-31
Ok good, things like that do take a while to run through.

Click on Thread Tools and select - Mark Thread Solved. :)

---

