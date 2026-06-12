---
title: "[SOLVED] Two quick questions..."
date: 2007-10-17
forum: Absolute Beginner Talk
---

### Post by frsrblch on 2007-10-17
First off, this is on whatever the latest installment of Gutsy is (2.6.22-14?).  Problems are to be expected with something like this, but these are matters of my own shortcomings, and not the result of a beta release.

**First question:**

I'm trying to make a startup script, and I've run into difficulties.  I have my .sh file made up, set to run as an executable, and have it in /etc/init.d.

```
#!/bin/sh
#
# Starts PuTTY and logs me in
putty 10.0.0.1 -P 22 -l mylogin -pw mypass
```

Here's the kicker though.  I had it working as intended! But then redid it as it originally only opened PuTTY, and I wanted automated login.  The script itself still works, but I can't seem to get it to run at startup anymore (and it seems I've tried everything).  I have to do all the clicking to make it go, and clicking is not cool (it still beats having to login by hand though :)).

**Second question**:

 I'm trying to make the nvidia-settings load before compiz starts up (so it will antialias right off the get-go).  Right now, I have to load the settings, and then manually toggle compiz off and then on again.  I think I need to know how to either make the nvidia configurations load before compiz or how to toggle compiz with gnome-appearance-properties (the Help button is buggered... which, you know, isn't helpful at all).

Alright, that may not actually have been short, but I'm more than thankful for any help you can give me.  I'm having a blast tinkering-with/learning Ubuntu, but I need a little help from time to time.

---

### Post by llamakc on 2007-10-17
Why would you use Putty?

---

### Post by llamakc on 2007-10-17
If you want to add the script (or any script) to your USER login when you start up Gnome, add it to your session.

SYSTEM |  PREFERENCES | SESSIONS | ADD

/etc/init.d/ scripts have a different use.

Are you aware you can just open a terminal and type "ssh IP.ADD.RE.SS" instead?

---

### Post by frsrblch on 2007-10-17
Thanks, and thanks!  I was using putty because I really didn't know any better before.  I had tried the Connect to Server thing from the Places menu, but to no avail.  Now that I know a bit more I could pull up info ssh and get myself going from that.

---

