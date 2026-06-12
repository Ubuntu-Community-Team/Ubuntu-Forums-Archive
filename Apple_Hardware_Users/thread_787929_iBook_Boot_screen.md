---
title: "iBook Boot screen"
date: 2008-05-09
forum: Apple Hardware Users
---

### Post by ibooklvr on 2008-05-09
Hi there, I just installed Ubuntu 7.04 on my iBook clamshell (indigo), its working good (using it right now) but whenever I boot up, the boot screen where it says "Ubuntu" and has a progress bar is all scrambled.  This didn't happen when i had 6.06 on this machine.  I changed all the resolutions in my xorg.conf to "800x600" and that hasn't solved the problem...sorry if this has been asked before but i've been googling for a while and haven't found anything.

thanks

---

### Post by stream303 on 2008-05-10
When you reach the second stage of the yaboot boot: prompt, can you temporarily stop the countdown by hitting -tab- and they using nosplash as a kernel parameter, ie
```
Linux nosplash
```

You'll lose the splash screen and see the boot messages instead..

---

### Post by ibooklvr on 2008-05-12
thanks, i guess that's what ill do

---

### Post by ibooklvr on 2008-05-13
ok, that actually doesn't work...I type "Linux nosplash" and it just shows the scrambled splash screen as normal

---

