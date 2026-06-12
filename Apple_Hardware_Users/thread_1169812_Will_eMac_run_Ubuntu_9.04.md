---
title: "Will eMac run Ubuntu 9.04"
date: 2009-05-25
forum: Apple Hardware Users
---

### Post by jrdjrd on 2009-05-25
Hello, I have an eMac that will run Ubuntu 7.04 Feisty, Fawn but it will not run the latest version of Ubuntu, (9.04). It will boot but when it gets done, I can't see anything. I think it has something  
to do with the graphics card. Is there a way to get it to work?

Thanks

---

### Post by tiresia on 2009-05-25
Have you tried at the yaboot prompt```
Linux nosplash video=ofonly
```

---

### Post by jrdjrd on 2009-05-25
Just tried, I did not get a splash screen but the code looked lile it wasn't going to have one. Did not get anything from it though.

---

### Post by tiresia on 2009-05-25
Can you switch to a console (ctrl-alt-F1)?

---

### Post by jrdjrd on 2009-05-25
Yes, I can go to console.

---

### Post by tiresia on 2009-05-25
You should now configure your xorg.conf file to fit to your monitor and your grafic card. You can follow this how-to [http://forums.debian.net/viewtopic.php?f=16&t=20481&hilit=emac](http://forums.debian.net/viewtopic.php?f=16&t=20481&hilit=emac) (section: To setup the X Window System) or you can find a thread here on this forum.
Let us know, if you have still problems

---

### Post by jrdjrd on 2009-05-27
Ok, It booted up until It was loging in and showed an internal error: failed to initatialize HAL!.

---

### Post by jrdjrd on 2009-05-30
Nevermind, I let the computer sit in mac os x for a few hours and retried, and had a sucessful install. (was using a live cd)

Thanks to all the people that helped me figure this out.
I didn't need to reconfigure the x-server thing.

---

