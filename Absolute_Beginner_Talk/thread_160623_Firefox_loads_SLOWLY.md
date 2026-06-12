---
title: "Firefox loads SLOWLY"
date: 2006-04-15
forum: Absolute Beginner Talk
---

### Post by SVwanders on 2006-04-15
At some point Firefox on my daul booting Ubuntu/XP system started really loading pages extremely slowly. It is hard to know just when it started. I have a laptop running XP off the same router and it loads Firefox very fast. What sort of information would be needed to figure out where the problem is and how to fix it?

Thanks, Tim

---

### Post by bscbrit on 2006-04-15
One of the easiest tools to start with would be Applications -> System Tools -> System Monitor.  Then you could see how much CPU time it was using, the speed of your downloaded pages, how much memory is being used (is there a lot of swapping going on?) and so on.  From there, it might give you a clue as to what more specialised tools will be needed to pin this down.  


But Firefox, for all its strengths, doesn't behave as well as it might on many linux systems.  Memory leakage is particularly poor under certain circumstances - although some would have you believe that this is a 'feature' rather than a bug.

---

### Post by SVwanders on 2006-04-15
Hi bscbrit,

Well, I did as you suggested and opened up the system monitor. The memory swap useage and user memory is a flat line, with swap being reported as zero and about 21% memory use. At first when I came back to this OS I thought the problem was cured but then at this site I had some slow down. At that point the send/ receive history was showing a little movement.

I switched over to Opera for awhile and at first thought your last comment might be right but again after awhile the system slowed down. It might be my provider . . . but I don't have any problems on my laptop or the other Linux machine using SuSe.

Maybe it is just idiot operator . . . I am just learning this system and have been trying to set up a network from my laptop on XP to this machine and maybe I have screwed something up. Anyway, I feel like I am learning things and am enjoying myself. Thank you so much for your help. Everyone here has been so nice to me.

---

### Post by SVwanders on 2006-04-15
update:

What watching the system monitor it did hang for about a minute. It was while I was sending the last post. No change in the memory but nothing, or very little, was being received or sent on the network history. I decided to refresh yahoo at the same time and it took about a minute to refresh . . . no change in the system.

Tim

---

### Post by Qrk on 2006-04-15
Try changing Firefox's settings by typing about:config in the address bar. Scroll down and set

network.http.pipelining 
network.http.proxy.pipelining

to "true"

and 

network.http.pipelining.maxrequests

to a larger number. I think I use 6.


But the truth is Firefox has some interesting bugs in Ubuntu that I haven't been able to find fixes for. 

I'd recommend trying Firefox 1.5, which is easy enough to install. Don't use the guides on the forum unless you want to completely replace 1.0x with 1.5. Instead download the firefox linux version from their website. Extract it to your home directory and run the firefox browser from there, its the file named "firefox." IMHO it isn't worth bothering to replace Breezy's version with the updated one, just update your laucher. 

To do this, right click on the firefox icon on your panel, select properties, change whats in the "Command" box to read ```
/home/*yourusername*/firefox/firefox
``` 

You'll need to substitute your real username here.

Lastly, look into epiphany. Its my web browser of choice and offers better Gnome integration than Firefox. To get it, just do a 

```
sudo apt-get install epiphany
```

---

### Post by jhaykage on 2006-04-16
Wow, I've learned so much from this bug and thread alone. II'm also keeping my eyes on this thread.

---

