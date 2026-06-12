---
title: "internal error:failed to initialise hal"
date: 2007-05-10
forum: Absolute Beginner Talk
---

### Post by keef247 on 2007-05-10
right restart lots and nothing it still comes up.i tried a solution post here...
[http://ubuntuforums.org/showthread.php?t=289654](http://ubuntuforums.org/showthread.php?t=289654)
which has now screwed it up so that im "not allowed" to access my own services:| THANKS for that then!
so what do i do to fix it?seeing as the link above probably cause more damage.
and what will happen if "hal" isn't running?

---

### Post by ikonia on 2007-05-10
Restart the hal service using the init scripts as that thread advises. Then check to see if hal and dbus are running using the "ps" command.

And once again - please stop posting duplicate threads on you've posted one about your DVD drive which isn't working due to HAL and try to keep the one thread full of information and on track.

---

### Post by keef247 on 2007-05-10
can you state the exact commands because following that thread it was no help and made it worse now i can't even get into admin-services it says im not allowed even after authorizing it!

---

### Post by ikonia on 2007-05-10
the exact commands you need are listed in the thread you posted. 

Remember to start a systems services you'll need to do that using sudo.

Once you have hal running again you just need to enable it at startup, as the guide you posted suggests.

---

### Post by keef247 on 2007-05-10
whats the command to start services using sudo as i've followed that thread and its not helping:S
i've seen others with this problem

---

### Post by ikonia on 2007-05-10
a direct quote from the thread.

> 
sudo /etc/init.d/dbus start


When you followed the guide in the mentioned threads, did you have any errors, warnings ?

---

### Post by keef247 on 2007-05-10
cheers mate works now.

---

