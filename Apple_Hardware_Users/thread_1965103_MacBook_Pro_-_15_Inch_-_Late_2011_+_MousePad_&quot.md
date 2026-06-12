---
title: "MacBook Pro - 15 Inch - Late 2011 + MousePad &quot;Swipe&quot; functions?"
date: 2012-04-25
forum: Apple Hardware Users
---

### Post by Jynks on 2012-04-25
When i moved to PC to Mac for development reasons one of the few things I really liked about the mac was the neat mouse pad thing the laptop had were you can use multi-touch mouse swipes to do things like scroll up and down and other things.

Are there any apps that emulate this behaviour on the Ubuntu?

Thanks in advance.
--Jynks

---

### Post by Jynks on 2012-04-27
ifound somthing called touchegg but after installing i can not find the gui that it talks about on the homepage.

[http://code.google.com/p/touchegg/](http://code.google.com/p/touchegg/)

anyone know how to get the gui? or No an alternitive software?

---

### Post by s0l1dsnak3123 on 2012-04-28
> **Jynks said:**
> ifound somthing called touchegg but after installing i can not find the gui that it talks about on the homepage.

[http://code.google.com/p/touchegg/](http://code.google.com/p/touchegg/)

anyone know how to get the gui? or No an alternitive software?


I've tried this program, when running it from the terminal it segfaults in 12.04

---

### Post by bradleyjones on 2012-04-28
See my post [here]("http://ubuntuforums.org/showthread.php?t=1966032") (Copied below for easy viewing :))

> In terms of configuration for the touchpad, touchegg is definately the way to go however it is not currently working in 12.04 due to problems with uTouch, see bug report - [https://bugs.launchpad.net/utouch-geis/+bug/986886](https://bugs.launchpad.net/utouch-geis/+bug/986886)

To those people getting the segfaults with touchegg you can fix this by downloading the daily build directly from the touchegg's svn but until uTouch gets updated we are left waiting.

I wish there was a way just to configure the multitouch gestures be default as the ones provided by the synaptics driver actually work quite well I just don't really have a need for 3-finger screen movement or a four finger tap, would rather configure them to do something useful!

Also if you want to speed up maybe getting this fixed go on over to the bug report and mark it as affecting you :)

---

