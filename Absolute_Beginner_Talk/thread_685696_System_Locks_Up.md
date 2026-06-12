---
title: "System Locks Up"
date: 2008-02-02
forum: Absolute Beginner Talk
---

### Post by The Minder on 2008-02-02
Greetings all,

I've recently converted one of my computer fully over to Ubuntu 7.10 and I gota say I'm pretty impressed.   I was driving the monitor from the on-board graphics output but yesterday decided to install a higher end video card, an nVidia GS7200GS based unit.   I also loaded a desktop theme that I found particularly attractive.   Searching through various forums I found the 'correct' way of installing the nVidia drivers, and all seemed to be going well.   Then the problems started.   For no reason that I can determine, my system now locks up... keyboard frozen, nada, the only thing left is the big red switch (as we used to say back in the 70s)

The lockup doesn't happen during any particular application and I'm not into high end games.   CPU and memory loads are well within normal parameters.   I'm not expecting readers to solve my problem based on the meagre information I've provided, but there is two questions I'd like to ask as I thought one of the benefits of Linux was an absence of M$ style freezes.

1.   Notwithstanding the keyboard being apparently locked, is there a key combination that will allow me to recover the system without loosing data.
2.   Would there be a log file somewhere that may give me some clues as to what's happening.

Regards to all

---

### Post by The Minder on 2008-02-02
Ok, an update.   Three more lockups and it seems that it's only happening when I'm running Firefox with multiple tabs... hope that helps.

Regards

---

### Post by jan quark on 2008-02-02
log files can be found here

system > administration > system log

---

### Post by jan quark on 2008-02-02
hey this does not help, but I have encountered the same firefox lock ups today and switched to the webbrowser kazehakase

it is light and easy to use and no crashes

---

### Post by The Minder on 2008-02-02
Update 2

Thanks Jan... I looked at the log files and most of it was gobblydgook to me.   As a fall-back, I went to system>preferences>appearance, selected the Visual Effects tab and reset it from 'normal' to 'none'.   The change didn't seem to greatly effect my 'computer experience' (as the ad men would say) and the lockups seemed to have stopped.

Thanks for the advice.

Regards

---

### Post by cubeist on 2008-02-02
Hey, Is this what you are experiencing?

[http://forum.compiz-fusion.org/showthread.php?t=4048&highlight=freezes+nvidia](http://forum.compiz-fusion.org/showthread.php?t=4048&highlight=freezes+nvidia)

It is fairly common with nvidia and compiz ... worse when switching tabs in firefox.


If you want to use compiz you could try the latest nvidia driver (169.09) and disable the appearance options in compiz... This mostly fixed the freezes for me.

---

### Post by The Minder on 2008-02-02
cubeist, thanx for the response.

I don't think the post you mentioned applies to my scenario.   I'm not using compiz (at least I don't think I am) and in my case even the mouse froze.   The nvidia install prog I used (from some Italian chap) included the 169.09 driver, which I used.
I haven't had a lock for an hour now so I think the appearance setting change I made solved the prob... fingers crossed.

Regards

---

### Post by cubeist on 2008-02-02
I think if you are using any setting other than "None" in the appearance settings then the system is using compiz.  If you leave it on none, I am sure you won't have lock-ups... but post-back if you do!

---

