---
title: "sudu su and script"
date: 2007-11-21
forum: Absolute Beginner Talk
---

### Post by endlessurf on 2007-11-21
i was wondering if it is possible to run sudo su as a start up script or from a script file and not have to put in your password

---

### Post by poudin on 2007-11-21
not really recommended...that is why Ubuntu forces u to sudo....the root account just to powerful...warnings aside

you could sudu su - passwd and set a root password...use that to signon to the machine...

---

### Post by endlessurf on 2007-11-21
my problem is the computer is in a car and i don't want to have to type in sudo su and then a password.  I Know how to login as root and do all of that good stuff.  But i want to get sudo su with out using a keyboard and driving

---

### Post by mokkai on 2007-11-21
> **endlessurf said:**
> i was wondering if it is possible to run sudo su as a start up script or from a script file and not have to put in your password

i thing not possible:(

---

### Post by barney385 on 2007-11-21
This was discussed a week or so ago.

:popcorn:

---

### Post by websnail on 2007-11-21
try this:
> echo passwd| sudo command
use pipe [COLOR="Red"]|[/COLOR]

---

### Post by Incense on 2007-11-22
> **endlessurf said:**
> i was wondering if it is possible to run sudo su as a start up script or from a script file and not have to put in your password

If you're going to do that, you just might was well enable the root account, and log in that way. It's really not recommended to ever do that though. Is there a reason you need root access while you're driving? I don't like people who talk on their cell, or text while they drive, last thing we need is someone driving around as root.Though I guess you could ignore the stop lights, and speed limits if you were doing that... hmmm... maybe that's not so bad after all. :lolflag:

---

