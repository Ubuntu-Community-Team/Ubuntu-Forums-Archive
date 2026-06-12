---
title: "X crashed twice in the last half hour"
date: 2007-11-14
forum: Absolute Beginner Talk
---

### Post by TheOrangePeanut on 2007-11-14
Twice it has booted me back to terminal, and then started right back up.  I had to relogin and all of my programs had closed.  I don't know what could have happened.  Even worse, just when I was typing this, X (I would assume) froze my computer.  Dead freeze; couldn't kill X (alt-ctrl-backspace), mouse wasn't working, keyboard wasn't working, etc.  I had to kill the power.

I did update this morning; I really hope that doesn't have something to do with it.  It's never did this before.  I've had Ubuntu installed for about 3 weeks now.  Are there any logs somewhere or is there something I could do to diagnose the problem?  I have to start on a CS project shortly and I can't have X crash and take my programs with it :)

---

### Post by schorsch on 2007-11-14
Did you have "Visual Effects" enabled when X crashed? I experienced some strange behaviour when watching some videos while running compiz-fusion. So if you are doing project work you should disable the visual effects. What is the type of your graphic card?

---

### Post by Inxsible on 2007-11-14
Almost all log files are located in the /var/logs directory.

you can view some of the common logs like so 
```
# tail -f /var/log/messages
# less /var/log/messages
# more -f /var/log/messages
```

---

### Post by TheOrangePeanut on 2007-11-14
Sorry, I guess I should have been more detailed in my earlier post.  I'm running a Radeon 9500 Pro using the 8.37 drivers from the repos.  I don't use any visual effects (fglrx doesn't support them.)

---

### Post by erginemr on 2007-11-14
Hello,

It is really hard to tell. The problem may be software specific, but you should not rule out the possibility of a hardware failure either.

If X would not start, I would say it is related to your config files, esp. /etc/X11/xorg.conf, but if you are 100% sure that you did not play with its settings except regular updates, and X crashes all of a sudden after using your computer for some time, I would suspect that there might be some hardware failure, rather than a software originated problem.

You can do several things, first go over the System Logs under Main Menu -> System -> Administration to catch any error message. 

Second, to boot your computer into the memtest mode, which is available as an option under the Grub startup menu. This way you can make sure that your memory chips are working good. 

Finally, you could open the computer box and see if the fan of the graphics card is working or not. Because, if your desktop freezes after some time, odds are that your graphics card may be overheated due to a failure in the fan.

---

