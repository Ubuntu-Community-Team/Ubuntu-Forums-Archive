---
title: "Timed shutdown"
date: 2007-08-21
forum: Absolute Beginner Talk
---

### Post by Dr Small on 2007-08-21
Is there someway to have a timed shutdown, after for example, every hour of inactivity?
Like, instead of a screensaver coming up every hour of inactivity, can I set it up for my computer to shutdown 1 hour after inactivity?

Dr Small

---

### Post by gatman3 on 2007-08-21
Try using the "Power Manager" (if this is a laptop, double click on the battery icon in the taskbar).  You can configure your manager to Shutdown (or Suspend or Hibernate, if supported) after a certain amount of idle time.

If the Power Manager is not running (i.e. this is a desktop) then you may have to start it.  Not sure how to do that on a desktop, maybe someone else does?

---

### Post by gatman3 on 2007-08-21
One more suggestion:  if you don't have the battery icon on your taskbar, try installing either gnome-power-manager (from GNOME) or kde-guidance-powermanager (if you run KDE) using your package manager.

---

### Post by heimo on 2007-08-21
> **Dr Small said:**
> Is there someway to have a timed shutdown, after for example, every hour of inactivity?
Like, instead of a screensaver coming up every hour of inactivity, can I set it up for my computer to shutdown 1 hour after inactivity?

Dr Small

That would indeed be useful. I did some searching and found this discussion (it doesn't solve your question):
[http://www.nabble.com/Feature-request-t3803098.html](http://www.nabble.com/Feature-request-t3803098.html)

I think Power Manager would be logical place for this feature.

> 
Try using the "Power Manager" (if this is a laptop, double click on the battery icon in the taskbar). You can configure your manager to Shutdown (
Oh, it already has this? :-) Nice.

---

### Post by nvteighen on 2007-08-21
Very simple. Type:

```

sudo shutdown 3600

```

3600 secs = 1 hr.

---

### Post by Dr Small on 2007-08-21
I have an ACP Battery backup which the entire system runs through, incase of power failure and surges, but I looked through the power management settings, and it only has stuff to turn the display off after x amount of time, or put to sleep after x amount of time.

I don't really think this is what I want.
But, there must be something out there that does this?

Dr Small

---

### Post by heimo on 2007-08-21
> **nvteighen said:**
> Very simple. Type:

```

sudo shutdown 3600

```3600 secs = 1 hr.

Which is not what original post asked.

---

### Post by Dr Small on 2007-08-21
> **nvteighen said:**
> Very simple. Type:

```

sudo shutdown 3600

```

3600 secs = 1 hr.
That just shuts it down in 1 hour. I want it to shutdown 1 hour from the time i stop moving my mouse, to save electricity.

Dr Small

---

### Post by nvteighen on 2007-08-21
> **heimo said:**
> Which is not what original post asked.
Ups... pardon!

---

### Post by gatman3 on 2007-08-21
> **nvteighen said:**
> Very simple. Type:

```

sudo shutdown 3600

```

3600 secs = 1 hr.

Yes, but that will shut the system down after 1 hour regardless of whether it's being used.  I think the user wants it shut down only if idle for an hour.

Try the Power Manager.  It has this feature.

---

### Post by Dr Small on 2007-08-21
It doesn't have a shutdown option. Only a sleep option, which is different, if my memory doesn't fail me.

Dr Small

---

### Post by nvteighen on 2007-08-21
> **gatman3 said:**
> Yes, but that will shut the system down after 1 hour regardless of whether it's being used.  I think the user wants it shut down only if idle for an hour.

Try the Power Manager.  It has this feature.
(Yes, I know, I misread it...)

I think Power Management has the feature to standby, not to shutdown, or am I wrong (again)?

---

### Post by Dr Small on 2007-08-21
You are correct.
So, now that I know ubuntu doesn't have such an option (so as far as I have found),
i'll have to go looking elsewhere for software that does this. :/

Dr Small

---

### Post by gatman3 on 2007-08-21
Hmmm..  Weird, mine has "When the system is idle for more than (selectable) min Do:  Nothing/Suspend/Hibernate/Shutdown".  (That's the KDE power manager, though).

---

### Post by gatman3 on 2007-08-21
> **Dr Small said:**
> You are correct.
So, now that I know ubuntu doesn't have such an option (so as far as I have found),
i'll have to go looking elsewhere for software that does this. :/

Dr Small

I doubt that ubuntu doesn't have such an option.  Try searching on "power" in our package manager(synaptic or adept) and experiment with the different packages.  There are a bunch of them.

---

### Post by Dr Small on 2007-08-21
Ok. I'll try that.

---

### Post by shaunbarlow on 2008-03-21
Maybe it's a little late... but I was just trawling through syanptic for some stuff and came across x autolock.
It's description sounds like it would fit your bill.
"Program launcher for idle X sessions
Xautolock monitors input devices under the X Window System, and launches a
program of your choice if there is no activity after a user-configurable
period of time.  You can use this to automatically start up a screen locker
if you have left your computer unattended for some period of time.  The
program launched need not be a screen locker such as xlock."

---

