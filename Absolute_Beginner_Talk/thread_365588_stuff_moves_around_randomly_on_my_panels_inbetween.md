---
title: "stuff moves around randomly on my panels inbetween startups"
date: 2007-02-19
forum: Absolute Beginner Talk
---

### Post by mrSlush50 on 2007-02-19
for instance, right now, my nm-applet is on the bottom panel next to the workspaces... for no reason!  I didn't move it there.  in fact absolutely everything on both of my panels is locked, yet any time i restart, I end up moving at least a couple of things around the get them the way they were before.

most of the time it's just annoying and I'd love to be able to fix it.  but the thing with the nm-applet is that I can't seem to get it back up to the top panel where I want it.  

if anyone could help with either of these issues (the moving stuff, or the nm-applet refusing to move back to the top panel) that would be great.

thanks.

(6.06 on an hp laptop)

---

### Post by mrSlush50 on 2007-02-19
fixed the nm-applet issue, still having issues with stuff moving around.

---

### Post by n8bounds on 2007-02-19
thats tough to help you with through the forums..I thot nm-applet ran inside the System Notification Panel Applet (the system tray).  Make sure you only have ONE of those running.  (i.e. you don't have one on panel A and another one on panel B, that might confuse it).  If you really get stumped you can remove everything, including extra panels and start over.

Try logging off and back on instead of restarted to test your changes...also make sure you haven't screwed up the permissions in your home folder by accidentally sudoing something you didn't mean to.  One sure fire way to put that back is a command like this from a terminal:

```
 sudo chown user:user /home/user -R 
```

replace ALL THREE of the "user"s in that example with YOUR username

G'luck

---

