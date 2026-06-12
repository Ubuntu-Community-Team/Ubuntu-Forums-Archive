---
title: "Left on overnight, slow"
date: 2008-04-14
forum: Absolute Beginner Talk
---

### Post by dmub82 on 2008-04-14
Gutsy -- Left on overnight, when I woke up this morning everything is slow to respond -- the mouse is jerky, menus and buttons take ~15s to respond to clicks, windows take a long time to draw. 

Only apps running when I left it on were Deluge, with one torrent that completed long before I woke; Amarok, sitting idle; and Firefox with two tabs open, no Java or anything. So I shut all those down, system is still slow; System Monitor shows nothing eating CPU or memory, most processes are asleep. 

I tried to shutdown and restart but the shutdown orange progress bar hung near the very end for about 5 minutes so I eventually just did a hard restart (I know that's not a good idea). Everything is fine now. 

I don't think the system tried to hibernate or anything, my power management settings say never put system to sleep. So what happened, how do I prevent it, and how do I correctly fix it next time? I just installed Gutsy the other day so this was the first time I'd left it on overnight.

---

### Post by Moop on 2008-04-14
I'd guess that it was Deluge. I've had trouble with it slowing everything down and stopped using it. Transmission works good for me. You could check your logs and see what was going on when you tried to shutdown.

---

### Post by lbotha on 2008-04-16
Yea..probably a memory leak

---

### Post by dmub82 on 2008-04-16
Thanks. If it was Deluge, I'll probably stick with it anyway cause I liked it a lot more than Transmission, more of the features closer to uTorrent which I was used to. I'll just keep an eye on it.

---

