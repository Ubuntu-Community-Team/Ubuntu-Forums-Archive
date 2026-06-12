---
title: "gedit problem"
date: 2007-01-28
forum: Absolute Beginner Talk
---

### Post by EKa on 2007-01-28
Does any one know cause and cure for the following what I get starting gedit:

 (gedit:15623): GLib-CRITICAL **: g_string_append: assertion `val != NULL' failed

---

### Post by theoneandonlywheeler on 2007-01-28
What are you trying to edit?

---

### Post by ecmerkle on 2007-03-13
I am having a similar problem with gedit: whenever I run it, I get the following message:

(gedit:6114): GLib-CRITICAL **: g_string_append: assertion `val != NULL' failed
sys:1: Warning: g_string_append: assertion `val != NULL' failed

I do not get this message when I sudo gedit.

This only started happening after I set up a VNC server a la this site:
[http://www.movingtofreedom.org/category/vnc/](http://www.movingtofreedom.org/category/vnc/)

Any ideas?

---

### Post by chavo on 2007-03-13
Does gedit still open?

---

### Post by dannyboy79 on 2007-03-13
always use gksudo when opening gui apps with sudo access. it's better and there is a place that explains why but don't know where the link is off the top of my head. plus, his gedit still opens and works, it's not a big deal, I somtimes get errors even using nano but if I hit enter, it still goes into nano and I can edit my text file.

---

### Post by ecmerkle on 2007-03-13
Yes, chavo, my gedit still opens.  So I suppose it's not a big deal, I was just seeing if I missed something obvious.

Thanks, danny, for the gksudo tip.  One link that has a good description of it is:

[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

### Post by CocoAUS on 2007-03-13
I really don't see how running gedit with gksudo is "better."  It has no affect on the functionality of gedit whatsoever.  This whole "it's proper to use gksudo..." thing has really got to go.

---

### Post by chavo on 2007-03-13
> **CocoAUS said:**
> I really don't see how running gedit with gksudo is "better."  It has no affect on the functionality of gedit whatsoever.  This whole "it's proper to use gksudo..." thing has really got to go.

Right and wrong. Yes you can run gedit just fine with sudo and edit files, no problem. The problem comes with the environment not being set up correctly, so you're running gedit with elevated privileges, but it still has all of the user's environment. So any settings changes in gedit itself will be made in the user's directory. The users files will then become owned by root, this will lead to all kinds of problems down the road. 

This is just one example of what can happen when using sudo with graphical apps. It won't always cause a problem, but it can. So it's easier to use gksudo all of the time and avoid any potential issues.

If you'd still like to use sudo for graphical apps, fine be my guest. Don't say you weren't warned and please don't go sprouting off remarks like the one above to new users.  Keep it to yourself. We are trying to protect them from damaging their system, that is all.

---

### Post by CocoAUS on 2007-03-13
Spouting off remarks?  Give me a break!  Using gedit with sudo does not cause problems for your system.  I and all my friends have been doing it since we started using Linux.  That doesn't mean sudo doesn't cause problems elsewhere sometimes.

By the way, keep your arrogant comments about "spouting off" to yourself.  There are new users here, and I'm sure they don't want to see the ugly side of the Ubuntu community first thing.

---

### Post by dannyboy79 on 2007-03-13
> **CocoAUS said:**
> I really don't see how running gedit with gksudo is "better."  It has no affect on the functionality of gedit whatsoever.  This whole "it's proper to use gksudo..." thing has really got to go.
you have your opinion and you can use sudo all you'd like for graphical applications but when something goes wrong and you can't login anymore, don't sit there and complain that ubuntu sucks because it's your own doing! the reasons have been explained explicitly in the link provided in a previous post. one main reason is so you won't potentially mess up their ~/.ICEauthority and other user configuration files.

also, if you can't abide by the Ubuntu Forums Code of Conduct than you will be given an infraction. Read number 10 of the code, you have clearly broken it, chavo was in the right, we don't want new users reading stuff like this which CAN cause issues.

---

