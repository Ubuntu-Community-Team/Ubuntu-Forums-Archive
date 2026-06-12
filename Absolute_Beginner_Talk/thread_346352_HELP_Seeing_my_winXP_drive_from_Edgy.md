---
title: "HELP: Seeing my winXP drive from Edgy"
date: 2007-01-25
forum: Absolute Beginner Talk
---

### Post by user007 on 2007-01-25
Hello. 

I just want to be able to access a drive on my laptop over the wired LAN network from my Ubuntu 6.10 installation.

Setup:

DESKTOP:

Ubuntu 6.10


LAPTOP:
WinXP 2005 Media Edition
All Firewalls OFF (for debugging)
Drive has been shared properly on windows end.
WORKGROUP: MSHOME


LAPTOP <---->  ROUTER  <----->DESKTOP

Router is configured right.  The machines can ping one another.
 

When I access the share from Konqueror I see:

smb:/ Shows "Mshome" (note the case.  Does this matter?)

I then click to get: smb://mshome/ with the error message "Timeout on server mshome"

How do I fix this.  It seems to me it should be simple.  I am not needing to share files on my ubuntu computer.  I just wish to access the laptop.

Please help.  I am moderately computer literate but reading all the past threads through search leave me confused.  I see people talking about WINS and enabling this, and I do not think I should have to.  I don't want to mess anything up by doing unneccesary things.

Thank you!

---

### Post by Happy_Man on 2007-01-25
I believe that the workgroup names have to agree exactly. Try changing that to "MSHOME" and see whether it works.

---

### Post by meng on 2007-01-25
Try
smb://(IP address)

---

### Post by user007 on 2007-01-25
> **meng said:**
> Try
smb://(IP address)

Yes!  Thank you!  Thank you!  It works!

Now I can at least work.

Is there something I should fix so it works better though?  I presume it should have worked before, right?

---

### Post by user007 on 2007-01-25
> **Happy_Man said:**
> I believe that the workgroup names have to agree exactly. Try changing that to "MSHOME" and see whether it works.

I changed it to smb://MSHOME/ but it changed it automatically to lower case and did the same thing.

---

### Post by meng on 2007-01-25
MSHOME is usually the name of the workgroup, not the server itself.

---

