---
title: "[SOLVED] how do I refer to my current computer in ssh - Double post"
date: 2008-01-27
forum: Absolute Beginner Talk
---

### Post by JPotter on 2008-01-27
I have openssh-server installed, and I was able to use it to connect to my desktop remotely.  Now, my problem is finding a way to move files from my current computer to and from the server. What command can  I use to do this?

Side note: I have a pretty complicated password . . . should I worry about the safety of my files?

---

### Post by JPotter on 2008-01-27
I have openssh-server installed, and I was able to use it to connect to my desktop remotely.  Now, my problem is finding a way to move files from my current computer to and from the server. What command can  I use to do this?

Side note: I have a pretty complicated password . . . should I worry about the safety of my files?

---

### Post by Lord Illidan on 2008-01-27
I moved the thread here from Tutorials and Tips, as Tutorials and Tips is meant for posting Tutorials and Tips, not asking for them ;)

---

### Post by bodhi.zazen on 2008-01-27
scp

---

### Post by bodhi.zazen on 2008-01-27
Moved from jail - >  ABT ;)

---

### Post by mortsahl on 2008-01-27
Take a look at scp

 scp copies files between hosts on a network.  It uses ssh(1) for data
     transfer, and uses the same authentication and provides the same security
     as ssh(1).  Unlike rcp(1), scp will ask for passwords or passphrases if
     they are needed for authentication.

---

