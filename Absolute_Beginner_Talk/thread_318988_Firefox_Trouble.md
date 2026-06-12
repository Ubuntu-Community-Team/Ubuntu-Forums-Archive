---
title: "Firefox Trouble"
date: 2006-12-14
forum: Absolute Beginner Talk
---

### Post by Buck2348 on 2006-12-14
During the last several days my Firefox occasionally quits very abruptly.  It always happens while it is loading a page--the window just suddenly disappears.  When I click on the Firefox icon again, it shows a box which says the previous session terminated suddenly and asks whether to restore that session or begin a new one.  It can restore the session no problem, but if I try to go the the same page that gave trouble, it usually quits again.  I reinstalled but that didn't fix it.  Any help for this, please?

Thanks,
Buck

---

### Post by lwr on 2006-12-14
Does the page contain Flash? If so, what version of Flash Player are you using. I think 9b has a bug that causes Firefox to quit if your colour depth is set too low.

---

### Post by jpeddicord on 2006-12-14
Usually I find that Java is the cause of this. I always have trouble on pages with Java. The browser will either randomly close on load or freeze. Flash (even 9b) has never done this unless I do something with the Flash applet itself.

What version of Firefox are you using, and were there any plugins on the page that may have caused it?

Jacob

---

### Post by matchstich on 2006-12-14
i have had  this happen to me, on myspace,.  and firefox freezes at times. someone said it was flash 7, so i uninstalled it

---

### Post by P235 on 2006-12-14
Try using the latest Adobe release for Linux (Flash 9) with this [Ubuntu forum thread]("http://www.ubuntuforums.org/showthread.php?t=315004").

---

### Post by drphilngood on 2006-12-14
...and install the Firefox extension called NoScript.

---

### Post by Buck2348 on 2006-12-15
Thanks for the replies.  I have firefox 2.0, which I reinstalled today.  I'm afraid I don't know how to find what version, if any, of flash player I have.  My Synaptic lists only one version, the latest, it says, and shows I do not have it.  I have two different flash files in ~/.mozilla/plugins:  flashplayer.xpt, and libflashplayer.so.  That last file showed up in instructions for installing flash 9, but as I said, I don't know what I've got.  I already had noscript, but it was disabled when I was having the problem.  I'll try leaving it on for a while.  What the consensus--should I install flash 9?  

Thanks,
Buck

---

### Post by dnite on 2006-12-29
You can check your plugins by typing 'about:plugins' (without quotes, of course) in the address bar in firefox.

EDIT: hmm.. i'm seeing a smily face in the middle of that, i'm not sure how to make that not show up, so I'll just say that it's 'about : plugins' ... mash that all together. x=) no spaces.

---

### Post by raul_ on 2006-12-29
Did you try starting firefox from the terminal? when it crashes you should see the type of error...i bet my money on seg fault :mrgreen:

---

### Post by Buck2348 on 2006-12-29
I haven't seen the problem recently.  Apparently forbidding scripts prevents it.  I have Shockwave Flash 7.0.

---

### Post by Keith_Beef on 2007-01-04
After installing an upgrade this morning (1.5.dfsg+1.5.0.9-0ubuntu0.6.06 and libraries), Firefox quits with a Segmentation fault when I try to use yahoo mail.

Beef.

---

### Post by JallenDragonhide on 2007-01-08
Same over here.. so I thought I'd try a force version downgrade in Synaptic... no biggie right?

Now it's asking me to remove firefox-gnome-support and ubutnu-desktop cause of deps...  ack!

I don't think I am going to proceed... :P

---

### Post by Efwis on 2007-01-08
what if any extensions are you using?

I had the same issue, it turned out to be one of my extensions tabbrowser preferences 1.3.1.1 that was causing this to happen to me.

---

### Post by JallenDragonhide on 2007-01-08
> **Efwis said:**
> what if any extensions are you using?

I had the same issue, it turned out to be one of my extensions tabbrowser preferences 1.3.1.1 that was causing this to happen to me.

Del.icio.us 1.2
greasemonkey 0.6.6.20061017.0

I'll start with uninstalling greasemonkey and see where that takes me..

Thanks for the thought!

---

### Post by JallenDragonhide on 2007-01-08
Since I uninstalled greasemonkey, I haven't had a single crash.  If I do later on, I'll report, otherwise it looks fixed.

Thank you!

"greasemonkey firefox update segmentation fault"

(wanted to make it easier for anyone like me to search)

---

### Post by Efwis on 2007-01-08
> **JallenDragonhide said:**
> Since I uninstalled greasemonkey, I haven't had a single crash.  If I do later on, I'll report, otherwise it looks fixed.

Thank you!

"greasemonkey firefox update segmentation fault"

(wanted to make it easier for anyone like me to search)

hopefully that will take care of the problem. If you continue to run without problems then I would contact the extension creator and notify them of it so they can patch and release a new version of it.

---

### Post by Buck2348 on 2007-01-10
I recently found the fix for my trouble [here]("http://www.ubuntuforums.org/showthread.php?t=286069").  It was the Flash plugin that was triggering the crashes.

Buck

---

