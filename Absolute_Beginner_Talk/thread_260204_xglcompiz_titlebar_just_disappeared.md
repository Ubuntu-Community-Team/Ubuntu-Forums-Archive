---
title: "xgl/compiz titlebar just disappeared"
date: 2006-09-18
forum: Absolute Beginner Talk
---

### Post by Rizla on 2006-09-18
Hey guys, I dont know if anyone else had experienced this problem and whether they know of a solution to it.  I've got xgl/compiz installed and everythings working great.  I have the aero theme installed (looks cool).  During my regular workings the titlebar just disappeared.  I dont have minimize/maximize/close icons anymore.  I tryed switching themes to see if it would force a new one, but i cant tell if its working since the title bar is completely gone. 

Has anyone heard of this happening before?  If so, whats the cause and what is a workaround?

---

### Post by Rizla on 2006-09-18
Quick update: I went into the console and restared compiz and it worked.  I have my title bar back.

console->compiz-start

Wish I knew what caused the problem in the first place though..

---

### Post by bulldog on 2006-09-18
Did you had an update?

The problem is known by me,mostly after a bad update.

Had no update today and all's working.

Try to logout and in again and see if it changes anything.

---

### Post by Rizla on 2006-09-18
> **bulldog said:**
> Did you had an update?

The problem is known by me,mostly after a bad update.

Had no update today and all's working.

Try to logout and in again and see if it changes anything.

WHen i checked my update manager it had a bunch of stuff that had newer version, of which compiz was on the list.  So i had updated that.  Maybe that was the culprit.  I'll logout after i finished downloading some stuff.

Thanks, at least its not just me.

---

### Post by Rizla on 2006-09-18
Another pesky problem. This one is REAALY bad.  COmpiz locks up my system whenever i press Shift+f9 to start the rain.  WOnder why.

---

### Post by bulldog on 2006-09-18
You use csm as configuration utility?

And /usr/bin/compiz-start  in your sessions menu to start compiz?

You use cgwd as window themer?

So much questions :biggrin:

---

### Post by Rizla on 2006-09-18
> **bulldog said:**
> You use csm as configuration utility?

And /usr/bin/compiz-start  in your sessions menu to start compiz?

Yes, i do both.  as far as compiz start,  Im assuming thats the path, but i just type compiz-start from the command line without specifying the full path.

---

### Post by bulldog on 2006-09-18
You shouldn't.

Make it /usr/bin/compiz-start because there where a lot of changes lately.

So you are certain it uses the right starter and not an old one.

gsetcompiz ,gcompiz-themer are outdated and some older starters refer to this programs.

There is a new file in /usr/bin which refer to csm

---

### Post by Psquared on 2006-10-09
Same problem here. I rebooted and the titlebar came back. It was there this morning when I got up, but during the day it left. We'll see if it does that tomorrow. Might be a bug.

Using Beryl 0.1 with xgl. Everything else works fine.

---

