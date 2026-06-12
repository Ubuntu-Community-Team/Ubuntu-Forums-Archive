---
title: "gusty freeze during start up"
date: 2007-11-30
forum: Absolute Beginner Talk
---

### Post by rhanex on 2007-11-30
right after i press Enter on login screen, it freeze for about 20sec. And also before the login screen i can read text (white text with da  black background) saying "bug found # gusty failed" (it fails to do something..) " 
pls help.

tanx in advance:):)

---

### Post by jpblock82 on 2007-11-30
mine has the BUG statment as well???

---

### Post by wormser on 2007-11-30
Can you post the whole error message.  We will be able to help you better.  If I press enter right when the Grub boot screen appears it boots for a few seconds and crashes with a message about a bug.  I do not know if this is the same error you are getting, but if it is, the solution is to wait a second before pressing enter.

---

### Post by rhanex on 2007-12-01
> **wormser said:**
> Can you post the whole error message.  We will be able to help you better.  If I press enter right when the Grub boot screen appears it boots for a few seconds and crashes with a message about a bug.  I do not know if this is the same error you are getting, but if it is, the solution is to wait a second before pressing enter.


I only press enter after typing my user and password (login screen), is that what r u saying?
here's the error message

Starting up ...
[     23.464266] PCI: BIOS #81[49435000]
[     23.580982] PCI: Failed to allocate mem resource #6:20000#d0000000 for 0000:01:00.00
Loading please wait...
_

this happens after the Grub boot screen countdown done

---

### Post by wormser on 2007-12-02
It looks like this is a [bug]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/54294").

---

### Post by rhanex on 2007-12-02
thank a lot wormer, I was searching about this bug for about 6 hours with  no luck,suddenly just replyed  this post of mine. that is a good stuff though

---

