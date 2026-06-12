---
title: "[SOLVED] Active Desktop?"
date: 2008-04-05
forum: Absolute Beginner Talk
---

### Post by I_R_LEENUCKS_MAN on 2008-04-05
Hi, I was wondering if it's possible to get an active desktop in Gutsy.

I wanted to get the Ubuntu countdown timer and a status light from my router onto my desktop, but I need to know how to do this.

Please help!

---

### Post by msgyrd on 2008-04-05
The most apparent solution to me would be to install Screenlets [http://www.screenlets.org/index.php/Home](http://www.screenlets.org/index.php/Home)

and then use the code 
```
<script type="text/javascript" src="http://www.ubuntu.com/files/countdown/display.js"></script>
```to create a page containing the countdown timer, then install a screenlet that can view web pages, like this one: [http://conceptualcaves.com/widgets/webframe](http://conceptualcaves.com/widgets/webframe)

Screenlets also has several network monitoring widgets you can try out.

If you use Compiz with the advanced features, you can enable the widget layer and use Compiz+Screenlets to create an OSX-like Dashboard.

---

### Post by I_R_LEENUCKS_MAN on 2008-04-05
Well, on my router, when I navigate to 192.168.0.1 (WLAN connection) there's an OK, DEGRADED, or SYSTEM FAILURE light on the 'web' page there. How should I get that?

---

### Post by msgyrd on 2008-04-05
I think you could use the same Webframe screenlet for that also, just open two frames, one for the ubuntu countdown, and one for your router page (I'm not sure how well that'll work if you have to login to your router though, I've never used Webframe).

---

### Post by joshrobinson on 2008-04-05
> **msgyrd said:**
> I think you could use the same Webframe screenlet for that also, just open two frames, one for the ubuntu countdown, and one for your router page (I'm not sure how well that'll work if you have to login to your router though, I've never used Webframe).

your avatar is giving me the stinkeye:(

---

### Post by I_R_LEENUCKS_MAN on 2008-04-05
Second webframe seems to open up blank, and I can't make it browse...

---

### Post by msgyrd on 2008-04-05
> **I_R_LEENUCKS_MAN said:**
> Second webframe seems to open up blank, and I can't make it browse...

You have to right click on it and go to Properties to configure it.  Like I said before though, if you have to log into your router, webframe may not handle it (it doesn't with my router that needs login credentials first).  I just installed it, and it's not too configurable with size dimensions either, so it may be kinda ugly to keep on your desktop all the time.

---

### Post by I_R_LEENUCKS_MAN on 2008-04-05
Even when I configure it, it just shows up as the default blank screen.

And it is rather obscene.

---

### Post by msgyrd on 2008-04-05
Nevermind, I see what you mean by the second one being blank.  Sorry, I'm out of easy suggestions for that one. :confused:

---

### Post by I_R_LEENUCKS_MAN on 2008-04-05
Dah...

Oh well, thanks anyways. I'll give you a thank.

---

### Post by msgyrd on 2008-04-05
> **I_R_LEENUCKS_MAN said:**
> Dah...

Oh well, thanks anyways. I'll give you a thank.


If you're willing to get your hands a little dirty, you could probably "install" web frame twice by changing the name in the code and the folder names and such and get it that way.  It looks like you can change the dimensions of the frame that way also.  Best of luck to you.

---

### Post by I_R_LEENUCKS_MAN on 2008-04-05
Well, not being very experienced in Linux, I might just try to find another app.

---

