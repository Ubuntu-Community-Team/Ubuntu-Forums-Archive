---
title: "Screen resolution problem"
date: 2007-05-06
forum: Absolute Beginner Talk
---

### Post by Typie on 2007-05-06
Can anyone help me? Whenever I reboot my computer, my screen resolution changes to 800x600 and I can't change it back. I'm using Ubuntu Feisty, have tried disabling restricted drivers, restarting X, restarting the system and no luck :(

---

### Post by Happy_Man on 2007-05-06
Right, open up a terminal (applications --> Accessories --> Terminal) and enter:

```
dpkg-reconfigure xserver-xorg
```

And answer the questions. Remember to use the spacebar to select stuff (this is especially important when you get to the screen resolution selection part!) After you finish, restart X and hopefully everything will be alright!

---

### Post by Dugg on 2007-05-06
I am having the exact same problem.  Someone mentioned changing it from the systems menu, however that just made it worse for me.  Now I'm stuck in 640 resolution, with most of my windows (including the NVIDIA control panel) off the screen.

---

### Post by freebird54 on 2007-05-06
Here is a walkthrough of the dpkg-reconfigure - might help you to know what you're doing in there (although answering the defaults is not a bad strategy for most of it).  Here's the link:  [http://users.bigpond.net.au/hermanzone/p7.html](http://users.bigpond.net.au/hermanzone/p7.html)

Also - make sure you use medium or advanced for the monitor setup....and let it know the 'best' setting.. (your choice of best that is)

---

### Post by Typie on 2007-05-06
Thanks guys, I kinda forgot about this topic xD

I solved it on IRC.

Thanks anyway for your time!

---

### Post by jayemcee on 2007-05-07
Thank you, Folks,
Just solved my screen resolution problem by following the above.
What a boon this forum is to absolute beginners! :) 
JMC

---

