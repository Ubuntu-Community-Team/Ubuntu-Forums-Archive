---
title: "Why cant I run firefox on more than one desktop?"
date: 2007-05-31
forum: Absolute Beginner Talk
---

### Post by kevdog on 2007-05-31
Ive installed KDE and Gnome on top of my ubuntu 7.04 installation.  Is possible to run both desktops at once.  Why cant I have firefox running on more than one desktop???  Ive even noticed this problem with freenx.  If the server is running firefox, the client can not start firefox (and vice versa).

---

### Post by Mazza558 on 2007-05-31
So you're running both KDE AND Gnome at the same time?

---

### Post by kevdog on 2007-05-31
Hmm, I dont want to confuse anyone.  I have 2 (or more) virtual desktops or sessions (maybe this is the appropriate word)-- they can be anything -- 2 kde, 2 gnome, kde and gnome, gnome and kde, kde and xcfe, etc.

Point is that firefox can only run on one of the running sessions and not the other at the same time.  If the first session closes firefox, then the 2nd session can open and run firefox.  But firefox can not be running on both sessions at the same time.

---

### Post by GabrielDunn on 2007-05-31
Are you using vmware or the other virtual machine ap?  I've had firefox open on 3 desktops at once.  Each virtual machine is ignorant of the others so there should never be a conflict.

---

### Post by kevdog on 2007-05-31
Not using VMware.  In KDE for example, if you hit the Kmenu->Switch User->Start New Session, a new session will fire up.  You can then choose to log in with any type of desktop you want.  Use Cntr-Alt-F7,F9 to switch between the two desktops or sessions.

Same goes however if using freenx (which basically starts another session in the background).  If server using firefox, the freenx user can not use firefox.  Shouldn't there be separation somewhere?

---

### Post by hrsvan on 2007-05-31
Sorry for asking... but why? :)
You can have multiple desktops en both kde and gnome at switch between them using CTRL+F#  where # is the DesktopNumber...

---

### Post by dbott67 on 2007-05-31
I've got Firefox running on 3 desktops, plus an NX client running 2 more Firefox instances.  Note the screenshot below and the Firefox logo running in each of the desktops (lower right corner) of both the NX client and the host OS.

-Dave

---

### Post by kevdog on 2007-05-31
Im not really concerned about running firefox between two different sessions on the server, its really an issue however between freenx or vnc with the server.

I keep getting the popup box on the second client that states
Firefox is already running but not responding. To open a new window, you must first close the existing firefox process, or restart your system.

One thing I thought of .. I logging in as the same user with these sessions.  Could that be a problem??

---

### Post by kevdog on 2007-05-31
dbott 67

I noticed with your desktop and you nx session - you were logged in as two different users.  What happens when you log in as the same user??

---

### Post by dbott67 on 2007-05-31
> **kevdog said:**
> dbott 67

I noticed with your desktop and you nx session - you were logged in as two different users.  What happens when you log in as the same user??

I get a message:
```
Firefox is already running, but is not responding. 
To open a new window, you must first close the existing Firefox process, 
or restart your system.  

OK
```-Dave

---

### Post by dbott67 on 2007-05-31
> **kevdog said:**
> ...One thing I thought of .. I logging in as the same user with these sessions.  Could that be a problem??

I think this may be the problem.

-Dave

---

### Post by kevdog on 2007-05-31
Not to give you a rough time but can you confirm this??

---

### Post by dbott67 on 2007-05-31
I did... Post #10 :)

-Dave

---

### Post by kevdog on 2007-05-31
Sorry about that -- kinda missed the last post on the first page ;)

---

