---
title: "clean shutdown?"
date: 2007-07-26
forum: Absolute Beginner Talk
---

### Post by NESFreak on 2007-07-26
if i shut down my computer while, for instance, firefox, gaim and utorrent are still running, the next time i start up those apps they give me an error that they weren't closed correctly(firefox), or my logs aren't up to date (gaim), or it'll go through several tests in order to be sure my downloads are ok (utorrent). Is there a way other than closing those apps individually while still closing them the way it should when shutting down?

Is the time-out before killing an app to short in gnome or doesn't it even try to politely close them, but just kills them?

NESFreak

---

### Post by Pragmatist on 2007-07-26
> **NESFreak said:**
> ....Is there a way other than closing those apps individually while still closing them the way it should when shutting down?....

Gnome-session allows you to save the "state" of your system when shutdown.  When you reboot your machine, all the applications will be open just the way they were when you shutdown. "Hibernate" does the same thing, but only puts the machine in a suspend state, rather than a complete shutdown.  Read these:
```
man gnome-session
```
```
man gnome-session-save
```

I don't know how to trigger the system to automatically close every open user application on shutdown.  The reason the applications don't like being "killed" is that it does not give them time to close the way they want to.  There are different types of kill "signals"; some give the applications more time than others.  You might be able to change the system kill command to a milder signal.  I just have no idea how to do it, or if it is even possible.

There is an obvious advantage to having to close the applications one-by-one: You might forget to save something.

---

### Post by NESFreak on 2007-07-27
> **Pragmatist said:**
> 
There is an obvious advantage to having to close the applications one-by-one: You might forget to save something.

or you might forget to close the whole application (i often forget closing gaim, resulting in losing my logs of the last session.)

i'll try figuring out how gnome closes running applications. Would be nice if there would just be a time-out setting or something.

---

### Post by Pragmatist on 2007-07-27
Do these help at all?
[http://www.howtogeek.com/howto/ubuntu/make-ubuntu-automatically-save-changes-to-your-session/](http://www.howtogeek.com/howto/ubuntu/make-ubuntu-automatically-save-changes-to-your-session/)
[http://www.howtogeek.com/howto/internet/firefox/quick-tip-save-windows-and-tabs-when-restarting-firefox/](http://www.howtogeek.com/howto/internet/firefox/quick-tip-save-windows-and-tabs-when-restarting-firefox/)

---

### Post by NESFreak on 2007-07-27
> **Pragmatist said:**
> Do these help at all?
[http://www.howtogeek.com/howto/ubuntu/make-ubuntu-automatically-save-changes-to-your-session/](http://www.howtogeek.com/howto/ubuntu/make-ubuntu-automatically-save-changes-to-your-session/)
[http://www.howtogeek.com/howto/internet/firefox/quick-tip-save-windows-and-tabs-when-restarting-firefox/](http://www.howtogeek.com/howto/internet/firefox/quick-tip-save-windows-and-tabs-when-restarting-firefox/)

nope. tried that already. It still kills the apps and after reboot opens them again. I don't want everything to be the same after reboot. I just don't want any error for not shutting down correctly.

---

### Post by Pragmatist on 2007-07-27
I hope you find a solution.  I am interested in hearing what it is.  I believe that saving the information within a program, however, is the responsibility of that particular program, not of the OS.  You might want to see if the specific programs have some settings to accomplish what you want.

---

