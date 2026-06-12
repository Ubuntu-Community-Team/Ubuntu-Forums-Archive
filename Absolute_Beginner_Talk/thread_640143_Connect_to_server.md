---
title: "Connect to server?"
date: 2007-12-13
forum: Absolute Beginner Talk
---

### Post by OlyPerson on 2007-12-13
Hi.  I do work at school in a web development class and save my work on a school provided server.  On XP I could use WinSCP to log onto my account there and do stuff.  On Ubuntu I have no idea how to do this.
I have tried the Connect to Server thing under Places but either that can't connect or I just don't get it.
So how would I go about connecting to it?

EDIT: I can go to Places-Connect to Server... and connect to it under a FTP (with login) and it shows up as mounted on my desktop, but then it says: 
"Opening "hulk.osd.wednet.edu".
You can stop this operation by clicking cancel.

---

### Post by ctyc on 2007-12-13
If you can use WinScp then in Ubuntu just use gFTP to do the same secure copy of the files.

scp is the protocol WinScp is simple a client that handles scp.

---

### Post by defrex on 2007-12-13
Nautilus should be able to handle it too. Try putting [ftp://hulk.osd.wednet.edu](ftp://hulk.osd.wednet.edu) (or whatever the right domain name is) into nautilus' location bar.

---

