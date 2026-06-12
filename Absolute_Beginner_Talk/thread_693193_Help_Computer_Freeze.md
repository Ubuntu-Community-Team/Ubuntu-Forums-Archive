---
title: "Help: Computer Freeze"
date: 2008-02-10
forum: Absolute Beginner Talk
---

### Post by pdavis1987 on 2008-02-10
I just installed Feisty Fawn and every time I try to install the software updates or video and audio codecs my laptop freezes.

---

### Post by pdavis1987 on 2008-02-10
bump

---

### Post by ed-koala on 2008-02-10
Can you post the specs of your equipment here?  That will help in troubleshooting your problem.

---

### Post by pdavis1987 on 2008-02-10
Dell Inspiron 6000
Intel Pentium M  1.73 GHz
1 Gig RAM
ATi Mobility Radeon X300

---

### Post by pdavis1987 on 2008-02-10
Bump

---

### Post by rkd on 2008-02-11
I've been doing a bit of searching to see whether I could find any threads with solutions to your freeze problem, and I found quite a lot of reports of freezes but no definite solutions.

One thing that is pretty easy to try is make sure you have the latest updates. My suggestion is that you go to System -> Administration -> Software Sources. In the Ubuntu Software tab, make sure "main", "universe", "restricted", and "multiverse" are checked and that the CD-ROM box down below is unchecked. Then on the Updates tab, make sure that "feisty-security", "feisty-updates", and "feisty-backports" are checked. Then close Software Sources and open a Terminal. in the Terminal, enter```
sudo apt-get update
sudo apt-get upgrade
```

If you upgraded to Feisty rather than doing a fresh install, problems sometimes seem to be caused by that. If doing the above steps to make sure your software is up to date doesn't fix the problem, the next thing to try is back up any files you need to keep, then do a clean install of Feisty from the Live CD, then repeat the above steps to be sure everything is completely up to date.

If that doesn't make the problem go away, I don't know what you could do except give up on Feisty and go to Ubuntu 6.10. That is an older version, but it is the long-term-supported version, so it is still under maintenance. You could try Ubuntu 7.10 rather than going to the older one, but I have a feeling 6.10 is more likely to fix the problem.  There's no guarantee it will, but it is a better bet.  

There are lots of other things you could try, but it seems to be rather hit or miss whether they will fix the problem. Something that cures the problem for one person doesn't work for others who try it. I get the impression that there are lots of causes for the freezes. Therefore, although they look alike to the casual bystander, they really are different, so what cures one person's problem naturally won't help someone else if the underlying cause is different.

Sorry to be kind of pessimistic, but unless you really want to try many things until you find one that works for you, or run out of things to try, it doesn't look hopeful.

Should you want to look at them, the Google search I did is this:

[http://www.google.com/search?hl=en&q=Dell+Inspiron+6000+%28feisty+OR+7.04%29+freeze](http://www.google.com/search?hl=en&q=Dell+Inspiron+6000+%28feisty+OR+7.04%29+freeze)

and the thread I spent the most time looking at is:

[http://sudan.ubuntuforums.com/showthread.php?t=412125](http://sudan.ubuntuforums.com/showthread.php?t=412125)

---

