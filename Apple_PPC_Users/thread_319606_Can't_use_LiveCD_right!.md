---
title: "Can't use LiveCD right!"
date: 2006-12-15
forum: Apple PPC Users
---

### Post by saxofoner on 2006-12-15
I keep trying different boot options from the liveCD (official distribution) of Ubuntu for Apples, and I have done so fine, in the past.  But now I get TONS of errors, at the heart of which is a Nautilus problem.


Error
-There was a problem starting the GNOME Settings Daemon
-Some things such as themes, sounds or background settings may not work correctly.
-The Settings Daemon restarted too many times
-The last error message was:
-System exception: IDL: omg.org/CORBRA/COMM_FAILURE:1.0
-GNOME will still try to start the Settings Daemon next time you log in.

It gets up to the nautilus load, then it gives all the errors.  What to do?

---

### Post by jachin on 2007-02-07
Hi I just got a few old iBooks [that had long been dead] to install Ubuntu on.
Here are the bumps in the road:
First I had to get the ppc version of the install
Then I clecked next a whole bunch of times to install
At boot up it would not display gnome correctly!
Tried setup again this time I only selected 600X800
Then I get the 
"System exception: IDL: omg.org/CORBRA/COMM_FAILURE:1.0" error
I read it is a hardware clock error that must be reset.
I tried everything I could to get the stupid thing to change... 
This is what worked on two seperate systems with the same problem:

So I shut down the system (off)
hold down the reset button (5 secs)
wait 5 secs
hold down ctrl=option=shift then power (moment)
wait 5 secs
boot up the system 
hit ctrl=option=f1
login the console
type sudo date --set "02/07/2007"
hit ctrl=option=f7
login to gnome. Yea it works!

---

