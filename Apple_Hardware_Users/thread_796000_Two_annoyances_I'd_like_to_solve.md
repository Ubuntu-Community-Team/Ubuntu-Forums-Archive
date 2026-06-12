---
title: "Two annoyances I'd like to solve"
date: 2008-05-16
forum: Apple Hardware Users
---

### Post by jamescoy on 2008-05-16
Generally my Ubuntu installation (via Parallels) is working okay, but there are two annoyances I'd like to clear up.

First, upon booting, I always get the "Unable to load system description file." In spite of getting this error message, the VM always continues booting without a problem. I'm just wondering why this is happening and how I can get rid of it.

Secondly, upon shutting down, Ubuntu displays the shutdown progress bar, but never completely shuts down. I end up having to shut down the Ubuntu virtual machine manually.

I'd be grateful for any suggestions.

---

### Post by cyberdork33 on 2008-05-16
is that a parallels error message, or a message in Ubuntu?

---

### Post by jamescoy on 2008-05-16
It appears to be an Ubuntu error message

---

### Post by russo.mic on 2008-05-17
If you've got an ATI Graphics card with the restricted driver installed, that could be the cause of it not shutting down.  I found this in a post last night, and the fix worked.

 You must edit the file /etc/ati/authatieventsd.sh.
 
 The suggestion is to update the change by changing
 
 XDM_AUTH_MASK=/var/lib/xdm/authdir/authfiles/A$1*
 
 to:
 
 XDM_AUTH_MASK=/var/run/xauth/A$1*


edit:  wait, never mind, your running in parallels, should have read better.

---

### Post by neorou on 2008-05-17
Upgrading to the most recent build of Parallels 3.0 may fix your first problem:
[http://kb.parallels.com/en/5257](http://kb.parallels.com/en/5257)

I would also install the most recent parallels tools if you are still running Edgy or anything before Hardy. I think Parallels doesn't formally support 8.04 yet.

I also have the same as your second problem.

---

### Post by jamescoy on 2008-05-17
> **neorou said:**
> Upgrading to the most recent build of Parallels 3.0 may fix your first problem:
[http://kb.parallels.com/en/5257](http://kb.parallels.com/en/5257)

I would also install the most recent parallels tools if you are still running Edgy or anything before Hardy. I think Parallels doesn't formally support 8.04 yet.

I also have the same as your second problem.

Actually I do have the newest version which is 5600. There's a known problem with Parallels Tools, though, so that may be the actual problem here. I was hoping someone might know of another solution.

Thanks anyway.

---

