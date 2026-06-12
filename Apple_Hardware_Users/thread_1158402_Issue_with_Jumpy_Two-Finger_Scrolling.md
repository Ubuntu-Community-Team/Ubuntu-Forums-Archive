---
title: "Issue with Jumpy Two-Finger Scrolling"
date: 2009-05-13
forum: Apple Hardware Users
---

### Post by penguininja on 2009-05-13
Hi all,

I am running Ubuntu 9.04 Jaunty on a Macbook 2,1.  I am currently using the Synaptics + Appletouch drivers as described in the following article: [https://help.ubuntu.com/community/MacBook2-1/Jaunty#Touchpad%20(appletouch](https://help.ubuntu.com/community/MacBook2-1/Jaunty#Touchpad%20(appletouch)) (using the appletouch.fdi file). 

In general, all touchpad functionality is working (two-finger click to right click, two-finger vertical scroll, etc.).  However, the two-finger vertical scrolling is very jumpy.  Specifically, when one finger is on the touchpad and I place the second finger on, it scrolls a short distance.  This makes it jumpy when I first start scrolling unless I put both fingers down at exactly the same time (i.e. if I am scrolling down and my top finger hits the touchpad a little later than the bottom one it scrolls up a little first).  It also makes two-finger clicks more difficult.  To compare, in OS X nothing happens when the second finger is put down and scrolling does not occur until either or both of the two fingers are dragged on the touchpad.

I have tried adjusting the VertScrollDelta value with apparently no effect.  I also have all "tap-to-click" events disabled.  Sorry this was kind of hard to explain!  In general I've been very pleased with the Synaptic and Appletouch drivers, a huge improvement over previous versions.  Is anyone else experiencing (or not experiencing) this behaviour?  Any insights would be greatly appreciated!  

Thanks!

---

### Post by tiagobt on 2009-05-13
Yes, I've also noticed the behavior you described. The vertical scrolling is sometimes activated when I try to right click (two-finger tap). In my experience, this issue becomes less noticeable by following the instructions on [http://ubuntuforums.org/showthread.php?t=981474](http://ubuntuforums.org/showthread.php?t=981474) (which are also explained on the Wiki page). However, I still get an unwanted scrolling when I place the second finger a little bit after the first one, like you explained.

Any ideas?

---

### Post by tiagobt on 2009-05-14
You could also try to use edge scrolling instead of two-finger scrolling:
```
<merge key="input.x11_options.VertEdgeScroll" type="string">true</merge>
<merge key="input.x11_options.HorizEdgeScroll" type="string">false</merge>
<merge key="input.x11_options.VertTwoFingerScroll" type="string">false</merge>
<merge key="input.x11_options.HorizTwoFingerScroll" type="string">false</merge>
```

---

### Post by penguininja on 2009-05-14
Thanks tiagobt, I may try edge scrolling instead.  I'd prefer two-finger scroll if I can resolve this issue with it, though :)  

The code at the link you posted does improve the touchpad functionality greatly for me as well (as well as the code on the Jaunty/Macbook wiki page, which is very similar), but as you noted does not completely resolve the unintended scrolling issue.

---

### Post by cygnl7 on 2009-05-25
I have this same problem.  It makes two-finger operations mostly unusable.  Right-clicking ends up in the wrong place most of the time.  I'm looking all over for an answer to this.

The interesting thing is that the FingerHigh option doesn't seem to affect this.  For example, if I set it to something high (like 50) it affects the first finger press (for moving the mouse) but the second finger press still works with a light touch.

This makes me think that there might be another option (or set of options) that can be used to tweak this behavior.

---

### Post by hanzomon4 on 2009-05-27
Does anyone have some fdi magic they could run... I guess I bug should be filed or feature request?

---

### Post by tiagobt on 2009-05-28
Filing a bug is probably a good idea. Quite a few people have reported this behavior now.

---

### Post by Richardcavell on 2009-05-29
I've looked all through the manuals of the synaptics driver.  There's no way of removing this problem as it's currently maintained.  Fiddling with the .fdi file isn't going to change anything.

It's really going to take some programming to fix this.  The source code is available.  When Apple fixed their trackpad, they made us install a trackpad driver update.  The Apple driver was jumpy to begin with.

Richard

---

### Post by hanzomon4 on 2009-05-29
I suck at filling these things so if anyone knows what kind of information the report will need let me know

---

### Post by Richardcavell on 2009-05-30
Guys,

I'm surprised to see that there has never been a bug report filed on this issue.  So I did one myself:

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/381884](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/381884)

Richard

---

### Post by hanzomon4 on 2009-05-30
Thank you

---

### Post by tiagobt on 2009-06-01
There's one more issue I have with appletouch: [the cursor moves "in steps"](http://ubuntuforums.org/showthread.php?t=813884). Do you think these issues are related? Should we file a new bug? Has anyone else experienced this problem?

---

### Post by Richardcavell on 2009-06-09
Others are mentioning this as well in different threads.  I don't think the issues are related.

Richard

---

