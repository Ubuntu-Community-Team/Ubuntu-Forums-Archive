---
title: "[SOLVED] gnome-panel won't load - Gutsy LiveCD"
date: 2007-11-29
forum: Absolute Beginner Talk
---

### Post by crjackson on 2007-11-29
I was planing on installing Gutsy onto another computer before work today and was greeted with gnome-panel failing to start.

I've rebooted and retried several times to no avail.

The machine has an MSI motherboard - AMD64 3200+ - 1GB Ram - ATI Radeon Xpress intergrated graphics.  100GB EIDE HD.

I hesitate to proceed with an install when I can't even get the genome-panel & menus running.

Any Suggestions?

---

### Post by Billy_McBong on 2007-11-29
hit alt-f2 and try running
```
gnome-panel
```

---

### Post by crjackson on 2007-11-29
> **Billy_McBong said:**
> hit alt-f2 and try running
```
gnome-panel
```


Thanks, I'll give this another shot when I get home from work.  Any idea why this would happen?

---

### Post by jasay on 2007-11-29
If gnome-panel is just not loading then the instructions above will ask it to start.  

The other option seems to be that the panel is running but somehow either hidden or locked up.  In fact, during gutsy development the panel would sometimes load behind the background so you couldn't interact with it.  I was pretty sure that was fixed though.  Anyway, if running Billy's command does not work you might try ```
killall gnome-panel
``` which will kill the current occurrence of gnome-panel and another should automatically respawn (hopefully working and above everything else).

---

### Post by crjackson on 2007-11-30
Strange thing happened.  I went home ready to try the suggestions, put the LiveCD in, booted, and all was well...

I tried this about 5 times yesterday and had the same problem each time.  Today it worked 1st time.  I guess I'll proceed with the install this weekend.

Thanks for the advice...

---

### Post by nate305 on 2008-06-26
I had same issue, the reason was that i uninstalled evolution-data-server-common (wanted to nix evolution all-together) the above post referring to using ctrl-alt-f2 and running sudo apt-get install gnome-panel worked 4 me...

---

