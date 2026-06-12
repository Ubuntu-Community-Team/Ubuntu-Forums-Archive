---
title: "Thunderbird (and Firefox) occasionally hangs computer"
date: 2006-04-18
forum: Absolute Beginner Talk
---

### Post by mdsmedia on 2006-04-18
Hi,

I use Thunderbird for email and Firefox for browsing.

Sometimes, I'll be working away and all of a sudden the CPU light is on constantly and everything is moving very slowly, if at all, in particular the mouse. I can't open any other package. On one occasion I was able to close down all apps, and when I closed a particular Firefox window, everything went back to normal. On another occasion I managed to close down Thunderbird, then everything went back to normal.

Ctrl-Alt-Del won't work. Ctrl-Alt-Esc won't work.

This only happens occasionally.

Is there a way to bring up a task manager, or force everything to quit, rather than having to shut down the computer using the Power Switch?

I was impressed though. I had been downloading about 250MB with Synaptic, and when the computer hung Synaptic stopped. When I rebooted and went back to Synaptic it just contunued from where it left off.

---

### Post by bikeboy on 2006-04-18
Press Ctrl + Alt + F1

This will take you to a login screen, enter your details and at the command prompt type "top" without the quotes.

Look for the PID of the offending program, type "k", the PID number and "y" when it asks to kill it.

This can also be done from a normal terminal via Applications > Accessories > Terminal and using "top", but I'm assuming your desktop has become really unresponsive so this might be a better way.

---

### Post by mdsmedia on 2006-04-18
thanks for that.

Yes it generally won't let me open a menu.

I hadn't thought of "ctrl-alt-Fn" to bring up a terminal/login screen, but even if I did I probably wouldn't have known what to do once there.

---

### Post by RAV TUX on 2006-04-18
[QUOTE=mdsmedia]Hi,

I use Thunderbird for email and Firefox for browsing.

Sometimes, I'll be working away and all of a sudden the CPU light is on constantly and everything is moving very slowly, if at all, in particular the mouse. I can't open any other package. On one occasion I was able to close down all apps, and when I closed a particular Firefox window, everything went back to normal. On another occasion I managed to close down Thunderbird, then everything went back to normal.

Ctrl-Alt-Del won't work. Ctrl-Alt-Esc won't work.

This only happens occasionally.

Is there a way to bring up a task manager, or force everything to quit, rather than having to shut down the computer using the Power Switch?

I was impressed though. I had been downloading about 250MB with Synaptic, and when the computer hung Synaptic stopped. When I rebooted and went back to Synaptic it just contunued from where it left off.[/QUOTE]


:-k 

what version Firefox?

---

### Post by mdsmedia on 2006-11-13
> **RAV TUX said:**
> :-k 

what version Firefox?Sorry I hadn't replied before this, but had solved the query.

Not sure what version I was using at the time, but it would have been the one in the repos.

Since then it's happened with firefox, thunderbird and Kontact open, and I go to terminal and shut down any one or several and Linux comes back to normal again.

---

