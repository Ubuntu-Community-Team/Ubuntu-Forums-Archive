---
title: "I broke network-manager!"
date: 2006-11-19
forum: Absolute Beginner Talk
---

### Post by stevieb on 2006-11-19
hello,

running edgy on my lenovo 3000 c100 with a b-com 4319.  thought i would try kde- big mistake.  when i use gnome now, nm-applet shows everything disconnected (even though i am, in fact, online wirelessly).  putting the mouse over the icon brings up 'no network connection', clicking on it brings up one faded-out option 'wired network', and right-clicking on it brings up 'enable networking' (available and checked), 'connection information' (faded-out), and 'about' (available).  there's not even an option to remove it from the panel!

i've tried completely removing and reinstalling the software, both in synaptic and terminal.  the result is always the same: nm-applet tells me i'm not connected when i am.

any ideas? thanks!
-steve

ps i have completely removed kde- didn't like it as much as gnome

---

### Post by kilps on 2006-11-19
Ok well after reading [http://www.ubuntuforums.org/showthread.php?t=287036](http://www.ubuntuforums.org/showthread.php?t=287036) perhaps you could try the following:

- open /etc/network/interfaces and comment out (with a #) everything except for:
```
auto lo
iface lo inet loopback
```
- or try going to network settings under System > Administrator and disable all your network connections ... this should let nm manage the connections

Otherwise I have no idea ... hope this helps

---

### Post by stevieb on 2006-11-19
*I was writing the following while kilps posted; seems I stumbled on the right thing.  thanks anyway kilps; nice to have confirmation!*

it's fixed now- and i have no idea what i've done.  just rebooted several times.  weird...

there is one thing i did; may have had some effect:  went to administration>networking and deselected everything.

sorry i can't give a complete solution that someone else could use, but that seems to be how i fix things- try several different solutions at once, then when something works, i have no idea what it was.

-steve

---

### Post by kilps on 2006-11-19
Glad you got it working anyway :D - nm has helped me out big time with switching to Ubuntu ... I really think that it is something which should be part of the default install ... but anyway ;)

---

