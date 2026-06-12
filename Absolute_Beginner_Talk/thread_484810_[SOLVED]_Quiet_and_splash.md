---
title: "[SOLVED] Quiet and splash"
date: 2007-06-26
forum: Absolute Beginner Talk
---

### Post by forestpixie on 2007-06-26
Hi I took quiet and splash out of grub in order to find out what whas stopping restart from restarting. 

Now I've put quiet and splash back into the grub listing - it doesn't work.

Can anyone give me an idea of why it might have stopped working, I've tried a space between quiet and splash and I've tried changing it to a tab.

Thanks

---

### Post by shearn89 on 2007-06-26
what was stopping it restarting?

---

### Post by forestpixie on 2007-06-26
not really sure to be honest last line I saw before i kicked the box was

```

NetworkManager: <WARNING> nm_hal_deint () libhal shutdown failed - Connection is closed
*Will now restart
[103.370674] Restarting System
```

but that appears on a normal shutdown - it just refuses to restart if I give the restart prompt, if it's called by Update for instance everythings cool. Sort of thinking of posting a bug - eventually, 

[http://ubuntuforums.org/showthread.php?t=483718](http://ubuntuforums.org/showthread.php?t=483718)

Not a major problem - it's just not right! 
And downright annoying if you forget to do shutdown and tell it to restart then wander off for a glass of wine and come back to have to reboot anyway! :D

But what I'm trying to sort now is making it quiet again - can't understand why putting back what I removed is making no difference :confused:

---

### Post by forestpixie on 2007-06-27
bump

---

### Post by speaker219 on 2007-06-27
Try looking here and doing the opposite steps:
[https://answers.launchpad.net/ubuntu/+question/7197](https://answers.launchpad.net/ubuntu/+question/7197)
Instead of removing "quiet" and "splash" add the things it tells you to remove

---

### Post by forestpixie on 2007-06-27
thanks speaker219

---

### Post by speaker219 on 2007-06-27
> **forestpixie said:**
> thanks speaker219
Sure, let me know if you get it to work =) :popcorn:

---

### Post by forestpixie on 2007-06-27
yea done it - just needed to update grub and all is quiet again :D

---

### Post by speaker219 on 2007-06-27
glad to help

---

