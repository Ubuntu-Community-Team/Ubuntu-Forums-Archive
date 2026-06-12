---
title: "Help! My graphics collapsed"
date: 2008-02-05
forum: Absolute Beginner Talk
---

### Post by getmeoutofhere on 2008-02-05
I've generally found that I have to do a complete reinstall of Ubuntu every three weeks.  My computer has collapsed again, but I don't want to do a reinstall.  Anyway, all of a sudden, my screen has collapsed.  Ubuntu (7.10) seems to have decided, after three weeks of working fine, that it no longer recognises my graphics card.  So, my Inspiron 1520 now has huge, low definition letters.  I now, in preferences for screen resolution, have a choice of 800X600 or 640 X 480.  What do I do?  How do I go about solving the problem? Thanks.

Put another way - when I first installed Ubuntu it recognised my graphics, etc.  How do I start this process again?

---

### Post by Ripfox on 2008-02-05
Open a terminal and try 

> sudo dpkg-reconfigure xserver-xorg -phigh

---

### Post by overdrank on 2008-02-05
> **getmeoutofhere said:**
> I've generally found that I have to do a complete reinstall of Ubuntu every three weeks.  My computer has collapsed again, but I don't want to do a reinstall.  Anyway, all of a sudden, my screen has collapsed.  Ubuntu (7.10) seems to have decided, after three weeks of working fine, that it no longer recognises my graphics card.  So, my Inspiron 1520 now has huge, low definition letters.  I now, in preferences for screen resolution, have a choice of 800X600 or 640 X 480.  What do I do?  How do I go about solving the problem? Thanks.

HI and what is the model of the graphics card? Does it do this when you have a update? Have you tried to reconfigure your xorg ```
sudo dpkg-reconfigure -phigh xserver-xorg 
```

---

### Post by getmeoutofhere on 2008-02-05
Thanks for the replies.

I tried the sudo dpkg-reconfigure xserver-xorg,  At the time my screen was completely unreadable, now my computer is just about usable.  I was presented with a barrage of questions, which I didn't really now how to answer.

My graphics card is an nvidia GeForce Go 8400M GS.

---

### Post by Ripfox on 2008-02-05
Sorry rerun it with the -phigh  (less questions...:))

---

### Post by overdrank on 2008-02-05
> **getmeoutofhere said:**
> Thanks for the replies.

I tried the sudo dpkg-reconfigure xserver-xorg,  At the time my screen was completely unreadable, now my computer is just about usable.  I was presented with a barrage of questions, which I didn't really now how to answer.

My graphics card is an nvidia GeForce Go 8400M GS.

Ok have you tried Envy or the restricted drivers? [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

### Post by getmeoutofhere on 2008-02-05
Well, I've got some improvement, in the sense the size of letter is better.  But there's something wrong with the screen I can't quite describe.  The refresh rate is apparently 0 Hz.

---

### Post by getmeoutofhere on 2008-02-05
I used to use the restricted driver, but I no long have access to that in administration.  I'm told that I need linux restricte modules 2.6 etc... which is installed, according to the synaptic manager.

---

### Post by overdrank on 2008-02-05
> **getmeoutofhere said:**
> I used to use the restricted driver, but I no long have access to that in administration.  I'm told that I need linux restricte modules 2.6 etc... which is installed, according to the synaptic manager.

Hi you can try and remove the restricted driver from synaptic and reboot and try to reinstall. Or Envy

---

### Post by Ripfox on 2008-02-05
> **getmeoutofhere said:**
> I used to use the restricted driver, but I no long have access to that in administration.  I'm told that I need linux restricte modules 2.6 etc... which is installed, according to the synaptic manager.

Why do you think he doesn't have admin access to the restricted drivers manager?

---

### Post by getmeoutofhere on 2008-02-05
I think the restrictred driver is a bit of a red herring, through it is strange I don't have access to it.  When I first installed 7.10 the graphics worked fine without it - adding it created a marginal improvement.  So I don't think anything's changed.  BTW my graphics are big and chunky again, working at 800X600.  I'm not sure I can wait for Hardy Heron to fix this problem, though unfortunately this computer doesn't work seem to work with 7.04 - I tried both the the live cd and alternate one.

But... why I can't I ask Ubuntu to repeat the auto-detection process it used when it first installed itself?

---

### Post by Ripfox on 2008-02-05
That would be the command in the third post...should do it.

---

### Post by Ripfox on 2008-02-05
Here is someone else with that graphics card too...

[http://ubuntuforums.org/showthread.php?t=644331](http://ubuntuforums.org/showthread.php?t=644331)

---

### Post by Ripfox on 2008-02-05
And another...[http://forum.notebookreview.com/showthread.php?t=205826](http://forum.notebookreview.com/showthread.php?t=205826)

---

### Post by getmeoutofhere on 2008-02-05
ripfox,

Your command helped,thanks.

But it hasn't competely returned be back to where I was.

The refresh rate of my monitor is 0 Hz, apparently.  Very jerky, particularly if try to scroll up and down quickly.

And there is still the problem of the disappearing restricted drivers.

But thanks again.

---

### Post by steveneddy on 2008-02-05
What were you doing when all of this happened?

---

