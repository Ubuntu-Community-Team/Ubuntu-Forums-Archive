---
title: "Disable touchpad while typing, but not for too long!"
date: 2008-09-13
forum: Apple Hardware Users
---

### Post by stealth17 on 2008-09-13
I am trying to come up with a solution to disable the touchpad while typing, but I don't like any of the current solutions. 

According to the Macbook Wiki there are two current solutions:

> To disable the touchpad while your typing read: [http://ubuntuforums.org/showthread.php?t=271052](http://ubuntuforums.org/showthread.php?t=271052) this guide uses the command 
syndaemon -i 1 -d which disables the touchpad for 1 second after you type something. This works well but if you go back and forth a lot it can be a hassle to wait that one second. 
This guide [http://ubuntu.wordpress.com/2006/09/20/disable-touchpad-temporarily-when-typing/](http://ubuntu.wordpress.com/2006/09/20/disable-touchpad-temporarily-when-typing/) uses the command: 
syndaemon -t -d which disables tapping motions but not movement while typing.

Both of these do exactly what they claim, but both solutions suck IMHO. I tried the first one but I don't like the one second wait time. The second solution sucks as well because when I am trying to highlight something with the mouse the touchpad is disabled.

Is there a third solution? What do they do in OSx that, because it is nearly impossible to type in Ubuntu while I can type fine in OSx. I can't stand the mouse jumping around, it is very frustrating. Is there a way to simply lower the sensitivity of the touchpad while typing?

---

### Post by kosumi68 on 2008-09-13
I presume you are talking about accidental taps from the touchpad. The solution I personally have come to prefer is to disable tapping altogether. If you really want tapping, careful tuning of the synaptics parameters for palm detection is a viable alternative.

---

### Post by stealth17 on 2008-09-13
> **kosumi68 said:**
> I presume you are talking about accidental taps from the touchpad. The solution I personally have come to prefer is to disable tapping altogether. If you really want tapping, **careful tuning of the synaptics parameters for palm detection is a viable alternative**.

That is what I am looking for exactly. Where do I even start?

---

### Post by flaggh on 2008-09-13
I think if you change the sensitivity thresholds in your xorg file, you won't have a problem.  The higher the number, the less sensitive.
```

     Option          "FingerLow"             "15"
     Option          "FingerHigh"            "25"

```

---

### Post by cyberdork33 on 2008-09-15
man synaptics

---

### Post by stealth17 on 2008-09-16
How about this, is there a way to disable the touchpad while I have my USB mouse plugged in?

---

### Post by cyberdork33 on 2008-09-16
> **stealth17 said:**
> How about this, is there a way to disable the touchpad while I have my USB mouse plugged in?

There is probably an easier way to do this, but there is a solution here:
[http://linuxtidbits.wordpress.com/2007/10/27/switch-automatically-mouse-and-touchpad/](http://linuxtidbits.wordpress.com/2007/10/27/switch-automatically-mouse-and-touchpad/)

---

### Post by Cerin on 2009-11-13
I'm also having a lot of problems with accidentally triggering my trackpad while typing. It's driving me crazy. Googling found me [http://discussions.apple.com/thread.jspa?threadID=2170944&tstart=30](http://discussions.apple.com/thread.jspa?threadID=2170944&tstart=30)

It claims there's an Apple utility that let's you mark "Ignore accidental clicks". I wonder how they do that, and more importantly, why would anyone *not* want to ignore accidental clicks?

---

### Post by Cerin on 2009-11-13
I just dawned on me to check the Mouse Preferences dialog in Ubuntu 9.10. Under the Touchpad tab, there's actually a "Disable touchpad while typing" option. Unfortunately, it's checked and I'm still having this problem. There also doesn't appear to be any way to adjust the sensitivity. I wonder if there's a way to adjust the timeout it uses to disable the touchpad?

---

### Post by llamabr on 2009-11-13
This doesn't seem to be a mac specific issue, so you might get better advice on a more general forum.

---

### Post by crocowhile on 2009-11-13
> **Cerin said:**
> I just dawned on me to check the Mouse Preferences dialog in Ubuntu 9.10. Under the Touchpad tab, there's actually a "Disable touchpad while typing" option. Unfortunately, it's checked and I'm still having this problem. There also doesn't appear to be any way to adjust the sensitivity. I wonder if there's a way to adjust the timeout it uses to disable the touchpad?

this works very well: 

syndaemon -i 0.5 -d 

Alternatively you can play with palmdetection settings in the fdi file controlling synaptics.

---

