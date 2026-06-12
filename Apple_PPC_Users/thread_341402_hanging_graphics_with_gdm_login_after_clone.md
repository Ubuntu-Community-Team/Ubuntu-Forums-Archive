---
title: "hanging graphics with gdm login after clone"
date: 2007-01-18
forum: Apple PPC Users
---

### Post by naitram on 2007-01-18
I'm working at cloning a large number of iMacs, and i've run into a problem.

It only happens on some systems, but when the system gets to the login screen it takes about 30 seconds to properly draw the screen.  Once the login/password are entered it appears to login correctly, but the screen lags horribly.  I see little bits of the menu bar, and about 5-10 minutes later the entire desktop is visible.  This continues for as long as i try to run in that login window.

The interesting thing is if i drop to a terminal and do 'startx -- :1' it works perfectly fine.  Brings up the correct desktop and everything, runs at normal speed, no complaints whatsoever.

I'm just stumped as to why this is happening.  I've cloned about 10 systems (all identical models) and it happens to some, but not others.  At this point about 2 in 10 of the clones functions properly.

Any thoughts/suggestions would be greatly appreciated.

---

### Post by didg on 2007-01-18
Dri ?

---

### Post by ssam on 2007-01-19
maybe the clock batteries have run out on some of them. that causes problems.

---

### Post by naitram on 2007-01-22
actually _most_ of the batteries are dead.  I've got them on NTP, which helps, but i know some of the files have some _really_ wrong timestamps (Hello 1974!).   The incorrect timestamps however are identical on the working as well as the unworking systems including the original that the clone was taken from.  If this is really likely to be _the_ culprit, i can recreate the original system.

I know that DRI exists...but beyond that not much.  Should i be enabling/disabling/updating? I'll try all of that in the meantime...


For some more interesting developments.

If i disable GDM at boot, and call the window session through startx, it still behaves incorrectly.  

Next I tried a clean boot, running startx -- :1 (which is laggy) and then ran gdm (which i assumed defaults to :0)  gdm functions to log me in and that session again works fine

So it appears that whatever second (and third, i tried with :2) session i start up runs fine, but the first session to be initiated misbehaves.  The only thing i've managed to find on this is an error message that pops up reading (i copied this by hand, it may not be 100% correct)

> (EE) R128(0): R128CCEWaitForIdle : (DEBUG) CCE idle took i = 1025
(EE) R128(0): Idle Timed out, resetting engine...

Googling shall commence.

---

### Post by didg on 2007-01-23
In /etc/X11/xorg.conf try to remove the line Load "dri"

In your test the second X has dri disabled because it's locked by the first.

---

### Post by ssam on 2007-01-23
dates before 1970 upset linux (it stores time in seconds since 1970/01/01 00:00 GMT).

if you do CRTL+ALT+F1, log in and type
```
date
```
you can see what the clock is set to.

---

### Post by naitram on 2007-01-23
didg:  did that and i'm going to tentatively say the problem is fixed. 3 of 3 that were previously broken are now working.  Thanks for the input, i'd been stumped on that one for a while.

ssam: and when the mac batteries go dead it goes back to something absurd like 1904.  I think i'll go back and redo the original image to make sure everything's at least remotely similar to the current date.  Thanks as well :)

---

