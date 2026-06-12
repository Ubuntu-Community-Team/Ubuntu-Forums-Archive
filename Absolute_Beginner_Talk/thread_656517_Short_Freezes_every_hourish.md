---
title: "Short Freezes every hourish"
date: 2008-01-02
forum: Absolute Beginner Talk
---

### Post by Vaelrith on 2008-01-02
I'm running a fresh install of Gutsy with all updates, graphics card driver installed through Restricted Drivers Manager. About every 30 minutes to an hour, my computer will freeze up and nothing will work except I can move the mouse.  If I type anything or click anything, that action will take place when everything unfreezes.  The freeze usually lasts only a few seconds, maybe 3-5 seconds.

I've searched all over and I can't find any solutions to this problem.

I've tried disabling desktop effects, and it still happens.  I thought it might be firefox, but it happens when running Epiphany too, so I'm out of ideas.

I have 1gb of ram, which should be plenty to handle gutsy...

---

### Post by Delvien on 2008-01-02
> **Vaelrith said:**
> I'm running a fresh install of Gutsy with all updates, graphics card driver installed through Restricted Drivers Manager. About every 30 minutes to an hour, my computer will freeze up and nothing will work except I can move the mouse.  If I type anything or click anything, that action will take place when everything unfreezes.  The freeze usually lasts only a few seconds, maybe 3-5 seconds.

I've searched all over and I can't find any solutions to this problem.

I've tried disabling desktop effects, and it still happens.  I thought it might be firefox, but it happens when running Epiphany too, so I'm out of ideas.

I have 1gb of ram, which should be plenty to handle gutsy...

Epiphany is very very very similar to firefox, If I'm not mistaken they are taken from the same code vice versa or w/e :P

I don't think it would be your browser, This same thing happens to me when running multiple virtual machines and trying to do memory intensive tasks. I would need more information as to what you are doing when this happens.

---

### Post by Vaelrith on 2008-01-02
It usually happens while browsing the internet, which is why I thought of firefox.  While scrolling is when I most notice it.  I'm usually listening to music at the same time, using Rhythmbox.  I usually have xchat running as well.  Also Pidgen, but all of that is not very memory intensive.

---

### Post by eolson on 2008-01-02
applicatins accessory terminal
resize it to get it small and stick it in an unused part of your screen
enter   top
when it freezes again check the terminal window and see whats hogging your resources.

---

### Post by Vaelrith on 2008-01-02
Did it, and luckily I didn't have to wait long for a freeze.  I was watching the terminal windows while browsing through firefox, and the command "Xorg" shot up to 73 %CPU, then went back down to 1 as soon as the freeze was over.

EDIT:  And it just happened again, about 5 minutes after the earlier freeze, and it was Xorg again at 61 %CPU.

---

### Post by Vaelrith on 2008-01-03
Bump: If it's on the 10th page nobody is probably going to see it...

So what do I do about Xorg?

---

