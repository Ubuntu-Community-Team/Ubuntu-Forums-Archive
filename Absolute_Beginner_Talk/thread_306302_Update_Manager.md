---
title: "Update Manager"
date: 2006-11-24
forum: Absolute Beginner Talk
---

### Post by mar2000 on 2006-11-24
I updated using the update manager.  Every now and then it says there are some new updates available.  Is there any way I can undo the last update I did?

Thanks

---

### Post by cilynx on 2006-11-24
Quick answer:  not really.

Longer answer:  Why are you looking to roll back the update?

---

### Post by mar2000 on 2006-11-24
After I updated, it said it required a restart.  I did not restart but clicked "restart later" and then I shut down the computer the way I always do.  Now, when I turn it on, sometimes the mouse is choppy and sometimes it is not.

Also, in our house we have several computers.  We have a DSL modem, a router, and a hub.  It seems that everytime I turn on the Ubuntu box, it stops all of the computers from using the internet.  There is a reset button on the router that if pressed will fix the problem.  However, if I shut down ubuntu and then start it again, the same thing will happen and the button has to be pressed again.  These things did not happen until after I updated.

So I am not 100% sure that the problem is because I updated, but I think it might be.

---

### Post by cilynx on 2006-11-24
Interesting.  Which distribution are you running?  Do you remember which packages updated?

---

### Post by mar2000 on 2006-11-24
I am running Ubuntu 6.06 LTS, Dapper.

Unfortunately I don't remember which packages updated.  I think one was dpkg and there were about 3 or 5.  So far I always just updated and it worked fine so I did not pay much attention.

If nothing else I can always just reinstall everything, but that is a pain.  I was also thinking about unplugging the ethernet cable until after I logged in and seeing if that helped any.

---

### Post by cilynx on 2006-11-24
The problem with blowing away and reinstalling is that you're going to get back the exact same system that you have now unless you decide not to keep it up to date.  Are you running any weird services or p2p clients on the Ubuntu box?

---

### Post by mar2000 on 2006-11-24
I am not running any p2p clients.  I do have apache2 and mysql start up every time because I use it to test php scripts.  There is a Win XP Box on the network that is almost always downloading stuff via bit torrent using the bitcomet client.

---

### Post by CatKiller on 2006-11-24
You could try not running apache and mysql on start up to see if you still have the same problem. Just as a troubleshooting step, since I have no idea if they could cause the behaviour you describe.

---

### Post by mar2000 on 2006-11-24
Okay, thanks, I will go to google and figure out how to do that.

---

### Post by mar2000 on 2006-11-26
I figured out what it was.  It was actually the windows xp computer on the network that was causing the problem.  For some reason it happened just after I booted Ubuntu (twice).

Thanks

---

### Post by cilynx on 2006-11-26
If I may ask, what was the XP machine doing that hosed the network?

---

### Post by mar2000 on 2006-11-30
First of all, the XP machine is not my computer, it was used by someone else.

As far as I can tell, he was trying to download too many things at once with various p2p clients.  That was the only thing that I think could have caused it.

---

